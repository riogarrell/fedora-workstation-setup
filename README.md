# fedora-workstation-setup
Things to do after installing fedora workstation

1. Updating the system:
    - GUI: Window Key > Software > Updates
    - Terminal: sudo dnf upgrade --refresh (Note: This cmd updates your system packages and refreshes the package metadata.)
  
2. Customizing your Desktop:
    - Installing COSMIC desktop environment on Fedora.
    - https://copr.fedorainfracloud.org/coprs/ryanabx/cosmic-epoch/
    - Terminal: dnf install @cosmic-desktop-environment

3. Terminal Customization:
    - Installing ZSH
    - Terminal: sudo dnf install zsh -y
    - Status: Complete!
    - Change Shell: chsh -s $(which zsh)
    - Status: Change completed
    - Logout and Login account to take effect
    - Note: $ = bash | ~ = zsh
  
    - Installing oh my zsh (install Git first check #6)
    - Reference: https://github.com/ohmyzsh/ohmyzsh
    - Terminal: sh -c "$(curl -fsSL https://install.ohmyz.sh/)"
  
      
4. Text Editor
    - Installing VIM
    - Terminal: sudo dnf install vim
    - Open VIM: vim
  
    - Customizing VIM
    - Terminal: vim ~/.vimsrc
    - Insert the following:
    - syntax on               " Enable syntax highlighting
    - set number              " Show line number
    - set relativenumber      " Show relative liine numbers
    - set tabstop=4           " Seet tab width to 4 spaces
    - set shiftwidth=4        " Use spaces instead of tabs
    - set cursorline          " Highlight the current line
  
    - VIM keys:
    - Insert Mode > Press i to start typing
    - Nomral Mode > Press Esc to exit insert mode
    - Save and Exit > Type :wq and press enter
    - Quit without Saving > Type :q! and press enter
    - Move to Start of Line > Press O
    - Move to End of Line > Press $
    - Delete Line > Press dd
    - Undo > Press u
    - Redo > Press Ctrl + r
  
    - 
  
5. Installing VSCode
    - https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions
    - Add the Snap for auto update in the background.
  
6. Installing Git
    - Terminal: sudo dnf install git -y
    - Verify Git
    - Terminal: git --version
    - Set the git name and email
    - Terminal: git config --global user.name <name>
    - Terminal: git confiig --global user.email <email@>
    - View git config
    - Terminal: git config --list
    - Check directory to confirm it is the local git repo (you will see .git)
    - Terminal: ls -la
  
    - Setup github and gitlab
    - generate ssh keygen
    - Terminal: ssh-keygen -C <email@>
    - Note: It will ask to set location and password, press enter to save it on default
    - Copy the generated pub key
    - Terminal: cat ~/.ssh/id_ed*****.pub
    - Open Github > Settings > SSH and GPG Keys > New > Save
    - Verify the gihub connection
    - Terminal: ssh -T git@github.com
    - Prompt: Are you sure you want to continue connecting? yes
    - Status: You've successfully authenticated, but GitHub does not provide shell access.

7. Installing Docker
    - Adding docker repo
    - Terminal: sudo dnf-3 config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
    - Install docker
    - Terminal: sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    - Verify docker
    - docker --version
    - Check docker status
    - Terminal: sudo systemctl status docker
    - Start docker
    - Terminal: sudo systemctl start docker
    - sudo docker run hello-world

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

Sample docker container running in the bacground
    - docker pull nginx -> this will pull nginx image on the docker repo
    - docker run -d -p 8000:8080 nginx -> -d = run the container in the background without any interaction, -p = port, you can access the container through port 8000 and 8080 is port number inside the container.
    - docker ps -> show running container
    - docker stop <container_id> -> stopping the running container
    
8. Installing TMUX
