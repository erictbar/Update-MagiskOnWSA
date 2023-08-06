# Update-MagiskOnWSA

These are instructions I use to update WSA manually with MagiskOnWSA installed. I am using Ubuntu 22.04 LTS on WSL2.
I am sharing it in case it can help others. Use at your own discression, update for your own personal usage, settings, directories, etc. and remember to backup

# Check Version
Check to see if you will actually need to update
- On https://store.rg-adguard.net/
- Package Family Name: MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe
- Choose version (Retail/RP/etc)

# Backup WSA: 
- %LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\
- Backup everything in LocalCache & LocalState folders﻿
- Take note of what apps are installed



# WSL2 - run script
## New
	gh repo clone LSPosed/MagiskOnWSALocal
 `cd ~/MagiskOnWSALocal`
## Update
	cd ~/MagiskOnWSALocal
	git pull
	
# Cleanup
Clearing `download` directory before running the script seems to prevent issues

## Issue with Mount images, cannot find valid erofs superblock on 2306.40000.4.0
Check https://github.com/LSPosed/MagiskOnWSALocal/issues/648#issuecomment-1666931560 
May need to edit build.sh to fix new issue

# Run
`./scripts/run.sh`

# Set:
Set yourself, with options for your preferences or device specs.  
*In my experience, if you have previously rooted your WSA, you will unable to update properly if you do not select yes to continue to root it here. The same may be true for some of the other options*

- x64	
- Retail (or a beta. Check issues first)
- Magisk version  Retail
- Install Gapps: Yes
- MindTheGApps(?)
- Keep Amazon
- Root: No 
- 7z

7z file will be in ./output

# Windows - Copying output
- Stop WSA
- Delete contents of C:\WSA
-- This is the directory where your modified WSA will be run from. It must be kept somewhere on the C: drive and cannot be edited while WSA is running
- Extract .7z file: 
	- `7z x output/[filename].7z -o/mnt/c/WSA/`
- Organize files in C:\WSA
- run `Install.ps1`
