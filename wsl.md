## Using WSL 2 in Windows

1. Enable the Windows Subsystem for Linux. Open PowerShell as Administrator and run:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

2.  Check requirements for running WSL 2
    To update to WSL 2, you must be running Windows 10.

        - For x64 systems: Version 1903 or higher, with Build 18362 or higher.
        - For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
        - Builds lower than 18362 do not support WSL 2. Use the Windows Update Assistant to update your version of Windows.

    To check your version and build number, select Windows logo key + R, type winver, select OK. (Or enter the ver command in Windows Command Prompt). Update to the latest Windows version in the Settings menu.

3.  Enable Virtual Machine feature

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Restart your machine to complete the WSL install and update to WSL 2.

4. Download the Linux kernel update package - [WSL2 Linux kernel update package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
   note: If you're using an ARM64 machine, please download the [ARM64 package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi) instead

5. Set WSL 2 as your default version

```powershell
wsl --set-default-version 2
```

6. Install your Linux distribution of choice
   Open the [Microsoft Store](https://aka.ms/wslstore) and select your favorite Linux distribution. From the distribution's page, select "Get".
   - Ubuntu - https://www.microsoft.com/store/apps/9n6svws3rx71

## Docker Desktop WSL 2 backend - to use docker on linux sub system without install docker on sub system

1. require Download [Docker Desktop Stable 2.3.0.2](https://hub.docker.com/editions/community/docker-ce-desktop-windows/) or a later release.

2. follow the [guide](https://docs.docker.com/docker-for-windows/wsl/) to enable WSL 2 backend for Windows and enable docker with GPU

## List installations

```powershell
wsl --list
```

```powershell
wsl --list --running
```

## Run a specific distribution

```powershell
wsl -d <DistributionName>
```

## Remove Linux Distribution

```powershell
wsl -- unregister <DistributionName>
```

## Set a Default Linux Distribution

```powershell
wsl --setdefautl <DistributionName>
```

## Accessing Linux File from Windows

1. Linux files can be accessed at the network path `\\wsl$\`. This can be entered in the File Explorer address bar or any file open dialog.

2. example:

```
\\wsl$\<DistributionName>\home\<username>
```

## Accessing Windows Files from Linux

- Windows drives are mounted in the Linux /mnt/ directory. For example, D: drive at D:\ is available at:

```powershell
/mnt/d/
```

## Running Linux Commands from Windows

- example :

```sh
wsl ls -la
```

## Running Windows Applications from linux

- example to edit .bashrc in notepad:

```sh
notepad.exe ~/.bashrc
```
