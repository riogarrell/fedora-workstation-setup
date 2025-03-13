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
  
    - Installing Git
    - Terminal: sudo dnf install git -y
  
    - Installing oh my zsh
    - Reference: https://github.com/ohmyzsh/ohmyzsh
    - Terminal: sh -c "$(curl -fsSL https://install.ohmyz.sh/)"
    - 
4. 
  
5. Installing VSCode
    - https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions
    - Add the Snap for auto update in the background.
