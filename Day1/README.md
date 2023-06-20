# Day 1

# Day 1

## 📌 Installing Git in Windows
<pre>
https://gitforwindows.org/
</pre>

## 📌 Installing Git in Ubuntu Linux Distribution
<pre>
sudo add-apt-repository ppa:git-core/ppa 
sudo apt update
sudo apt install git
</pre>

## 📌 Installing Git in RedHat Family Linux Distributions
```
sudo yum install -y epel-release && sudo yum -y install git
sudo dnf install git
```

## Check your git version
```
git --version
```

## 🔖 How to clone this repository from Git Bash CLI ?
```
cd ~
git clone https://github.com/tektutor/git-us-june2023-batch1.git
cd git-us-june2023-batch1
```

## Types of Version Control System 
1. Local Version Control System (LVCS)
2. Centralized Version Control System (CVCS)
3. Distributed Version Control System (DVCS)


#### Local Version Control System

#### Centralized Version Control System (CVCS)
- follows client/server architecture
- Example
  - Perforce
  - p4/p4v client tool
  - perforce server tool
- Advantages
  - multi-user, hence all team members would be collaborate
- Disadvantages
  - doesn't support working offline
 
#### Distributed Version Control System (DVCS)
- Example
  - Git/GitHub
- Git Overview
  - opensource tool developed by Linus Torvalds
- Advantages
  - multi-user
  - can work offline unlike CVCS(eg: Perforce)


# Git Commands

## Checking version
```
git --version
```

## Perform some basic git configurations
```
git config --global user.name "Jeganathan Swaminathan"
git config --global user.email "mail2jegan@gmail.com"
git config --global core.editor vim
```

Expected output
<pre>
jegan@tektutor.org:~$ mkdir -p git-demo
jegan@tektutor.org:~$ cd git-demo
jegan@tektutor.org:~/git-demo$ ls

jegan@tektutor.org:~/git-demo$ git config --global user.name "Jeganathan Swaminathan"
jegan@tektutor.org:~/git-demo$ git config --global user.email "mail2jegan@gmail.com"

jegan@tektutor.org:~/git-demo$ git config --global --list
credential.helper=cache --timeout=9999999999
pull.rebase=false
core.editor=vim
user.name=Jeganathan Swaminathan
user.email=mail2jegan@gmail.com
init.defaultbranch=main
</pre>


## Lab - Creating a local Git repository
```
cd ~
mkdir -p git-demo
cd git-demo
git init

git config --local user.name "Nitesh Jeganathan"
git config --local user.email "mail2nitesh@gmail.com"
```

