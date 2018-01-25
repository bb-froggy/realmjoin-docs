# Packaging In-Depth


## Preface

Most of the command lines below need to be run with adminitrative rights. As RealmJoin itself will install Chocolatey and machine Craft packages from within the System context, the command lines can also be run from a System command prompt to resemble the production situation as close as possible.  
To open a System command prompt, the tool `psexec` from the [Windows Sysinternals](https://docs.microsoft.com/en-us/sysinternals/) tools can be used: `psexec /d /i /s cmd.exe`


### Updating to the Latest RealmJoin Core Extension

In some cases, it may be necessary to update to the latest version of the RealmJoin Core Extension for the latest development features to become available:  
`choco upgrade realmjoin-core.extension -y --force`


## Testing Chocolatey Packages from Source

To test a Chocolatey package from source without packing, building or deploying it, a helper within the RealmJoin Core Extension can be used. Change to the folder were the package sources are located (i.e. where the `.nuspec` file is located) and run the following command (as Administrator!):  
`"%ProgramData%\chocolatey\extensions\realmjoin-core\choco-install-local-nuspec-file.bat"`

This command will also accept parameters like `-uninstall` (to uninstall instead of installing) and `-params` (to pass args like they would be specified in the RealmJoin Backend package definition).

Also, the contents of the `blobs` folder will automatically be copied to the temporary location where they would normally be downloaded to. Therefore the download of blob files from the RealmJoin CDN might fail (in case a file has never been deployed to the CDN), but the installation should still complete successfully as Chocolatey will detect that a file with the correct name and checksum is already available locally.

Except for very specific cases, this command should also work from a folder shared with a virtual machine from outside (e.g. VMware Shared Folders or [local drives shared with Hyper-V guests in enhanced session mode](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/learn-more/use-local-resources-on-hyper-v-virtual-machine-with-vmconnect)). This might be helpful if package development and testing are done on two different (virtual) machines.


## Packing Chocolatey Packages Locally for Testing

In specific cases (if the `blobs` folder is not being used at all or if it's contents have already been deployed to the RealmJoin CDN before, see above), a package can also be packed locally for testing by running the following command from from the folder where the `.nuspec` file is located:  
`choco pack`

On the testing machine, a normal file system folder can be added as a Chocolatey repository, e.g.:  
`choco source add -n=rjlocaltemp -s"c:\temp"`

The resulting package (`.nupkg`) from step 1 can then be copied to this folder and be installed by Chocolatey natively:  
`choco install customername-packagename -y --force`


## Importing the Chocolatey and RealmJoin Cmdlets into a PowerShell Session

To import all Chocolatey and RealmJoin cmdlets into a PowerShell session, the following PowerShell command can be used:  
`Import-Module "$env:ProgramData\chocolatey\helpers\chocolateyInstaller.psm1"`  
This will also import the RealmJoin Core extension module and can be useful to run some of it's cmdlets interactively, e.g. `Get-ChocolateyRealmjoinRegistryUninstallInfo`

If run with administrative rights, there are a few more development cmdlets available to load package information from a `.nuspec` file and to even run a chocolatey script (e.g. `chocolateyInstall.ps1`) directly from within the PowerShell session:
* `Initialize-RealmjoinChocoDevChocoEnvironment [[-nuspecFile] <string>] [[-packageName] <string>] [[-packageVersion] <string>] [[-packageTitle] <string>] [[-packageFolder] <string>] [[-params] <string>] [<CommonParameters>]`
* `Invoke-RealmjoinChocoDevScript [[-scriptToRun] <string>] [[-params] <Object>] [-uninstall] [-copyBlobs]`

For further details, please take a look at the files in `%ProgramData%\chocolatey\lib\realmjoin-core.extension` and specifically at the code in the following files:
* `extensions\choco-install-local-nuspec-file.bat`
* `extensions\choco-install-local-nuspec-file.ps1`
* `tools\RealmjoinChocoDevUtils\RealmjoinChocoDevUtils.bat`
* `tools\RealmjoinChocoDevUtils\RealmjoinChocoDevUtils.psm1`
