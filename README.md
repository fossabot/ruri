[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FMoe-hacker%2Fruri.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2FMoe-hacker%2Fruri?ref=badge_shield)


![](https://github.com/Moe-hacker/ruri/raw/main/logo/logo.png)

![](https://img.shields.io/github/stars/Moe-hacker/ruri?style=for-the-badge&color=fee4d0&logo=starship&logoColor=fee4d0)
![](https://img.shields.io/github/forks/Moe-hacker/ruri?style=for-the-badge&color=fee4d0&logo=git&logoColor=fee4d0)
![](https://img.shields.io/github/license/Moe-hacker/ruri?style=for-the-badge&color=fee4d0&logo=cloudera&logoColor=fee4d0)
![](https://img.shields.io/github/repo-size/Moe-hacker/ruri?style=for-the-badge&color=fee4d0&logo=files&logoColor=fee4d0)
![](https://img.shields.io/github/last-commit/Moe-hacker/ruri?style=for-the-badge&color=fee4d0&logo=codeigniter&logoColor=fee4d0)
![](https://img.shields.io/badge/language-c-green?style=for-the-badge&color=fee4d0&logo=C&logoColor=fee4d0)

<p align="center">「 须臾水面明月出，沧江万顷瑠璃寒 」</p>

-----------------     
### WARNING:      
```
* Your warranty is void.
* I am not responsible for anything that may happen to your device by using this program.
* You do it at your own risk and take the responsibility upon yourself.
* This program has no Super Cow Powers.
```
### About ruri:         
&emsp;ruri is pronounced as  `luli`, or you can call it `瑠璃` in Chinese or Japanese as well.       
&emsp;ruri is the romaji acronym of Lightweight, User-friendly Linux-container Implementation. It's designed to provide better security for Linux containers on devices that do not support docker.       
- Simple:      
Although it has many args in the help page, the basic usage is very very simple, you can use it just like the command chroot.
- Secure:      
It uses libcap and libseccomp for security, and most devices in /dev will never be reached in containers.
- Static:      
Compile ruri with `make static`, it will be compiled as a small binary file(less than 1M), but it can be run everywhere without dependent libraries.      

&emsp;The default capability set is based on docker container, which can be elevated with the `-p` option, reduced by `-d`, or you can use `--keep` and `--drop` to set by yourself.      
### Install:      
```
git clone https://github.com/Moe-hacker/ruri
cd ruri
sudo make install
```
### Quick start(with rootfstool):
#### First, download and unpack a rootfs:
```
git clone https://github.com/Moe-hacker/rootfstool
cd rootfstool
./rootfstool download -d alpine -v edge
mkdir /tmp/alpine
sudo tar -xvf rootfs.tar.xz -C /tmp/alpine
```
#### Then:
```
sudo ruri -u /tmp/alpine
```
Or:      
```
sudo ruri -D
sudo ruri -u /tmp/alpine
```
Very simple as you can see.    
#### For command line examples, please see `ruri -hh`
#### make options:
```text
  make all            compile
  make install        install ruri to $PREFIX
  make static         static compile,with musl or glibc
  make static-bionic  static compile,with bionic
  make clean          clean
Only for developers:
  make dev            compile without optimizations, enable gdb debug information and extra logs.
  make asan           enable ASAN
  make check          run clang-tidy
  make format         format code
```
#### Dependent libraries:
For dynamic compilation:         
- libcap       
- libpthread
- libseccomp
     
For static compilation:         
- libcap-static
- libc-static
- libseccomp-static       
### Usage:    
```text
Usage:
  ruri OPTIONS
  ruri [ARGS] CONTAINER_DIRECTORY [COMMAND [ARG]...]

OPTIONS:
  -v                     Show version info
  -V                     Show version code
  -h                     Show helps
  -hh                    Show helps and commandline examples
  -D                     Run daemon
  -K                     Kill daemon
  -t                     Check if daemon is running
  -l                     List all running unshare containers
  -U [container_dir]     Umount&kill a container

ARGS:
  -u                     Enable unshare feature
  -n                     Set NO_NEW_PRIVS Flag
  -s                     Enable Seccomp
  -d                     Drop more capabilities for lower privilege
  -p                     Run privileged container
 --keep [cap]            Keep the specified cap
 --drop [cap]            Drop the specified cap
  -e [env] [value]       Set env to its value *Not work if init command is like `su -`
  -m [dir] [mountpoint]  Mount dir to mountpoint
  -w                     Disable warnings
```
&emsp;This program should be run with root privileges.        
&emsp;Please unset $LD_PRELOAD before running this program.              
### About Seccomp:
The seccomp rule of ruri is based on Docker's default seccomp profile. ruri does not provide the way to change it, but you can edit ruri.c and replace setup_seccomp() with your own config.      
### About daemon:
The daemon will create a socket file in $TMPDIR/ruri.sock (to be /tmp/ruri.sock on GNU/Linux) for interprocess communication. This file will be automatically removed after running `ruri -K`.         
### Full User Guide:
See `ruri(1)` in manpage after installation.   
### License:
Licensed under the MIT License      
Copyright (c) 2022-2023 Moe-hacker      

```
●●●●  ●   ● ●●●●   ●●●        ●   ●  ●●●         ●●●
●   ● ●   ● ●   ●   ●         ●   ● ●   ●       ●   ●
●●●●  ●   ● ●●●●    ●   ●●●●● ●   ●   ●●        ●   ●
●  ●  ●   ● ●  ●    ●          ● ●   ●     ●●●  ●   ●
●   ●  ●●●  ●   ●  ●●●          ●   ●●●●●  ●●●   ●●●
```
--------
<p align="center">「 咲誇る花 美しく、</p>    
<p align="center">散り行く運命 知りながら、</p>    
<p align="center">僅かな時の彩を 」</p>          
<p align="center">(>_×)</p>


[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FMoe-hacker%2Fruri.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2FMoe-hacker%2Fruri?ref=badge_large)