# Workflow (internal GK)

## First: Upload through customer  
The customer uses the *RealmJoin Organic Uploader* <https://realmjoin-uploader.azurewebsites.net/> to upload a * .zip file containing the .msi or .exe file as well as the instructions on the desired installation mode.

## Second: Get involved  
The customers upload triggers an automatic ticket in the GK ticketing system. Find the relevant upload ticket and assign it to yourself. The ticket may contain the *UUID* which is needed to identify the upload in the BLOB storage. 
**NOTE:** Currently it is not possible to track the upladed zip - file into the BLOB storage, resulting in a missing *UUID*. Therefore, it is currently neccessary to remember the timestamp of the ticket.

## Third: Find the file  

Use the *Microsoft Azure Storage Explorer* (install using RealmJoin if it not already done so) to find the upload corresponding to the *UUID* of the ticket or timestamp of the ticket. 
Due to different time zones, the hour in the tickets timestamp and the *MASE* timestamp may be deviate. If several blobs have the same timestamp or are too close, check their properties (right click) for the original filename. 
Save the file to your working directory. You might remove the upload in the storage after succesfully enrolling the package.

## Fourth: Check the requierments 

Before building your package, there are different checks to be performed:

1. Did the customer provide all information that is needed to create the package: EXE / MSI? Readme with installation requirements? ...? 
  + If not, get in touch with the customer to clarify the required information.
2. Is this package neccessary:
  * Check if the package already exists. If so: Same software version and parameters?
  * If the requested software exists in a different version: Might an update be more reasonable? Are different version required due to features or similar? 
  + Get in touch with the customer to discuss and clarify the need for a additional version of this package.
3. Is this package generic:
  * **ALWAYS TRY TO GO GENERIC** This will make maintaining and updating a lot easier, plus you may reuse the package for different users later on.
  * Does the customer request parameter or arguments that prevent the package to be used as a generic package? 
  * If so, check if those are really neccessary: How is the software installed? Instead of reg keys, is it possible to use installation parameters in the package assigning step to configure the software?
    Why do the customer need this configuration and not the generic package?
  + Get in touch with the customer, if neccessay and try to make the package generic.

**Do not start creating the package before you have a reasonable assumption of what to pack**

## Create your package  

The creation process demonstrated on a generic VLC player package. 

### Create local repository folder

```mkdir videolan-vlc-2.15```  
Convention: use small letters for all naming purposes and use *vedor-program-version* as folder name.

### Use Jumpstarter to create repository

To create a template for your package, use the following *Jumpstarter* command within the created folder:  
```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://github.com/realmjoin/realmjoin-package-jumpstarter/raw/master/JumpstartRealmJoinPackage.ps1'))"
```

* Please enter the RealmJoin GitLab repository path: videolan-vlc-2.15 (or leave empty)    
* Please enter the RealmJoin GitLab repository name: VideoLan - vlc   
* Please enter the RealmJoin GitLab repository namespace: (your namespace)   
* Please enter the RealmJoin GitLab Access Token: (your token)     
*Cloning into ....*

### Edit Package

The now existing repository may be used as a template for all types of packages: *organic*, *craft*, *chocolatey*. The *Readme.md* file contains instructions for the creation of either. 

* First, delete all files that are not neccessay for the desired package type. 
* 

Use your favorite Visual Studio Code editor and edit ```choco-package.nuspec``` and ```readme.md```.  
....


## Testing of the package  
<!-- 
Pr�fungen: 
Softwareversion, gibt es andere Versionen beim Kunden
Sind Args und Parametern sinnvoll, vllt statt custom lieber generic hinterher, nicht unbedingt zu viel User/Kundenspezifisch
Argumente f�r generic: Kosten und Updates (die sind schneller da)
Test der Software ggf auf VM

Verzechnis erstellen vedor-program-version
Jumpstarter f�r Template ausf�hren aus (Admin) cmd, gut wenn das im Ordner dr�ber liegt
Werte eingeben

Neue Repo Folder: 
Folder aufr�umen, steht in der Readme.md welche, readme auch weg, 
Umgenennen der ci.yml
Sourcen in BLOBs, Versionsnummer in BLOBnamen angeben, da diese im Blobstorage ausserhalb von choco landen
Erzeugen der hash check sum
�ffnenin VS Code, editieren von chocolateyinstall
Anapssen der nuspec datei
Anpassen install script, auch wegen uninstall
Falls notwendig eine post installtion Info mitgeben f�r Inis, Uninstal Files abfragen aus powershell



Test durch eine Batchfile (Felix) zur Sim einer Umgebung

Helferskripte um Uninstall Infos und weiteres zu ziehen (siehe extensions), wird ins choco temp geschoben, weil choco da sucht wenn online nichts gefunden wird




Erg�nzung RJ Docu: 
Beim Packaing:Jumpstarter gibt�s Parameter im Script, die k�nnen in den Befehl reinkommen
VLC zu vlc, weil immer klein
-->