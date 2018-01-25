# Core Extension

## Enable-ChocolateyRealmjoinAppv
### Syntax
Enable-ChocolateyRealmjoinAppv
## Install-ChocolateyRealmjoinAppvPackage
### Syntax
Install-ChocolateyRealmjoinAppvPackage \[\[-fileName\] \<string\>\] \[\[-fileChecksum\] \<string\>\] \[\[-DynamicDeploymentConfiguration\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                           Aliases Description Required? Pipeline Input? Default Value
----                           ------- ----------- --------- --------------- -------------
DynamicDeploymentConfiguration None                false     false                        
fileChecksum                   None                false     false                        
fileName                       None                false     false                        
```

## Uninstall-ChocolateyRealmjoinAppvPackage
### Syntax
Uninstall-ChocolateyRealmjoinAppvPackage \[\[-name\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name Aliases Description Required? Pipeline Input? Default Value
---- ------- ----------- --------- --------------- -------------
name None                false     false                        
```

## Get-ChocolateyRealmjoinAppvPackageVfsPath
### Syntax
Get-ChocolateyRealmjoinAppvPackageVfsPath \[\[-appvPackage\] \<Object\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name        Aliases Description Required? Pipeline Input? Default Value
----        ------- ----------- --------- --------------- -------------
appvPackage None                false     false                        
```

## Get-ChocolateyRealmjoinLocaleId
### Syntax
Get-ChocolateyRealmjoinLocaleId \[\[-localeString\] \<string\>\] \[\[-defaultLocaleId\] \<int\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name            Aliases Description Required? Pipeline Input? Default Value
----            ------- ----------- --------- --------------- -------------
defaultLocaleId None                false     false                        
localeString    None                false     false                        
```

## Get-ChocolateyRealmjoinLocaleMsiTransform
### Syntax
Get-ChocolateyRealmjoinLocaleMsiTransform \[\[-localeString\] \<string\>\] \[\[-localeTransformsFolder\] \<string\>\] \[\[-defaultLocaleId\] \<int\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                   Aliases Description Required? Pipeline Input? Default Value
----                   ------- ----------- --------- --------------- -------------
defaultLocaleId        None                false     false                        
localeString           None                false     false                        
localeTransformsFolder None                false     false                        
```

## Get-ChocolateyRealmjoinLogFilePath
### Syntax
Get-ChocolateyRealmjoinLogFilePath \[\[-operation\] \<string\>\] \[\[-target\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name      Aliases Description Required? Pipeline Input? Default Value
----      ------- ----------- --------- --------------- -------------
operation None                false     false                        
target    None                false     false                        
```

## Install-ChocolateyRealmjoinPackage
### Syntax
Install-ChocolateyRealmjoinPackage \[\[-installerFileName\] \<string\>\] \[\[-installerFileChecksum\] \<string\>\] \[\[-msiTransforms\] \<string\[\]\>\] \[\[-msiTransformsCabs\] \<string\[\]\>\] \[\[-additionalArgs\] \<string\[\]\>\] \[\[-silentArgs\] \<string\[\]\>\] \[\[-validExitCodes\] \<int\[\]\>\] \[\[-installers\] \<psobject\[\]\>\] \[\[-preActions\] \<scriptblock\>\] \[\[-postActions\] \<scriptblock\>\] \[\[-installPackage\] \<bool\>\] \[\[-noInstallMessage\] \<string\>\] \[-installerFileNameIsLocalPath\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                         Aliases Description Required? Pipeline Input? Default Value
----                         ------- ----------- --------- --------------- -------------
additionalArgs               None                false     false                        
installPackage               None                false     false                        
installerFileChecksum        None                false     false                        
installerFileName            None                false     false                        
installerFileNameIsLocalPath None                false     false                        
installers                   None                false     false                        
msiTransforms                None                false     false                        
msiTransformsCabs            None                false     false                        
noInstallMessage             None                false     false                        
postActions                  None                false     false                        
preActions                   None                false     false                        
silentArgs                   None                false     false                        
validExitCodes               None                false     false                        
```

## Uninstall-ChocolateyRealmjoinPackage
### Syntax
Uninstall-ChocolateyRealmjoinPackage \[\[-uninstallerFile\] \<string\>\] \[\[-additionalArgs\] \<string\[\]\>\] \[\[-silentArgs\] \<string\[\]\>\] \[\[-validExitCodes\] \<int\[\]\>\] \[\[-subPackageName\] \<string\>\] \[\[-uninstallers\] \<psobject\[\]\>\] \[\[-uninstallInfo\] \<Object\>\] \[-WhatIf\] \[-Confirm\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name            Aliases Description Required? Pipeline Input? Default Value
----            ------- ----------- --------- --------------- -------------
Confirm         cf                  false     false                        
WhatIf          wi                  false     false                        
additionalArgs  None                false     false                        
silentArgs      None                false     false                        
subPackageName  None                false     false                        
uninstallInfo   None                false     true (ByValue)               
uninstallerFile None                false     false                        
uninstallers    None                false     false                        
validExitCodes  None                false     false                        
```

## Import-ChocolateyRealmjoinPackageParameters
### Syntax
Import-ChocolateyRealmjoinPackageParameters \[\[-params\] \<string\>\] \[-setVariables\] \[-clearVariables\] \[-returnKeyValuePairs\] \[-returnParameterHashset\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                   Aliases Description Required? Pipeline Input? Default Value
----                   ------- ----------- --------- --------------- -------------
clearVariables         None                false     false                        
params                 None                false     false                        
returnKeyValuePairs    None                false     false                        
returnParameterHashset None                false     false                        
setVariables           None                false     false                        
```

## Test-ChocolateyRealmjoinRegistryUninstallExists
### Syntax
Test-ChocolateyRealmjoinRegistryUninstallExists \[\[-keyNameFilter\] \<string\>\] \[\[-displayNameFilter\] \<string\>\] \[\[-publisherFilter\] \<string\>\] \[\[-versionGe\] \<version\>\] \[\[-versionGt\] \<version\>\] \[\[-versionLe\] \<version\>\] \[\[-versionLt\] \<version\>\] \[\[-filterScriptblock\] \<scriptblock\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name              Aliases Description Required? Pipeline Input? Default Value
----              ------- ----------- --------- --------------- -------------
displayNameFilter None                false     false                        
filterScriptblock None                false     false                        
keyNameFilter     None                false     false                        
publisherFilter   None                false     false                        
versionGe         None                false     false                        
versionGt         None                false     false                        
versionLe         None                false     false                        
versionLt         None                false     false                        
```

## Get-ChocolateyRealmjoinRegistryUninstallInfo
### Syntax
Get-ChocolateyRealmjoinRegistryUninstallInfo \[\[-keyNameFilter\] \<string\>\] \[\[-displayNameFilter\] \<string\>\] \[\[-publisherFilter\] \<string\>\] \[\[-versionGe\] \<version\>\] \[\[-versionGt\] \<version\>\] \[\[-versionLe\] \<version\>\] \[\[-versionLt\] \<version\>\] \[\[-filterScriptblock\] \<scriptblock\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name              Aliases Description Required? Pipeline Input? Default Value
----              ------- ----------- --------- --------------- -------------
displayNameFilter None                false     false                        
filterScriptblock None                false     false                        
keyNameFilter     None                false     false                        
publisherFilter   None                false     false                        
versionGe         None                false     false                        
versionGt         None                false     false                        
versionLe         None                false     false                        
versionLt         None                false     false                        
```

## Get-ChocolateyRealmjoinRegistryUninstallStrings
### Syntax
Get-ChocolateyRealmjoinRegistryUninstallStrings \[-uninstallKeyNameFilter\] \<string\> \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                   Aliases Description Required? Pipeline Input? Default Value
----                   ------- ----------- --------- --------------- -------------
uninstallKeyNameFilter None                true      false                        
```

## Get-ChocolateyRealmjoinWebFile
### Syntax
Get-ChocolateyRealmjoinWebFile \[\[-fileName\] \<string\>\] \[\[-fileChecksum\] \<string\>\] \[\[-remoteFileName\] \<string\>\] \[-extractArchive\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name           Aliases Description Required? Pipeline Input? Default Value
----           ------- ----------- --------- --------------- -------------
extractArchive None                false     false                        
fileChecksum   None                false     false                        
fileName       None                false     false                        
remoteFileName None                false     false                        
```

## Get-RealmjoinComputerSystemInformation
### Syntax
Get-RealmjoinComputerSystemInformation
## New-RealmjoinScheduledTaskBootTrigger
### Syntax
New-RealmjoinScheduledTaskBootTrigger \[\[-Enabled\] \<bool\>\] \[\[-StartBoundary\] \<datetime\>\] \[\[-EndBoundary\] \<datetime\>\] \[\[-RepetitionInterval\] \<timespan\>\] \[\[-RepetitionDuration\] \<timespan\>\] \[\[-Delay\] \<timespan\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name               Aliases Description Required? Pipeline Input? Default Value
----               ------- ----------- --------- --------------- -------------
Delay              None                false     false                        
Enabled            None                false     false                        
EndBoundary        None                false     false                        
RepetitionDuration None                false     false                        
RepetitionInterval None                false     false                        
StartBoundary      None                false     false                        
```

## New-RealmjoinScheduledTaskLogonTrigger
### Syntax
New-RealmjoinScheduledTaskLogonTrigger \[\[-Enabled\] \<bool\>\] \[\[-StartBoundary\] \<datetime\>\] \[\[-EndBoundary\] \<datetime\>\] \[\[-RepetitionInterval\] \<timespan\>\] \[\[-RepetitionDuration\] \<timespan\>\] \[\[-Delay\] \<timespan\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name               Aliases Description Required? Pipeline Input? Default Value
----               ------- ----------- --------- --------------- -------------
Delay              None                false     false                        
Enabled            None                false     false                        
EndBoundary        None                false     false                        
RepetitionDuration None                false     false                        
RepetitionInterval None                false     false                        
StartBoundary      None                false     false                        
```

## New-RealmjoinScheduledTaskXml
### Syntax
New-RealmjoinScheduledTaskXml \[\[-Principal\] \<ScheduledTaskPrincipal\>\] \[\[-Action\] \<Object\[\]\>\] \[\[-Trigger\] \<Object\[\]\>\] \[\[-Enabled\] \<bool\>\] \[\[-ExecutionTimeLimit\] \<timespan\>\] \[\[-DeleteAfterFirstRunTaskName\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                        Aliases Description Required? Pipeline Input? Default Value
----                        ------- ----------- --------- --------------- -------------
Action                      None                false     false                        
DeleteAfterFirstRunTaskName None                false     false                        
Enabled                     None                false     false                        
ExecutionTimeLimit          None                false     false                        
Principal                   None                false     false                        
Trigger                     None                false     false                        
```

## New-RealmjoinShortcut
### Syntax
New-RealmjoinShortcut \[-shortcutPath\] \<string\> \[-targetPath\] \<string\> \[\[-targetArguments\] \<string\>\] \[\[-workingDirectory\] \<string\>\] \[\[-description\] \<string\>\] \[\[-iconLocation\] \<string\>\] \[\[-hotKey\] \<string\>\] \[\[-windowStyle\] \<int\>\] \[-forCurrentUser\] \[-onDesktop\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name             Aliases Description Required? Pipeline Input? Default Value
----             ------- ----------- --------- --------------- -------------
description      None                false     false                        
forCurrentUser   None                false     false                        
hotKey           None                false     false                        
iconLocation     None                false     false                        
onDesktop        None                false     false                        
shortcutPath     None                true      false                        
targetArguments  None                false     false                        
targetPath       None                true      false                        
windowStyle      None                false     false                        
workingDirectory None                false     false                        
```

## Remove-RealmjoinShortcut
### Syntax
Remove-RealmjoinShortcut \[-shortcutPath\] \<string\> \[-forCurrentUser\] \[-onDesktop\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name           Aliases Description Required? Pipeline Input? Default Value
----           ------- ----------- --------- --------------- -------------
forCurrentUser None                false     false                        
onDesktop      None                false     false                        
shortcutPath   None                true      false                        
```

## Format-RealmjoinShortcutPath
### Syntax
Format-RealmjoinShortcutPath \[-shortcutPath\] \<string\> \[-forCurrentUser\] \[-onDesktop\] \[-doNotCheckCreateFolder\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
Name                   Aliases Description Required? Pipeline Input? Default Value
----                   ------- ----------- --------- --------------- -------------
doNotCheckCreateFolder None                false     false                        
forCurrentUser         None                false     false                        
onDesktop              None                false     false                        
shortcutPath           None                true      false                        
```

