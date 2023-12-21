# Instructions:

## Partition setup:
512 MiB fat32 parition for EFI at the start of the OS disk, `/boot/efi`\
RAM size x2 linux-swap partition\
Rest of OS drive as ext4 for `/`\
Data drive as ext4 for `/home/`

## Ensure swap parition is being loaded correctly:
Get swap UUID from GParted or something
```
sudo -H nvim /etc/fstab
UUID=[swap UUID]	none	swap	sw	0	0
```
Remove any unwanted swapfile mountings, e.g. `/swap.img`\
Reboot to ensure that the swap partition is working correctly: `swapon --show'\
Remove any unwanted and no longer used swap files.

## Pre-run checks
The OpenRGB install currently points to the package created for Debian Bookworm, which is what Ubuntu 23.10 is built from. Change this if the target operating system is different.

## Run script:
```
sudo apt update
sudo apt install git -y
mkdir ~/Repos
cd ~/Repos
git clone https://github.com/FubarBazquux/RestoreUbuntu.git
cd RestoreUbuntu
./main > RestoreUbuntu.log
```

Don't run in the background initially as a sudo prompt needs to be handled. After that, CTRL-Z if desired.

## After-run tweaks
### GitHub credentials setup
```
git config --global credential.helper store
```
Then do something that requires authentication, like pushing to a remote. It'll ask for username and access token, which will then be stored.

### AWS CLI setup
```
aws configure
```

### Backup cron job
```
crontab -e
0 0 * * MON /home/administrator/Documents/Scripts/weeklyBackup.sh
```

### Google Drive integration
Settings -> Online Accounts

### Syncthing
Search apps for Syncthing
Run the start app first, then the web UI
Configure as desired. Remember that delete commands are synced just as files are, so if you want to delete from one device but not another, disconnect the folder sync or move/copy the files elsewhere on the machine that needs them before deleting anything.

## Notes:
Barrier is no longer maintained. Synergy is a paid alternative, but the active maintainers of Barrier have moved to a new project, input-leap, found at github.com/input-leap/input-leap. This is currently in development without any active releases, but once that has an official release it should be substituted for the Barrier package. Barrier does not support Wayland, so it's tough luck until input-leap can get it supported.
