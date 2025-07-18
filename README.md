# Fedora-Workstation-Setup
> Things to do after installing fedora workstation

## Updating the System
- Terminal:
```
sudo dnf upgrade --refresh -y
sudo dnf clean all
sudo systemctl reboot
```
- GUI: Window Key > Software > Updates

## Getting System & Hardware Information
- Terminal:
```
fastfetch
```

## Terminal Customization
### Installing ZSH
- Terminal:
- Install zsh 
```
sudo dnf install zsh -y
```
- Verify zsh
```
zsh --version
```
> Re-login account to take effect ~$ = bash | ~% = zsh
- Change shell
```
sudo chsh $USER
```
- Source: [Installing ZSH](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)


### Installing oh my zsh (install git first)
- Terminal:
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
> Reference: [https://github.com/ohmyzsh/ohmyzsh](https://ohmyz.sh/#install) [Documentation](https://github.com/ohmyzsh/ohmyzsh/wiki) [Auto Complete Plugins](https://gist.github.com/n1snt/454b879b8f0b7995740ae04c5fb5b7df) | re-open the terminal and type ps ax you will notice auto completion and suggestions
    


## Text Editor
### VIM
- Terminal:
- Installing vim 
```
sudo dnf install vim
```
- Customizing vim
```
vim ~/.vimsrc
```
- Input the following script:
```
syntax on               " Enable syntax highlighting
set number              " Show line number
set relativenumber      " Show relative liine numbers
set tabstop=4           " Seet tab width to 4 spaces
set shiftwidth=4        " Use spaces instead of tabs
set cursorline          " Highlight the current line
```
- VIM keys
```
Insert Mode > Press i to start typing
Nomral Mode > Press Esc to exit insert mode
Save and Exit > Type :wq and press enter
Quit without Saving > Type :q! and press enter
Move to Start of Line > Press O
Move to End of Line > Press $
Delete Line > Press dd
Undo > Press u
Redo > Press Ctrl + r 
```

### Installing VSCode
- https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions
  

## Installing Git
1. Install git
    - Open the terminal and follow the command below:
    ```
    sudo dnf install git -y
    ```
    - Verify Git
    ```
    git --version
    ```
    - Set the git name and email
    ```
    git config --global user.name <name>
    git confiig --global user.email <email@>
    ```
    - View git config
    ```
    git config --list
    ```
2. Setup github and gitlab
    - Open the terminal and follow the command below:
    - Generate ssh keygen
    ```
    ssh-keygen -C <email@>
    ```
    > Note: It will ask to set location and password, press enter to save it on default (e.g: /home/username/.ssh/id_ed***)
    - Copy the generated pub key
    ```
    cat ~/.ssh/id_ed*****.pub
    ```
    - Open Github > Settings > SSH and GPG Keys > New > Paste the key > Save
    - Verify the gihub connection
    ```
    ssh -T git@github.com
    Are you sure you want to continue connecting? yes
    You've successfully authenticated, but GitHub does not provide shell access.
    ```
    


## Installing Docker
- Terminal:
- Adding docker repo
```
sudo dnf-3 config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
```
- Install docker
```
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
- Verify docker
```
docker --version
```
- Check docker status
```
sudo systemctl status docker
```
- Start docker
```
sudo systemctl start docker
```
- Test docker
```
sudo docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit: https://docs.docker.com/get-started/
    - as default docker needs permission to run, lets add the user to docker group
    - Terminal: sudo usermod -aG docker $USER
    - Terminal: newgrp docker
    - Now run again the hello-world without using sudo, this should work else logout and login the account.
```

- Sample docker container running in the bacground:
- Get nginx image on docker repo
```
docker pull nginx
```
- create container and run in the background
```
docker run -d -p 8000:8080 nginx
```
> -d = run the container in the background without any interaction, -p = port, you can access the container through port 8000 and 8080 is port number inside the container.
- show running container
```
docker ps
```
- stop the running container
```
docker stop <container_id>
```    
    
## Installing TMUX
- Terminal:
```
sudo dnf install tmux -y
```
> To start TMUX, simply run the command tmux,  for more command: https://tmuxcheatsheet.com/

## Basic Automation
- Terminal:
- Create update script
```
vim update.sh
``` 
- input the following and save:
```
#!/bin/bash
echo "UPDATING SYSTEM..."
sudo dnf update -y
echo "CLEANING UP..."
sudo dnf clean all
```
- Change the file permission with execution
```
chmod +x update.sh
```
- Execute the script
```
./update.sh
```


## Installing BTOP - System Monitoring tool
- Terminal: 
```
sudo dnf install btop -y
btop
``` 


## Adding Binary to Home Directory
- Terminal:
  ```
  cd
  mkdir bin
  vi ~/.zshrc
  export PATH=$PATH:$HOME/bin
  :wq
  mv <path of the binary like ansible eg: ~/Downloads/ansible> bin
  . ./.zshrc
  ansible
  ```

## ISSUEs AND FIXES
* User login password not matching the keyring -> This is usualy happened when opening an app asking for keyring/password.
* Fix: Download "Passwords and Keys" on Fedora Software Downloader > Open and Check the Default keyring if available, if none lets proceeed on terminal.
* Termminal:
* cd ~/.local/share/keyrings
* ls -> you will see a login.keyring file, and lets remove it using this cmd -> rm login.keyring
* Once remove, try to open the app and it will ask a new keyring/password; you can put a password or simple leave it blank.
* Now check the Passwords and Keys, you will see a Default keyring.
