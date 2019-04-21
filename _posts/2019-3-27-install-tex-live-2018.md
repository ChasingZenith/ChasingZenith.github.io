

install texlive2018

Loading https://mirrors-lan.geekpie.club/CTAN/systems/texlive/tlnet/tlpkg/texlive.tlpdb
Installing TeX Live 2018 from: https://mirrors-lan.geekpie.club/CTAN/systems/texlive/tlnet (verified)
Platform: x86_64-linux => 'GNU/Linux on x86_64'
Distribution: net  (downloading)
Using URL: https://mirrors-lan.geekpie.club/CTAN/systems/texlive/tlnet
Directory for temporary files: /tmp/_OkPqSS8dV

======================> TeX Live installation procedure <=====================

======>   Letters/digits in <angle brackets> indicate   <=======
======>   menu items for actions or customizations      <=======

 Detected platform: GNU/Linux on x86_64
 
 <B> set binary platforms: 1 out of 17

 <S> set installation scheme: scheme-full

 <C> set installation collections:
     40 collections out of 41, disk space required: 5806 MB

 <D> set directories:
   TEXDIR (the main TeX directory):
     !! default location: /usr/local/texlive/2018
     !! is not writable or not allowed, please select a different one!
   TEXMFLOCAL (directory for site-wide local files):
     /usr/local/texlive/texmf-local
   TEXMFSYSVAR (directory for variable and automatically generated data):
     /usr/local/texlive/2018/texmf-var
   TEXMFSYSCONFIG (directory for local config):
     /usr/local/texlive/2018/texmf-config
   TEXMFVAR (personal directory for variable and automatically generated data):
     ~/.texlive2018/texmf-var
   TEXMFCONFIG (personal directory for local config):
     ~/.texlive2018/texmf-config
   TEXMFHOME (directory for user-specific files):
     ~/texmf

 <O> options:
   [ ] use letter size instead of A4 by default
   [X] allow execution of restricted list of programs via \write18
   [X] create all format files
   [X] install macro/font doc tree
   [X] install macro/font source tree
   [ ] create symlinks to standard directories

 <V> set up for portable installation

Actions:
 <I> start installation to hard disk
 <P> save installation profile to 'texlive.profile' and exit
 <H> help
 <Q> quit

Enter command: p
Installation profile saved to 'texlive.profile', exiting.

 ----------------------------------------------------------------------
 The following environment variables contain the string "tex"
 (case-independent).  If you're doing anything but adding personal
 directories to the system paths, they may well cause trouble somewhere
 while running TeX.  If you encounter problems, try unsetting them.
 Please ignore spurious matches unrelated to TeX.

    SUDO_COMMAND=./install-tl --portable --location https://mirrors-lan.geekpie.club/CTAN/systems/texlive/tlnet/
 ----------------------------------------------------------------------


Welcome to TeX Live!

See /usr/local/texlive/index.html for links to documentation.
The TeX Live web site (https://tug.org/texlive/) contains any updates and
corrections. TeX Live is a joint project of the TeX user groups around the
world; please consider supporting it by joining the group best for you. The
list of groups is available on the web at https://tug.org/usergroups.html.


Add /usr/local/texlive/texmf-dist/doc/man to MANPATH.
Add /usr/local/texlive/texmf-dist/doc/info to INFOPATH.
Most importantly, add /usr/local/texlive/bin/x86_64-linux
to your PATH for current and future sessions.
Logfile: /usr/local/texlive/install-tl.log


# find ctex

>            If the option "--list" is given with a package, the list of
>            contained files is also shown, including those for
>            platform-specific dependencies. When given with schemes and
>            collections, "--list" outputs their dependencies in a similar
>            way.

tlmgr info --list ctex

# fandol ubuntu

编译过程中提示如下警告,不影响.

* fontspec warning: "script-not-exist"
*
* Font 'FandolFang-Regular' does not contain script 'CJK'.
* 
http://www.cnblogs.com/ccoming/p/7810861.html

## to use latexmk with xelatex

add -xelatex
remove -pdf

## sysu

https://gitlab.com/sysu-gitlab/latex-group/thesis/blob/master/Makefile

## font not found

https://blog.csdn.net/up_com/article/details/51099928


