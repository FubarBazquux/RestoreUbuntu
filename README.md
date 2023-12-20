Instructions:
sudo apt update
sudo apt install git -y
mkdir ~/Repos
cd ~/Repos
git clone https://github.com/FubarBazquux/RestoreUbuntu.git
cd RestoreUbuntu
./main > RestoreUbuntu.log

Don't run in the background initially as a sudo prompt needs to be handled. After that, CTRL-Z if desired

The OpenRGB install currently points to the package created for Debian Bookworm, which is what Ubuntu 23.10 is built from. Change this if the target operating system is different.

GitHub credentials setup:
    git config --global credential.helper store
Then do something that requires authentication, like pushing to a remote. It'll ask for username and access token, which will then be stored.

AWS CLI setup:
    aws configure

Backup cron job:
    crontab -e
    0 0 * * MON /home/administrator/Documents/Scripts/weeklyBackup.sh

Set up Google Drive access through Settings -> Online Accounts

Notes:
Barrier is no longer maintained. Synergy is a paid alternative, but the active maintainers of Barrier have moved to a new project, input-leap, found at github.com/input-leap/input-leap. This is currently in development without any active releases, but once that has an official release it should be substituted for the Barrier package. Barrier does not support Wayland, so it's tough luck until input-leap can get it supported.
