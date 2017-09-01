# Managing RealmJoin
Administrative users have access to the RealmJoin administrator console. As RealmJoin is highly compatible with Microsoft Intune and Microsoft Azure, it incorporates the same group based user and policy management experience and uses the Azure AD defined groups as basis for software deployment. The default interval for group synchronization between Azure AD and RealmJoin is 15 minutes, while only groups with a defined prefix are taken into consideration. Only groups with at least one assigned user are syncronized, and the syncronization interval can be adjusted.

## User Client
The RealmJoin client is enrolled on evey Windows 10 device. RealmJoin seamlessly fits into the modern workplace with its focus on user self-service and mobility. Using the RealmJoin client module, the user may install provided software, get basic information on the device and membership in the tenant domain wihout the need of contact an IT administrative. 

### Initial Start
When RealmJoin is enrolled and started for the first time, it asks for the User-Identity and then calls to the cloud Service for a policy.  
   
![RJ AAD Auth](./media/rj-aad-auth.png)

RealmJoin “Security Requirement” assessment does some pre-checks (Encryption, Patch Level, Firewall, Anti-Virus, etc. – this is optional and can be replaced in parts by Intune-Health-Check).  
  
![RJ Sec Check](./media/rj-sec-check.png)
  
If no error ocurs during deployment, RealmJoin is ready to use.

### Client usage
After being successfully installed, RealmJoin is automatically started on the user login and is permanent active in the background. It is represented with an ID card icon. Clicking on the icon opens up the RealmJoin client menu. It contains basic information in the lower and a number of links in the upper part. The selector *Software Packages* opens a second context menu with all the software packages that are allocated to the user.
  
![RJ Tray](./media/rj-tray-menu.png)
  
If a user wishes to install any of the listed software, he/she is only required to select the package to start the installation. 
  
![RJ Add Package](./media/rj-client-addpackage2.png)
  
The installation mode depends on the packages selected: If those are only user mode packages, they are installed immediately. In case of a higher permission level, RealmJoin starts a service (realmjoinservice.exe) and installs the packages with the *SYSTEM* user account.

### Debug Modus
If neccessary, a debug window can be opened by clicking on the RealmJoin icon while pressing Shift+Strg on the keyboard. This reveals a new entry in the context menu listed as *Show Debug Window*. This window offers seven different diagnostic tools. If a device is not able to be addressed by the server or can not connect to the backend, this tool will provide the user with the tools for the first steps of diagnosis. Another new tray menu entry showing up in debug mode is *Retry base installation*, which allows the user to reinstall the RealmJoin client. Additionally, when the client tray menu is opened in debug mode, all packages are shown with the package version number.

![RJ Debug Menu](./media/rj-debug-menu.png)

*Collect Logs* is a quick way to access all log files, which will be saved in a zip-file to the users desktop. See chapter *troubleshooting* for a detailed description of the RealmJoin debug window and its features.

## Admin Console
Device provisioning and RealmJoin configuration is done with the RealmJoin *Admin Console*. Designed to mirror the style of the new Microsoft administration services, it is the main tool for the management of the RealmJoin clients and users. The web application can be reached under <https://realmjoin-web-staging.azurewebsites.net/>.

![RJ Dashboard](./media/rj-ac-dashboard.png)

The dashboard provides a quick and beneficial overview. All sections can be accessed by either clicking on the corresponding number or selecting the section in the toolbar on the left.

### Clients
![RJ clientsicon](./media/rj-ac-clientsicon.png)

The clients tab gives you a transparent overview over all enrolled devices as well as the respective primary user. To enter the devices' states (see section *States*) or associate users, just click on the green numbers on the right. 
 
### Users
![RJ rj-ac-usersicon](./media/rj-ac-usersicon..png)

A list of all users assigned to the tenant. The selectable details on the right include states, group membership, installed software packages, client devices and (to come...) individual settings. Users can't be added or assigned to groups using RealmJoin, the management of users and groups has to be done in Azure AD. 
Selecting a user opens up the users detail page, which contains information gathered by RealmJoin using the Microsoft Graph API.

### User settings
![RJ usersettingsicon](./media/rj-ac-usersettingsicon.png)

<img src="media/rj-ac-usersettingsicon.png"> Configurable group settings and policies. See chapter *Policies* for a list of implemented features.

### Groups
![RJ rj-ac-groupsicon](./media/rj-ac-groupsicon.png)

All in this tenant registered user groups. RealmJoin syncronizes groups from Azure Active Directory into the RealmJoin backend. The details on the right contain users within the individual group, packages that are assigned to a group as well as group settings. Since not all users in Azure AD might be equipped with RealmJoin, only a specified range of groups are transfered into RealmJoin (depending on the group name.....). The groups can not be added or altered within RealmJoin, therefore the group naming conventions have to be established in advance.
   
While there are not strict naming pattern requirements in RealmJoin, we recommend the following convention:
  
```
*APP|CFG-Location-[Vendor-Product-Language-Type-Flavor]*  
```

**Examples:**  
CFG-Global-Core  
CFG-DE-Core  
CFG-DE7499-Core  
APP-Adobe-Photoshop  
APP-Microsoft-Visio  
APP-Mozilla-Firefox  
APP-Mozilla-Firefox-PreRelease  
APP-Mozilla-Firefox-Optional  
APP-Mozilla-Firefox-Optional-PreRelease  
APP-Mozilla-Firefox-x86  
APP-Mozilla-Firefox-x64  
APP-Mozilla-Firefox-DE7499  
APP-Mozilla-Firefox-withFlash  

The synchronization time schedule and the prefixes that are taken into account might be configured from the settings control panel or individually implemented by the developer.

### User settings
![RJ rj-ac-groupsettingsicon](./media/rj-ac-groupsettingsicon.png)

Configurable group settings and policies. See chapter *Policies* for a list of implemented features.

### Software Packages
![RJ rj-ac-packagesicon](./media/rj-ac-packagesicon.png)

A list of all added packages. 
The detail list contains the package version, install order, auto upgradibility and user/group assignment. 

#### Add packages
The administrator is able to add created craft and choco packages to RealmJoin using the *Add Choco* / *Add Craft* buttons. 
This open the package setup window.    
![RJ rj-ac-packages](./media/rj-ac-packages.png)

There are two ways to add the neccessary information: Entering the required fields *Name*, *GroupName*, *Version* and *Package* manually or pasting the JSON code, which can be found in the corresponding package repository (pipeline).
![RJ ac-package-json](./media/rj-ac-package-json.png)
![RJ rj-ac-groupsettingsicon](./media/rj-gitlab-pckg-pipeline.png)

While adding a package the following configuration options are available: 
1. GroupName
  * An optional group name may be entered. This name has no connection to the user groups, instead it will be shown in the RealmJoin client context menu to group the depicted applications.
2. DependsOn
  * The *DependsOn* option is used to indicate if a package needs another package to be installed to work properly. This may be the case for Office user setting packages, that require an office installation upfront. It is possible to hide packages, so that the client context menu only shows one installation option (see section *Package Assignment*). 
     For a working correlation, the correct package name has to be provided. 
     If there is a multiple level-dependency, RealmJoin takes this into consideration. Before the installation process, all dependency-related packages are sorted (also including mandatories) and installed afterwards. 
     RealmJoin takes 1:n dependenciey into account.     
3. Order
  * The order number is an Int32 type figure and provides RealmJoin with a basic structure to determine the package installation sequence. The lower the number the higher the importance, therefore a 10 will be installed before 100. 
    It has to be noted that a 0 is translated to "no sequence given" and the order number is only taken into account at the first roll out.
4. Args
  * If the packaged software has to be installed with arguments. If the package to be deployed is a chocolatey package, make sure to use the prefix *-params* and correct escaping, since chocolatey might mistake the arguments to be directed to it.
    It has to be noted, that it is also possible to provide arguments in the package assignment stage (see section below). Globally relevant parameters (e.g. volume license number) should be provided at the package addition step, while more individualized arguments (e.g. language packs) are better specified during the assignment step.
5. Version
  * Version of the package to be installed (for conventions of the version numbering see chapter *Packages*).
6. Package
  * Exact repository name of the package to be installed. The combination of name and version is used ensure that the correct package is installed. 
7. Availability
  * *Allow Reinstall*: This option allows the client user to reinstall and therefore override their current installation of the package. Useful for information that is taken from Azure or similiar. 
  * *Pre Release*: For testing of a new package, a pre release package is created. The option is chosen, to emphasize, that a test version is deployed. This should not done be using a special version number.
    If two packages have the same ID, but one is a pre release package, the pre release package installed if this option is chosen. 
8. Auto Upgrade
  * The *Auto Upgrade* feature can be enabled to allow applications to use their own internal auto updater. This option should only be activated if trusted, but might prve useful for software, that is continuously extended and update by the manufacturer. 
9. Staggered Deployment
  * It is possible to use staggered deployment and distribute the risk of updating a software if desired. The two parameters needed are the target date and the amount of days over which the update should take place. 
    The clients are not equaly distributed in the deplyoment groups, with fewer deployments in the first part of the timeline and the majority on the last. 
    Deployed package versions for each can be found in the user details of the package or the deployed package details of the users.
    Exsample distribution for n = 10000 and 8 days update time:  
![RJ autoupdate_sim](./media/rj-autoupdate_sim.png)
    
   
#### Assign Packages

Similar to the profile management with Microsoft Azure AD, packages can be assigned to groups and individual users. To assign a package, enter the group or user detail for the package in the package control panel. 
There are four options to override the package configuration when assigning, if in conflict with the package settings, the assignment settings override: 
1. Availabilty
  * Packages can be labeled as *mandatory* to make the software package non-optional.
  * Packages might also be labeled as *hidden*, making them invisible in the RealmJoin client context menu. This might be used for mandatory software or for multiple level dependencies, when the user should only be able to install the highest hierachie and the underlying packages should be installed automatically.  
2. Auto Upgrade
  * In addition to the configuration of the package itself (see section above for the feature description), *auto upgrade* can be enabled for the selected group / user individually. 
3. Staggered Deployment
  * In addition to the configuration of the package itself (see section above for the feature description), *stagered deployment* can be enabled for the selected group / user individually. 
4. Args
  * In addition to the configuration of the package itself (see section above for the feature description), *Args* can be set for the selected group / user individually.  

![RJ rj-ac-packageoverrides](./media/rj-ac-packageoverrides.png)

### States

![RJ rj-ac-statesicon](./media/rj-ac-statesicon.png)

The *states* detail of the client or user control panel provides a list of the devices of the user and how frequent data was upstreamed. 
The *Branch Cache* column indicates, how much this client has contributed to the package distribution over the *Branch Cache* feature (see chapter *Infrastructure*).
Selecting the white arrow in the green circle gives away the complete upstream file.
It contains all the information about the device, OS, Defender Pattern States and installed packages that are transfered to the backend, where some of it is evaluated.  

![RJ rj-ac-states](./media/rj-ac-states.png)

### Settings
#### List of states

##### Information on the Windows Device: 

-  "Type": "win",
-  "ClientID": "ad681fc2-6347-4f72-929d-1c582fb45c13",
-  "VersionTray": "4.8.14+11139.ebe94d4e",
-  "VersionService": "4.8.14+11139.ebe94d4e",
-  "OperatingSystem": 
    * "Name": "Windows 10 Enterprise",
    * "Edition": "Enterprise",
    * "CompositionEdition": "Enterprise",
    * "Version": "10.0.15063.0",
    * "ReleaseID": "1703",
    * "BuildBranch": "rs2_release",
    * "Build": 15063,
    * "BuildRevision": 540,
    * "InstallDate": "2017-07-28T13:08:44Z",
    * "Bits": 64,
    * "Activated": false
-  "MachineName": "MC1",
-  "DomainName": "AzureAD",
-  "JoinedDomainName": null,
-  "HostName": "C1",
-  "Timestamp": "2017-08-18T12:19:35.7293104+00:00",
-  "User": 
   * "LocalName": "User1",
   * "LocalLogonAt": "2017-08-17T10:19:01.8367465+00:00",
   * "IsAdministrator": false
-  "Branchbox": 
   * "Available": [],
   * "Suspended": false
-  "CloudVpn": 
   * "Available": false,
   * "Active": false
-  "Firewall": 
   * "ProfileStates": 
     + "ON",
     + "ON",
     + "ON"
-  "AvProducts": 
   * "Installed": 
       + "Name": "Windows Defender",
       + "State": 397568
-  "Bitlocker": {
   * "DriveStates": 
       * "ComputerName": "C1",
       * "MountPoint": "C:",
       * "EncryptionMethod": 0,
       * "AutoUnlockEnabled": null,
       * "AutoUnlockKeyStored": null,
       * "MetadataVersion": 0,
       * "VolumeStatus": 0,
       * "ProtectionStatus": 0,
       * "LockStatus": 0,
       * "EncryptionPercentage": 0,
       * "WipePercentage": 0,
       * "VolumeType": 0,
       * "CapacityGB": 49.4462852,
       * "KeyProtector": []
- "OsUpdates": 
   * "RefreshTime": "2017-08-17T22:19:41.193123+00:00",
   * "PendingUpdates": 
      * "NoSeverity": 1
-   "BranchCache": 
   * "DataCacheCurrentActiveCacheSize": 0,
   * "CurrentClientMode": "DistributedCache"
   
##### Software:

-  "Chocolatey":
   * "RequiredVersion": "0.10.3",
   * "InstalledVersion": "0.10.3",
   * "Status": "Ready"
 
-  "SoftwarePackages": 
   * "Installed": 
       * "ID": "chocolatey",
          * "Version": "0.10.3",
          * "ArgsHash": null
       *  "ID": "generic-google-chrome",
            * "Version": "59.0.3071.86000",
            * "ArgsHash": null
      
-    "Inventory":    
     *  "Name": "Google Chrome",
            * "Version": "60.0.3112.101",
            * "Publisher": "Google, Inc.",
            * "EstimatedSize": 48768,
            * "UserScope": false
      


## TBD  
Roles and self service in the admin console.
<!-- 
Roles werden noch eingeführt, aktuell nur Admin oder kein Admin
### Increased self service
SelfService im Backend/Admin Console geplant, niedrige Prio -->
