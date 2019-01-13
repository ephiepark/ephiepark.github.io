---
layout: post
title: Setting up a box
---
Add following to ~/.bashrc to show current path on prompt
```
export PS1='$(whoami):$(pwd)] '
```
and run the following to make it effective.
```
source ~/.bashrc
```

In case of Redhat, add centos repo
Add following content to `/etc/yum.repos.d/centos1.repo` [guide](https://unix.stackexchange.com/questions/433046/how-do-i-enable-centos-repositories-on-rhel-red-hat)
```
[centos]
name=CentOS-7
baseurl=http://ftp.heanet.ie/pub/centos/7/os/x86_64/
enabled=1
gpgcheck=1
gpgkey=http://ftp.heanet.ie/pub/centos/7/os/x86_64/RPM-GPG-KEY-CentOS-7
```
And run the following command to check if it worked.
`sudo yum repolist`

In case of Redhat or Centos
```
yum install vim 
yum install git
yum install tmux
```

add `~/.tmux.conf` file with the following content to enable mouse scroll and mouse click for pane change.
```
# Make mouse useful in copy mode
setw -g mode-mouse on

# Allow mouse to select which pane to use
set -g mouse-select-pane on

# Allow xterm titles in terminal window, terminal scrolling with scrollbar, and setting overrides of C-Up, C-Down, C-Left, C-Right
set -g terminal-overrides "xterm*:XT:smcup@:rmcup@:kUP5=\eOA:kDN5=\eOB:kLFT5=\eOD:kRIT5=\eOC"

# Scroll History
set -g history-limit 30000

# Set ability to capture on start and restore on exit window data when running an application
setw -g alternate-screen on

# Lower escape timing from 500ms to 50ms for quicker response to scroll-buffer access.
set -s escape-time 50
```

Installing mosh 
mosh is in EPEL repo
1. download and enable EPEL repo [guide](https://www.tecmint.com/how-to-enable-epel-repository-for-rhel-centos-6-5/)
```
yum install wget
wget http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -ivh epel-release-latest-7.noarch.rpm
```

2. install mosh
```sudo yum --enablerepo=epel install mosh```
Now you can connect with command like
```mosh -ssh "ssh -i side_projects.pem" ec2-user@ec2-13-57-28-121.us-west-1.compute.amazonaws.com```

This seems useful, even though I am exactly sure what it does :) [guide](https://computervisiononline.com/blog/install-opencv-31-and-python-27-centos-7)
```sudo yum groupinstall 'Development Tools'```

Setting up opencv [guide](https://computervisiononline.com/blog/install-opencv-31-and-python-27-centos-7)

Setting up nuclide
```npm install -g nuclide```
