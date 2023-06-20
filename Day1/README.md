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
