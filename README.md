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
  
    - Setup githug and gitlab
    - generate ssh keygen
    - Terminal: ssh-keygen -C <email@>
    - Note: It will ask to set location and password, press enter to save it on default
    - Copy the generated pub key
    - Terminal: cat ~/.ssh/id_ed*****.pub
    - Open github 

7. 
