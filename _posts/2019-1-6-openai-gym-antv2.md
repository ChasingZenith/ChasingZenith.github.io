---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
language: zh-cn

---

研究一下OpenAI的GYM环境中是怎么设置 **reward** 的。

```python
    def step(self, a):
```

```python
        # 这一步应该是获取当前状态
        xposbefore = self.get_body_com("torso")[0]
        # 按照给定的action进行一步仿真
        self.do_simulation(a, self.frame_skip)
        # 得到了仿真后的状态
        xposafter = self.get_body_com("torso")[0]
        # reward 分为四个部分
        # 分别为
        #   1. forward_reward 速度 （行动后的xpos - 行动前的xpos）除以dt
        forward_reward = (xposafter - xposbefore)/self.dt
```

2. -ctrl_cost 控制消耗 $-\sum a_i^2$

```python
        # -ctrl_cost 控制消耗 $-\sum a_i^2$
        ctrl_cost = .5 * np.square(a).sum()
        contact_cost = 0.5 * 1e-3 * np.sum(
            np.square(np.clip(self.sim.data.cfrc_ext, -1, 1)))
        survive_reward = 1.0
        reward = forward_reward - ctrl_cost - contact_cost + survive_reward
        state = self.state_vector()
        notdone = np.isfinite(state).all() \
            and state[2] >= 0.2 and state[2] <= 1.0
        done = not notdone
        ob = self._get_obs()
        return ob, reward, done, dict(
            reward_forward=forward_reward,
            reward_ctrl=-ctrl_cost,
            reward_contact=-contact_cost,
            reward_survive=survive_reward)


```

通过下面这两个网站找到了cfrc的解释

[Meaning of the observation list #282](https://github.com/openai/mujoco-py/issues/282)

[MuJoCo API Reference <-- where I find what cfrc_ext mean](http://www.mujoco.org/book/APIreference.html)

> mjData
>
> ```c
>
> struct _mjdata
> {
>
>     // ...
>
>     // computed by mj_sensorAcc/mj_rnePostConstraint if needed; rotation:translation format
>
>     mjtNum*   cacc;                 // com-based acceleration                   (nbody x 6)
>
>     mjtNum*   cfrc_int;             // com-based interaction force with parent  (nbody x 6)
> 
>     mjtNum*   cfrc_ext;             // com-based external force on body         (nbody x 6)
>
>     // ...
> }
>
> ```

为了明白什么是com-based，我又查找了这里

> mj_jacBodyCom
>
> ```c
>
> void mj_jacBodyCom(const mjModel* m, const mjData* d,
                   mjtNum* jacp, mjtNum* jacr, int body);
>
> ```
>
> Compute body center-of-mass end-effector Jacobian. 

[MuJoCo Programming <--- Where I find what com-based mean](Coordinate frames and transformations)

> ### Coordinate frames and transformations
> 
> Finally, there is the **com-based** frame. This is used to represent 6D spatial vectors containing a 3D angular velocity or acceleration or torque, followed by a 3D linear velocity or acceleration or force. Note the backwards order: rotation followed by translation. mjData.cdof and mjData.cacc are example of such vectors; the names start with "c". These vectors play a key role in the multi-joint dynamics computation. Explaining this is beyond our scope here; see Featherstone's excellent [slides](http://royfeatherstone.org/spatial/) on the subject. In general, the user should avoid working with such quantities directly. Instead use the functions mj_objectVelocity, mj_objectAcceleration and the low-level mju_transformSpatial to obtain linear and angular velocities, accelerations and forces for a given body. Still, for the interested reader, we summarize the most unusual aspect of the "c" quantities. Suppose we want to represent a body spinning in place. One might expect a spatial velocity that has non-zero angular velocity and zero linear velocity. However this is not the case. The rotation is interpreted as taking place around an axis through the center of the coordinate frame, which is outside the body (we use the center of mass of the kinematic tree). Such a rotation will not only rotate the body but also translate it. Therefore the spatial vector must have non-zero linear velocity to compensate for the side-effect of rotation around an off-body axis. If you call mj_objectVelocity, the resulting 6D quantity will be represented in a frame that is centered at the body and aligned with the world. Thus the linear component will now be zero as expected. This function will also put translation in front of rotation, which is our convention for local and global coordinates. 
> 
> > translation 平移


根据猜测frc是force的缩写，c是CoM-based的意思。
CoM是 **center-of-mass** 重心的意思。