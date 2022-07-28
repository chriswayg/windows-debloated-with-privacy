# Windows 10 Enterprise 21H2
- On Gigabyte EP45-UD3L, Core 2 Quad Q9400, 8GB DDR2 PC2-8500, Asus GTX 660Ti
## Download from MS
### MyDigitalLife ESD Repository - Get latest version

* [https://forums.mydigitallife.net/threads/windows-10-esd-repository.59082/](https://forums.mydigitallife.net/threads/windows-10-esd-repository.59082/) 

---

**Download Version 21H2**

Client Business Volume ISO Edition List:
- Windows 10 Education
- Windows 10 Enterprise
- Windows 10 Pro

- http://b1.download.windowsupdate.com/d/upgr/2022/05/19044.1706.220505-0136.21h2_release_svc_refresh_clientbusiness_vol_x64fre_en-us_03d0a0dfebf88acfce0e6f870cba95ad3b3221c9.esd

---

## Convert to ISO
1. Download the latest decryption package `esd-decrypter-wimlib` from [WHD/scripts · abbodi1406 · GitHub](https://github.com/abbodi1406/WHD/tree/master/scripts), and extract its contents to a folder with a simple path.
	- [Download esd-decrypter-wimlib-63.7z · GitHub](https://github.com/abbodi1406/WHD/blob/master/scripts/esd-decrypter-wimlib-63.7z)
2. Move the ESD file to the same folder. Make sure that the ESD file is not read-only or blocked.
3. Right click on `decrypt.cmd` and 'Run as administrator' (this requires that only 1 ESD file is present in the current directory).
4. ESD file contains 6 editions
	- Select Option 2 - Include one edition
5. When the list of editions is shown
	- Enter edition number 3 for Enterprise
	- This will create an ISO with Enterprise edition only
6. On the next screen select option 1:
	- 1 Create ISO with install.wim (this is the most preferable option, which will convert ESD file to a regular ISO distribution that contains standard install.wim file)
7. This will take a while...
	- `Creating Setup Media Layout... boot.wim file... install.wim file`

- More details in the ReadMe.txt

## Create USB Installer
- Plug in a 8GB or more USB flash drive
- in [Rufus](https://rufus.ie/en/#) choose 
	- Select the Windows 10 ISO
	- Partition scheme: MBR install
	- Target System: BIOS (or UEFI-CSM)

## BIOS settings
- Based on “Optimized Defaults”
- Keep “Full Screen Logo Show” due to buggy monitor not switching on without it 
- PEG: use GPU on PCIe
- Refrained from overclocking due to very old hardware resulting in lack of stability 

## Install Windows 10 
- **Do not use Internet**, unplug Ethernet, do not log into Wifi
- Only USB2 ports are available on this board, making this a slow install 
- Use a port on the back
- F12 for Boot Menu, select Harddisk+ and select USB to boot
- press any key to boot from USB
- when cursor blinking, wait for 5 to 10 minutes to boot

### First boot
- English Philippines 

### Second boot
- Basics
	- Region: Philippines
	- Keyboard: US
	- Add layout: Germany 
	- Skip second keyboard layout 
- Network 
	- click: I don’t have Internet 
	- Click: continue with limited setup

### Third boot
- Network 
	- click: I don’t have Internet 
	- Click: continue with limited setup
- Account (local account)
	- Name
	- Password
	- Security Questions 1-3
- Services - Choose privacy settings 
	- All 6: No
* Wait for automatic login to the initial local user account 

## Configure Windows 10
### Taskbar
- Arrange shortcuts on Taskbar
	- Show Tasks, Snip, Explorer, Edge
	- News and Interests -> Turn Off

### Privacy
* **Keep Internet disconnected** in order to setup privacy settings first and disable Telemetry before MS can transmit data

### Settings
* in UAC: do not dim my desktop

### Windows10Debloater
- Do this first before installing anything else
- Download Zip from [GitHub - Sycnex/Windows10Debloater: Script to remove Windows 10 bloatware.](https://github.com/Sycnex/Windows10Debloater)
- Windows10DebloaterGUI
	1. Download the .zip file on the main page of the GitHub and extract the .zip file to your desired location
	2. Once extracted, open PowerShell as an Administrator
	3. Enable PowerShell execution `Set-ExecutionPolicy Unrestricted -Force`
	4. On the prompt, change to the directory where you extracted the files:   e.g. - `cd c:\Users\Public\Scripts\Windows10Debloater`
	5. Next, to run the script, enter in the following: `.\Windows10SysPrepDebloater.ps1 -Debloat -Privacy`
	6.  Then run: `.\Windows10DebloaterGUI.ps1` to *Uninstall OneDrive*
	7. In additional user accounts just run: `.\Windows10DebloaterGUI.ps1` if some apps have reappeared

### Install Graphics Driver
* Driver file should be on the USB installer
- Nvidia Graphics Driver
	- Custom: Only the graphics driver
	- Clean installation 

### Telemetry, Updates & Lock Screen
* Start the Local Group Policy Editor
	* create a shortcut for Local Group Policy Editor  `gpedit.msc` on the start menu and add it to *Windows Administrative Tools*
* Use Group Policy Editor to set your organization’s telemetry level: 
	* From Local Group Policy Editor, go to 
		* Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds. 
	* Double-click 'Allow Telemetry'
	* Select Enable
	* In the Options box, select Level 0, and then click OK 
* Delay Updates
	* Go to: Computer Configuration > Administrative Templates > Windows Components > Windows Update > Windows Update for Business
	* Quality Updates: defer 7 days
	* Feature Updates - Semi Annual Channel: defer 90 days
* Disable Lock Screen
	* Go to: Computer Configuration > Policies > Administrative Templates > Control Panel> Personalization
	* Enable: "Do not display the lock screen"
* Disable Cortana (optional, as already done in debloater)
	* Go to: Computer Configuration > Administrative Templates > Windows Components > Search 
	* Allow Cortana - disable Cortana 

### Reconnect internet  & Install Windows 10 Updates
- Reconnect internet 
- Windows Update -> Check for Updates
- Wait for Updates to finish and Restart when finished (configure System and Edge while waiting)

### System
* System - About - Advanced System Settings - Advanced
	* Static Swapfile at 2024 MB
* also change Computer Name

### Chris Titus Windows Tool
[The Ultimate Windows Utility](https://christitus.com/windows-tool/)
- Reinstall "App Installler" from MS Store, in case it was uninstalled by the Debloater
- From an Elevated (Run as Administrator) PowerShell prompt run:
`iwr -useb https://christitus.com/win | iex`
- Install
	- Firefox
	- Signal, Skype, Zoom
	- Adobe Reader DC, Notepad++
	- VLC
	- 7-Zip, Bitwarden, Everything Search, HWinfo, TreeSize, Windows Terminal
- then remove Icons from Desktop
- Tweaks
	- Desktop
	- Check also: Show File Extensions

### Privacy
* in Settings -> Privacy, set everything "Off" except:
	* Camera
		* Camera: On
		* Allow Desktop Apps: On
	* Microphone
		* Camera: On
		* Allow Desktop Apps: On
	* Notifications: On
	* Documents: On
	* Pictures: On
	* Videos: On
	* File System: On

### Configure Edge Browser
- Upon first launch
	- Sync -> Start without your data
	- Google -> Continue without this data
	- Uncheck; "Make MS experience more useful"
* Start Screen
	* Custom: all Off except for "Show Quick Links"
- Settings
	- Privacy -> Strict
	- (scroll down) Address bar and search -> Search Engine -> DuckDuckGo
	- Start -> Open tabs from previous sessions
- Extensions
	- uBlock Origin
		- Unckeck: Show the number of blocked requests
		- Filter Lists -> add German

### Configure Firefox  Browser
* Firefox Home
	* Shortcuts: 1 or 2 rows
	* Recent Activity: On
* General -> Startup -> Open previous windows and tabs
- Search
	- Add search bar in toolbar
	- Default Search Engine -> DuckDuckGo
	- Privacy -> Strict
		- Allow Firefox... Off
- Add-ons
	- uBlock Origin
		- Unckeck: Show the number of blocked requests
		- Filter Lists -> add German

### Install 
* LibreOffice (stable)
	* Custom -> German Dictionary
	* Open MS Office Documents
* Autoruns
	* [Autoruns for Windows - Windows Sysinternals | Microsoft Docs](https://docs.microsoft.com/en-us/sysinternals/downloads/autoruns)
	* Copy to Program Files & create Start Menu shortcut in Windows System
	* disable Skype autostart
* Prime95 
* Winaero 
	* Classic Sticky Notes
	* (optional) Winaero Tweaker

### Install Windows 10 Digital License (HWID)
* Microsoft Activation Scripts - OpenSource
	*  A collection of scripts for activating Microsoft products using HWID / KMS38 / Online KMS activation methods with a focus on open-source 
- **Method 1 - PowerShell**
	- [Microsoft Activation Scripts](https://massgrave.dev)
	* On Windows 10/11, right click on windows start menu, select PowerShell or Terminal.
	* Copy-paste the below code and press enter
	`iwr -useb https://massgrave.dev/get | iex`
- **Method 2 - Traditional**
	* [GitHub - massgravel/Microsoft-Activation-Scripts](https://github.com/massgravel/Microsoft-Activation-Scripts)
	* 	Download the file named 'MAS_1.5_Password_1234.7z' from  [here](https://github.com/massgravel/Microsoft-Activation-Scripts/releases) 
	* Extract this file with 7zip (Password is 1234)
	* Go to the folder named 'All-In-One-Version'
	* Run the file named 'MAS_1.5_AIO_CRC32_21D20776.cmd'
- **Options**
	* You will see the activation options, follow onscreen instructions.
	* Use HWID (1)
	* Check activation using the script (4) and (5)

### Optional Configuration
* Personalize Windows: Themes, Colors
	* Download Themes without MS Account: [Desktop Themes](https://support.microsoft.com/en-us/windows/desktop-themes-94880287-6046-1d35-6d2f-35dee759701e) (double-click to store)
* Automatic login
  * Use the Windows key + R keyboard shortcut to open the Run window. 
  * Run `regedit` and navigate to
  * `\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PasswordLess\Device\`
    * right-click [DevicePasswordLessBuildVersion]
    * and select [Modify..] then change [Value Data] to 0 {zero!}
	* Run `netplwiz` 
	  * Click your account within the Users for this computer field. 
	  * Click the checkbox beside Users must enter a user name and password to use this computer. ... 
	  * Click Apply and enter the password twice. Click OK!
* Reverse Mouse Scroll Direction (like in macOS)
  - [How to reverse mouse and touchpad scrolling direction on Windows 10 | Windows Central](https://www.windowscentral.com/how-reverse-scrolling-direction-windows-10)

## User Accounts
- Computer Management -> Local Users and Groups -> Users -> New User
	- Name, Password
	- Check: Password never expires
	- Create
- Upon first login: Services -> Privacy -> No (to all 4)
- If OneDrive still shows up run: `.\Windows10DebloaterGUI.ps1` to *Uninstall OneDrive* for this account as well. 
	- Explorer shell might disappear, in this case run `shutdown /r`
- Configure Taskbar
	- Search (show)
	- News and Interests (hide)
	- Icons (select)
- Configure Browsers, Start Menu
- Configure Theme
- Configure LibreOffice

### Testing
* Admin PowerShell:  `sfc /scannow`
* Run Prime95 
