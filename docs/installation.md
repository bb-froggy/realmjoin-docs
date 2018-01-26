# Installation

RealmJoin can be deployed on a device using one of multiple ways, depending on the individual scenario. As a first step, download the RealmJoin installer of your choice and procede to the desired installation method.
## Download RealmJoin Client 
### Release 
[RealmJoin Release Version](https://gkrealmjoin.s3.amazonaws.com/win-release/RealmJoin.msi)
### Beta Channel 
[RealmJoin Beta Version](https://gkrealmjoin.s3.amazonaws.com/win-beta/RealmJoin.msi)
### Canary Channel 
[RealmJoin Canary Version](https://gkrealmjoin.s3.amazonaws.com/win-canary/RealmJoin.msi)

## Via Microsoft Intune
There are different ways to install and enroll RealmJoin in Microsoft Intune. If a more-visual configuration experience is desired, the interactive configuration of deployment can be carried out using the Microsoft Intune portal. An alternative approach is the configuration of RealmJoin deployment in Intune via a powershell command line.

### Azure Intune Portal
The deployment of RealmJoin using Azure Intune requires only the .MSI installer to be configured. If the RealmJoin app in the desired release version is not registered in Intune, it can be added as a Line-of-Business app via the Azure Portal blade *Microsoft Intune / Mobile Apps / Apps / Add*.  
  
![RJ Intune Deploy](./media/rj-intune-deploy.png)  
  
In the configuration tab basic and advanced information can be provided.   
  
![RJ Intune Deploy2](./media/rj-intune-deploy2.png)  
  
Like any other application in Intune, ReamJoin then can be assigned to the desired user groups as (required) software. It is not neccessary to install additional software on the client devices to run RealmJoin. RealmJoin will be deployed on the client devices on next Azure sync.

### Windows Defender Exceptions
RealmJoin might be recognized by the *Windows Defender* as a possible thread. While this behaviour is not certain, it is recommended to implement some Windows Defender exceptions. Create a new device configuration profile, type *Device restriction*, or edit your existing profile and add the following *Windows Defender Antivirus Exceptions*:  
* Files and folders  
`%ProgramFiles%\RealmJoin`  
* Processes   
`%ProgramFiles%\RealmJoin\RealmJoin.exe`    
`%ProgramFiles%\RealmJoin\RealmJoinService.exe`    
`%ProgramFiles%\RealmJoin\RealmJoinUpdate.exe`    

### Powershell
It is possible to configure Intune device configurations, so that a powershell script is executed on the client which downloads and installs the RealmJoin software:    
```
# check if AAD joined
if (Test-Path HKLM:\SYSTEM\CurrentControlSet\Control\CloudDomainJoin\TenantInfo\<ID>)
{
    $url = "https://gkrealmjoin.s3.amazonaws.com/win-beta/RealmJoin.msi"
    $filePath = "c:\windows\temp\RealmJoin.msi"
    $ProgressPreference = 0
    Invoke-WebRequest $url -OutFile $filePath -UseBasicParsing 
    & $filePath /quiet
}

```
where <ID> is the corresponding tenant ID. The script may then be assigned:  
  ![RJ Intune Deploy3](./media/rj-intune-deploy3.png)  
  
## Interactive Installation
If an administrator wants to install RealmJoin on a device without mass deployment or the Microsoft Intune infrastructure, he/she may download the MSI and do an interactive installation or copy one of the command lines below to download and run in a single step.

## Command Line Installation
You may download and install RealmJoin in a single step by using the following command lines. This may help especially when testing scenarios or new software packages in virtual machines.

### Release Channel 
```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "((new-object net.webclient).DownloadFile('https://gkrealmjoin.s3.amazonaws.com /win-release/RealmJoin.exe', 'realmjoin.exe'))" && .\realmjoin.exe
```
### Beta Channel 
```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "((new-object net.webclient).DownloadFile('https://gkrealmjoin.s3.amazonaws.com
/win-beta/RealmJoin.exe', 'realmjoin.exe'))" && .\realmjoin.exe
```
### Canary Version
```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "((new-object net.webclient).DownloadFile('https://gkrealmjoin.s3.amazonaws.com
/win-canary/RealmJoin.exe', 'realmjoin.exe'))" && .\realmjoin.exe
```

### Silent Installation
When installing RealmJoin during unattend OS installation or any other non-interactive deployment method you may favour not to have any UI interaction during installation. To install RealmJoin in such a scenario use the silent installation option:

```
reamjoin.exe -install
```

