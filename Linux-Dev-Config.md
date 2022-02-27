# Linux Dev Config

## Intellij

### Unpack Intellij
```
tar -zxvf ideaIC-2021.3.2.tar.gz
```

### Add Intellij to The PATH
```
PATH="$HOME/.cargo/bin:$HOME/JetBrains/Intellij/idea-IC-XYZ/bin${PATH:+:${PATH}}"

alias intellij='idea.sh'
```

### Create A Desktop Entry
```
[Desktop Entry]
Version=1.0
Type=Application
Name=IntelliJ IDEA Community Edition
Icon=/home/augusto/JetBrains/Intellij/idea-IC-213.6777.52/bin/idea.svg
Exec="/home/augusto/JetBrains/Intellij/idea-IC-213.6777.52/bin/idea.sh" %f
Comment=Capable and Ergonomic IDE for JVM
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-idea-ce
StartupNotify=true

```

## VSCode
### Installing
1. Download 
2. `sudo dpkg -i code.deb`

## Docker

### Set up the repository
Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```
 sudo apt-get update
 sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Add Docker’s official GPG key:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88 by searching for the last 8 characters of the fingerprint:

`sudo apt-key fingerprint 0EBFCD88`

**OUTPUT**
```
pub rsa4096 2017-02-22 [SCEA]
9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88
uid [ unknown] Docker Release (CE deb) <docker@docker.com>
sub rsa4096 2017-02-22 [S]
```

Use the following command to set up the stable repository:

- `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
- The above command in linux mint probably has issues regarding de lsb_release -cs

### Install Docker Engine
Update the apt package index, and install the latest version of Docker Engine and containerd, or go to the next step to install a specific version:

```
 sudo apt-get update
 sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### Create a user
The docker group is created but no users are added to it. You need to use sudo to run Docker commands. Create a non-root user which will be added to the docker group:

```
adduser user
usermod -aG docker user
```

Restart the Docker service:

```
systemctl restart docker
```

### Reference
[Install Docker CE on Ubuntu 18.04 - 20.04q](https://www.vultr.com/docs/install-docker-ce-on-ubuntu-18-04/)

### [Linux Mint Problem](https://stackoverflow.com/a/45881841)
- [Stackoverflow to get UBUNTU_CODENAME](https://stackoverflow.com/a/43639310)
- [Stackoverflow Understanding the Problem](https://stackoverflow.com/a/45881841)]