## Install docker in windows. (Home x62)

1. Download and Install `Docker Desktop for Windows` from an official link: https://docs.docker.com/docker-for-windows/install/
2. Download and Install `wsl-2-backend` from an official link: https://docs.docker.com/docker-for-windows/install/#wsl-2-backend
3. Follow manual Installation Guide https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-1---enable-the-windows-subsystem-for-linux

## Install docker in linux/ubuntu 
### Prerequisites
#### Before installing Docker, you need to make sure that the following things are available on your system:

`Ubuntu 18.04 64-bit operating system.`
<br>
`Your user account with sudo privileges.`
<br>
`Command-line interface / terminal.`

#### Step 1: Update Repositories
##### Before beginning, it’s a good idea to update the local database of your software to make sure that there is access to the latest revisions.
##### To do so, run the following command on the terminal:

> sudo apt-get update

#### Step 2: Remove prior installations
##### Next, you need to make sure that your system does not have any prior Docker software installation that may be outdated. For that, run:

> sudo apt-get remove docker docker-engine docker.io

#### Step 3: Install Docker
##### To install Docker on Ubuntu 18.04, run the following command in the terminal:

> sudo apt install docker.io

#### Step 4: Start and automate Docker
##### In order for Docker to be up and running at system startup, run the following commands one by one:

> sudo systemctl start docker
> sudo systemctl enable docker

#### Step 5: Check version
##### To verify whether the installation has been successful, it is a good idea to verify the Docker version number installed. For that, run:

> docker --version

## The version number of the installed Docker software will be visible on the terminal.
