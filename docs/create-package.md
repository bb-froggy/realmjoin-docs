# Create Choco Package

The following documentation describes the creation of a VLC choco package.
  
## Create local repository folder

```mkdir VLC```

## Use Junpstarter to create repository

```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://github.com/realmjoin/realmjoin-package-jumpstarter/raw/master/JumpstartRealmJoinPackage.ps1'))"
```

* Please enter the RealmJoin GitLab repository path: vlc   
* Please enter the RealmJoin GitLab repository name: VLC Media Player   
* Please enter the RealmJoin GitLab repository namespace: (your namespace)   
* Please enter the RealmJoin GitLab Access Token: (your token)   
Cloning into ....  

## Edit Package

Use your favorite Visual Studio Code editor and edit ```choco-package.nuspec``` and ```readme.md```.

## TBD

* run zzz....
* rename sample... to .gitlab-ci.yml
* delete usersettings

## Add binaries into package

* Place binaries into ```blobs``` (add version into binary-name)
* create hash

## TBD

* edit tools/chocolateyInstall.ps1
* choose matching install hive
* set uninstall naming
* set install parameter
* set hash

## Optional: Dynamic Parameter
## git add, commit, push (git branch)


