Instructions:
sudo apt update
sudo apt install git -y
mkdir ~/Repos
cd ~/Repos
git clone https://github.com/FubarBazquux/RestoreUbuntu.git
cd RestoreUbuntu
./main > RestoreUbuntu.log

Don't run in the background initially as a sudo prompt needs to be handled. After that, CTRL-Z if desired

Notes:
Barrier is no longer maintained. Synergy is a paid alternative, but the active maintainers of Barrier have moved to a new project, input-leap, found at github.com/input-leap/input-leap. This is currently in development without any active releases, but once that has an official release it should be substituted for the Barrier package.
