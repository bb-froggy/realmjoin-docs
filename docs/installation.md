# Installation

## Interactive Installation

In general you should deploy RealmJoin by using Intune app deployment. Intune will deploy one application only, the RealmJoin client. The application will be deployed through the MDM Channel with an Installer Type “Windows Installer trough MDM (*.msi)”. The Windows 10 clients will be auto enrolled to Intune during their AzureAD Join. 

### Release 

[RealmJoin Release Version](https://gkrealmjoin.s3.amazonaws.com/win-release/RealmJoin.msi)

### Beta Channel 

[RealmJoin Beta Version](https://gkrealmjoin.s3.amazonaws.com/win-beta/RealmJoin.msi)

### Canary Channel 

[RealmJoin Canary Version](https://gkrealmjoin.s3.amazonaws.com/win-canary/RealmJoin.msi)

## Command Line Installation

You may download and install RealmJoin in a single step by using the following command line. This may help especially when testing scenarios or new software packages in virtual machines.

### Release Channel 

```
@powershell -NoProfile -ExecutionPolicy unrestricted 
-Command "((new-object net.webclient).DownloadFile('https://gkrealmjoin.s3.amazonaws.com
/win-release/RealmJoin.exe', 'realmjoin.exe'))" && .\realmjoin.exe
```

### Beta Channel 

```
@powershell -NoProfile -ExecutionPolicy unrestricted 
-Command "((new-object net.webclient).DownloadFile('https://gkrealmjoin.s3.amazonaws.com
/win-beta/RealmJoin.exe', 'realmjoin.exe'))" && .\realmjoin.exe
```

### Canary Version

```
@powershell -NoProfile -ExecutionPolicy unrestricted 
-Command "((new-object net.webclient).DownloadFile('https://gkrealmjoin.s3.amazonaws.com
/win-canary/RealmJoin.exe', 'realmjoin.exe'))" && .\realmjoin.exe
```

## Silent Installation

When installing RealmJoin during unattend OS installation or any other non-interactive
deployment method you may favour not to have any UI interaction during installation. To
install RealmJoin in such a scenario use the silent installation option:

```
reamjoin.exe -install
```
