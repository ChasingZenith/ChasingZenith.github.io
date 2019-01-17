---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page

---
# SUMO environment(Ubuntu)

## Renference

1. [教程](https://zhuanlan.zhihu.com/p/35707739)
2. [获取osm](https://www.openstreetmap.org/export#map=18/31.20601/121.59720)
3. [sumo 生成地图osm](http://sumo.dlr.de/wiki/Networks/Import/OpenStreetMap)
4. [源码安装sumo](https://www.linuxidc.com/Linux/2014-03/97771.htm)
5. [csdn源码安装sumo](https://blog.csdn.net/lucyxiaomeng/article/details/79608454)
6. [official源码安装sumo](http://www.sumo.dlr.de/wiki/Installing/Linux_Build_Libraries)
7. [Method1： official apt 安装josm 使用自带的源将显示No valid JVM found to run JOSM. Method2： 也可以直接下载josm-test.jar 然后java -jar josm-test.jar 运行](https://josm.openstreetmap.de/wiki/Download#Ubuntu)

## 注意点

1. 可能需要源码安装，使用apt安装的话，需要复制data文件夹到${SUMO_HOME}文件夹下
2. randomTrips.py -e endingtime -l weight edge probability by length
