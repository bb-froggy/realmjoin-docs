# Create Package
  
mkdir VLC  
   
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://github.com/realmjoin/realmjoin-package-jumpstarter/raw/master/JumpstartRealmJoinPackage.ps1'))"
   
Please enter the RealmJoin GitLab repository path: vlc
Please enter the RealmJoin GitLab repository name: VLC    
Please enter the RealmJoin GitLab repository namespace:     
Please enter the RealmJoin GitLab Access Token: (token)
Cloning into ....    
    
edit choco-package.nuspec    
edit readme.md    
    
run zzz....     
rename sample to .gitlab-ci.yml     
     
delete usersettings    
     
place binaries into blobs    
. achtung: versionsnummer mit in den binary-name     
. create hash    
     
edit tools/chocolateyInstall.ps1    
. choose matching install hive    
. set uninstall naming    
. set install parameter    
. set hash    
    
Optional: Dynamic Parameter    
     
git add, commit, push (git branch)     
  
  

