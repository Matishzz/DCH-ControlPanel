<p align="center">

  <img src="https://nvidia.wd5.myworkdayjobs.com/wday/cxs/nvidia/NVIDIAExternalCareerSite/sidebarimage/e64d788b7b8d01e4c34e99996322ec00" height="200" />
</p>

<p align="center">
If you need to install DCH Drivers for some reason and you are in the situation that you do not have the Microsoft Store and you cannot install the control panel for the reason that in the DCH Drivers the Control Panel is not included and its distribution is through the Microsoft Store. This script saves and configures the ContextMenu so you don't have to open nvcplui.exe every time you want to make a modification.
</p>

## Installation via powershell (Not working Powershell 2.0/1.0) 📺
```
powershell Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; Invoke-WebRequest "https://github.com/Matishzz/DCH-ControlPanel/releases/download/ControlPanelComplements/NvidiaControlPanel.bat" -OutFile "$env:temp\NvidiaControlPanel.bat"; Start-process $env:temp\NvidiaControlPanel.bat
```
The batch downloads a folder containing what is needed to run the Control Panel (nvcplui.exe and nvcpl.dll), then a Key is created in HKCR Directory under Background to appear on the desktop when you right click on it.

### Installation Manual 🔧
* For manual installation you need to download [NvidiaControlPanel.zip](https://github.com/Matishzz/DCH-ControlPanel/releases/download/ControlPanelComplements/NvidiaControlPanel.zip)
* Move it to [%temp%](https://win10faq.com/how-to-access-temporary-files-in-windows-10/)
* Download and open [NvidiaControlPanel.bat](https://github.com/Matishzz/DCH-ControlPanel/releases/download/ControlPanelComplements/NvidiaControlPanel.bat)

### Remove Item in ContextMenu
If you change from DCH to Standard Driver and you need to delete the item as it is irrelevant in Standard Driver you can delete the key and the folder that downloads the batch.
```
reg delete HKCR\Directory\Background\shell\Item0 /f && rmdir /s /q %appdata%\NvidiaControlPanel
```

### Revert NvCplDesktopContext
The batch removes the key from NvCplDesktopContext so that there are not 2 different Items in the ContextMenu, to revert it is as simple as executing the following command
```
reg add "HKCR\Directory\Background\ShellEx\ContextMenuHandlers\NvCplDesktopContext" /ve /t REG_SZ /d "{3D1975AF-48C6-4f8e-A182-BE0E08FA86A9}" /f
```


[![Twitter](https://img.shields.io/badge/-Twitter-black?style=for-the-badge&logo=twitter)](https://twitter.com/Matishzz)
[![Discord](https://img.shields.io/badge/-Discord-black?style=for-the-badge&logo=discord)](https://discord.io/MatishzzTweaking)
