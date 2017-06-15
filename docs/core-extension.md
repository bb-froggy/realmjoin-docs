# Core Extension

## Enable-ChocolateyRealmjoinAppv

### Syntax
Enable-ChocolateyRealmjoinAppv

### Parameters

```no-highlight
| Name | Alias | Description | Required? | Pipeline Input | Default Value |
| ---- | ----- | ----------- |:---------:|:--------------:| ------------- |
```

## Get-ChocolateyRealmjoinAppvPackageVfsPath
### Syntax
Get-ChocolateyRealmjoinAppvPackageVfsPath \[\[-appvPackage\] \<Object\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name        | Alias | Description | Required? | Pipeline Input | Default Value |
| ----------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| appvPackage | None  |             | false     | false          |               |
```

## Get-ChocolateyRealmjoinLocaleId
### Syntax
Get-ChocolateyRealmjoinLocaleId \[\[-localeString\] \<string\>\] \[\[-defaultLocaleId\] \<int\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name            | Alias | Description | Required? | Pipeline Input | Default Value |
| --------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| defaultLocaleId | None  |             | false     | false          |               |
| localeString    | None  |             | false     | false          |               |
```

## Get-ChocolateyRealmjoinLocaleMsiTransform
### Syntax
Get-ChocolateyRealmjoinLocaleMsiTransform \[\[-localeString\] \<string\>\] \[\[-localeTransformsFolder\] \<string\>\] \[\[-defaultLocaleId\] \<int\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name                   | Alias | Description | Required? | Pipeline Input | Default Value |
| ---------------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| defaultLocaleId        | None  |             | false     | false          |               |
| localeString           | None  |             | false     | false          |               |
| localeTransformsFolder | None  |             | false     | false          |               |
```

## Get-ChocolateyRealmjoinLogFilePath
### Syntax
Get-ChocolateyRealmjoinLogFilePath \[\[-operation\] \<string\>\] \[\[-target\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name      | Alias | Description | Required? | Pipeline Input | Default Value |
| --------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| operation | None  |             | false     | false          |               |
| target    | None  |             | false     | false          |               |
```

## Get-ChocolateyRealmjoinRegistryUninstallInfo
### Syntax
Get-ChocolateyRealmjoinRegistryUninstallInfo \[\[-keyNameFilter\] \<string\>\] \[\[-displayNameFilter\] \<string\>\] \[\[-publisherFilter\] \<string\>\] \[\[-versionGe\] \<version\>\] \[\[-versionGt\] \<version\>\] \[\[-versionLe\] \<version\>\] \[\[-versionLt\] \<version\>\] \[\[-filterScriptblock\] \<scriptblock\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name              | Alias | Description | Required? | Pipeline Input | Default Value |
| ----------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| displayNameFilter | None  |             | false     | false          |               |
| filterScriptblock | None  |             | false     | false          |               |
| keyNameFilter     | None  |             | false     | false          |               |
| publisherFilter   | None  |             | false     | false          |               |
| versionGe         | None  |             | false     | false          |               |
| versionGt         | None  |             | false     | false          |               |
| versionLe         | None  |             | false     | false          |               |
| versionLt         | None  |             | false     | false          |               |
```

## Get-ChocolateyRealmjoinRegistryUninstallStrings
### Syntax
Get-ChocolateyRealmjoinRegistryUninstallStrings \[-uninstallKeyNameFilter\] \<string\> \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name                   | Alias | Description | Required? | Pipeline Input | Default Value |
| ---------------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| uninstallKeyNameFilter | None  |             | true      | false          |               |
```

## Get-ChocolateyRealmjoinWebFile
### Syntax
Get-ChocolateyRealmjoinWebFile \[\[-fileName\] \<string\>\] \[\[-fileChecksum\] \<string\>\] \[\[-remoteFileName\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name           | Alias | Description | Required? | Pipeline Input | Default Value |
| -------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| fileChecksum   | None  |             | false     | false          |               |
| fileName       | None  |             | false     | false          |               |
| remoteFileName | None  |             | false     | false          |               |
```

## Import-ChocolateyRealmjoinPackageParameters
### Syntax
Import-ChocolateyRealmjoinPackageParameters \[\[-params\] \<string\>\] \[-setVariables\] \[-clearVariables\] \[-returnKeyValuePairs\] \[-returnParameterHashset\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name                   | Alias | Description | Required? | Pipeline Input | Default Value |
| ---------------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| clearVariables         | None  |             | false     | false          |               |
| params                 | None  |             | false     | false          |               |
| returnKeyValuePairs    | None  |             | false     | false          |               |
| returnParameterHashset | None  |             | false     | false          |               |
| setVariables           | None  |             | false     | false          |               |
```

## Install-ChocolateyRealmjoinAppvPackage
### Syntax
Install-ChocolateyRealmjoinAppvPackage \[\[-fileName\] \<string\>\] \[\[-fileChecksum\] \<string\>\] \[\[-DynamicDeploymentConfiguration\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name                           | Alias | Description | Required? | Pipeline Input | Default Value |
| ------------------------------ | ----- | ----------- |:---------:|:--------------:| ------------- |
| DynamicDeploymentConfiguration | None  |             | false     | false          |               |
| fileChecksum                   | None  |             | false     | false          |               |
| fileName                       | None  |             | false     | false          |               |
```

## Install-ChocolateyRealmjoinPackage
### Syntax
Install-ChocolateyRealmjoinPackage \[\[-installerFileName\] \<string\>\] \[\[-installerFileChecksum\] \<string\>\] \[\[-msiTransforms\] \<string\[\]\>\] \[\[-msiTransformsCabs\] \<string\[\]\>\] \[\[-additionalArgs\] \<string\[\]\>\] \[\[-silentArgs\] \<string\[\]\>\] \[\[-validExitCodes\] \<int\[\]\>\] \[\[-installers\] \<psobject\[\]\>\] \[\[-preActions\] \<scriptblock\>\] \[\[-postActions\] \<scriptblock\>\] \[\[-installPackage\] \<bool\>\] \[\[-noInstallMessage\] \<string\>\] \[-installerFileNameIsLocalPath\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name                         | Alias | Description | Required? | Pipeline Input | Default Value |
| ---------------------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| additionalArgs               | None  |             | false     | false          |               |
| installPackage               | None  |             | false     | false          |               |
| installerFileChecksum        | None  |             | false     | false          |               |
| installerFileName            | None  |             | false     | false          |               |
| installerFileNameIsLocalPath | None  |             | false     | false          |               |
| installers                   | None  |             | false     | false          |               |
| msiTransforms                | None  |             | false     | false          |               |
| msiTransformsCabs            | None  |             | false     | false          |               |
| noInstallMessage             | None  |             | false     | false          |               |
| postActions                  | None  |             | false     | false          |               |
| preActions                   | None  |             | false     | false          |               |
| silentArgs                   | None  |             | false     | false          |               |
| validExitCodes               | None  |             | false     | false          |               |
```

## Test-ChocolateyRealmjoinRegistryUninstallExists
### Syntax
Test-ChocolateyRealmjoinRegistryUninstallExists \[\[-keyNameFilter\] \<string\>\] \[\[-displayNameFilter\] \<string\>\] \[\[-publisherFilter\] \<string\>\] \[\[-versionGe\] \<version\>\] \[\[-versionGt\] \<version\>\] \[\[-versionLe\] \<version\>\] \[\[-versionLt\] \<version\>\] \[\[-filterScriptblock\] \<scriptblock\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name | Alias | Description | Required? | Pipeline Input | Default Value |
| ----------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| displayNameFilter | None  |             | false     | false          |               |
| filterScriptblock | None  |             | false     | false          |               |
| keyNameFilter     | None  |             | false     | false          |               |
| publisherFilter   | None  |             | false     | false          |               |
| versionGe         | None  |             | false     | false          |               |
| versionGt         | None  |             | false     | false          |               |
| versionLe         | None  |             | false     | false          |               |
| versionLt         | None  |             | false     | false          |               |
```

## Uninstall-ChocolateyRealmjoinAppvPackage
### Syntax
Uninstall-ChocolateyRealmjoinAppvPackage \[\[-name\] \<string\>\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name | Alias | Description | Required? | Pipeline Input | Default Value |
| ---- | ----- | ----------- |:---------:|:--------------:| ------------- |
| name | None  |             | false     | false          |               |
```

## Uninstall-ChocolateyRealmjoinPackage
### Syntax
Uninstall-ChocolateyRealmjoinPackage \[\[-uninstallerFile\] \<string\>\] \[\[-additionalArgs\] \<string\[\]\>\] \[\[-silentArgs\] \<string\[\]\>\] \[\[-validExitCodes\] \<int\[\]\>\] \[\[-subPackageName\] \<string\>\] \[\[-uninstallers\] \<psobject\[\]\>\] \[\[-uninstallInfo\] \<Object\>\] \[-WhatIf\] \[-Confirm\] \[\<CommonParameters\>\]
### Parameters

```no-highlight
| Name            | Alias | Description | Required? | Pipeline Input | Default Value |
| --------------- | ----- | ----------- |:---------:|:--------------:| ------------- |
| Confirm         | cf    |             | false     | false            |             |
| WhatIf          | wi    |             | false     | false            |             |
| additionalArgs  | None  |             | false     | false            |             |
| silentArgs      | None  |             | false     | false            |             |
| subPackageName  | None  |             | false     | false            |             |
| uninstallInfo   | None  |             | false     | true \(ByValue\) |             |
| uninstallerFile | None  |             | false     | false            |             |
| uninstallers    | None  |             | false     | false            |             |
| validExitCodes  | None  |             | false     | false            |             |
```
