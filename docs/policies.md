# Settings and Policies

After installing the RealmJoin client on the device, a configuration is saved locally. This configuration is encrypted and can not be modified by the user. RealmJoin compares the hash value of the local configuration  to the hash value of the configuration for this user on the backend. If the hash deviats, the confifguration is re-synced from the server to the local device. The configuration is signed with the servers public key, therefore the local RealmJoin client can validate the configuration. 

## Delivery Optimization for Windows Update

*Windows Update Delivery Optimization*, or *WUDO* is a self organised solution for distributed caches for Windows Updates. In default mode, WUDO identifies peers as part of a WAN based on their external IP. In case of streched out WANs with just one breakout point, this leads to a high network load and a bottleneck. 
To improve the handling, Microsoft Intune can be used to set WUDO to *download mode 2*, where peers are grouped by a groupID. The ID (GUID) is set for each device using network fingerprinting and the MAC address of the default gateway and therefore creating a more localized group. RealmJoin is used to set the groupID for each client.

The following registry key is set to define the DOGroupID:  
  
**Network-Fingerprint-GUID in Reg-Key**
```
HKLM\SOFTWARE\Policies\Microsoft\Windows\DeliveryOptimization\DOGroupId
```
Remember to set the Download Mode to Group via Windows Update settings in Intune:
```
Delivery optimization download mode: HTTP blended with peering across private group
```
This is effectively DownloadMode=2.
  
For a more on WUDO see the [Microsoft WUDO documentation (DE)](https://docs.microsoft.com/de-de/windows/deployment/update/waas-delivery-optimization).

## Bitlocker
### Bitlocker enforcement

It is possible to force Bitlocker encryption for OS volumes. The configuration file (see chapter *Policies*) allows to set the switch *BitlockerEnabled* to true. If the device is equipped with a *ready state* TPM chip the encryption is activated. To allow the Bitlocker enforcement, the registry key ```HKLM\SYSTEM\CurrentControlSet\Control\BitLocker:PreventDeviceEncryption``` is set to false. 
For virtual machines the encryption is only enforced, if the virtual machine variable ```$env:RjDisableVmDetection=1``` is set. 

### Bitlocker recovery key
If the client device is Azure AD joined, RealmJoin uploads the Bitlocker recovery key to Azure AD. If the upload is not successfull in the first try, it will be retried. If the upload can not be performed successfully, the RealmJoin rollout failed. 
In case of a *not-AAD-joined* device, the Bitlocker recovery key is not secured. 

## Domain Passwort expiry
RealmJoin uses the Azure AD attribute ```msDS-UserPasswordExpiryTimeComputed``` to check if the user passwort is expired. 

## Other Configuration Settings

- "Environment"
  * "UpdateCheckInterval": "01:00"
  * "ConfigCheckInterval": "00:30"
    + Set as "hh:mm"
    
- "FirstRun"
  * "EnableSecureDesktop": true
    + Enable the Windows *secure desktop* feature
    
- "Realm"
  * "Domain": "glueckkanja.net"
  *   "NetBIOS": "GLUECKKANJA"
    + Connection data to the backend
    
-  "DomainConnect"
  *   "Domain": "glueckkanja.net",
  *   "NetBIOS": "GLUECKKANJA",
  *   "CredentialName": "RealmJoin (master)",
  *   "CheckInterval": "01:00"
  
 - "CredentialManager":
    + Allows to configure WAN/LAN connections and manage authentication
  * "Type": "wlan",
    *   "Target": "GKEnterprise",
    *   "CredentialName": "RealmJoin (master)"
  * "Type": "ntlm",
    *   "Target": "identity.glueckkanja.net"
  * "Type": "smb",
     *   "Target": "files.glueckkanja.net",
     *   "Share": "Filestore"
      
-    "IpSec": 
   *   "Rules":
       *   "Name": "Domain Controller - glueckkanja.net",
       *   "Targets": "glueckkanja.net",
       *   "Protocol": "tcp",
       *   "Range": "135,389,445,30000-30400",
       *   "RangeOSX": "135,389,445",
       *   "Key": "xxxxxxxxxxxxxxxxxxxxx"
       
 -    "Branchbox": 
   *    "RescanInterval": "00:15",
          
   *   "Rules": 
       * "Name": "Branchbox",
       *   "Target": "files.glueckkanja.net",
       *   "IPs": "172.27.0.20",
       *   "CheckPort": 63069,
       *   "CN": "*.glueckkanja.net"
         
-    "CloudVPN": 
   *    "Gateway": "cloudvpn.gkdatacenter.net",
   *   "Username": "",
   *    "Password": ""
    
-    "WebLinks": 
   *     "Name": "GK Help",
   *     "Target": "https://help.glueckkanja.net/",
   *    "Platform": "any"
   
-   "BranchCache": 
   *     "Mode": "Distributed"
   
- "Chocolatey": 
   *     "Version": "0.10.3",
   
   *     "Sources": 
   *       "Name": "gkpackages",
   *       "Source": "https://packages.gkdatacenter.net/nuget",
   *       "User": "packages",
   *       "Password": "xxxxxxxxxxxxxxxxxxxxx",
   *       "Priority": 10
     
-    "SoftwarePackages": 
   *    "Package": "bcurl",
   *    "ID": "bcurl",
   *    "Platform": "winchoco",
   *     "Version": "1.0.11",
   *     "Args": "",
   *     "Name": "BcUrl",
   *     "Order": 500,
   *     "PreRelease": false,
   *     "AllowReinstall": false,
   *     "DependsOn": [],
   *     "AutoUpgrade": true,
   *     "AutoUpgradeStaggered": "",
   *     "GroupName": "Development",
   *     "Hidden": false,
   *     "Mandatory": false

-   "Location": "https://packages.gkdatacenter.net/blobs/glueckkanja/glueckkanja-core-settings-wlan-gkenterprise/glueckkanja-core-settings-wlan-gkenterprise-v1.0.0.0.zip",
  *      "Hash": "46298d7dfe399cc46bd62ee359ab983771f5bcf1",
  *      "Scope": "user",
  *      "ID": "glueckkanja-core-settings-wlan-gkenterprise",
  *      "Platform": "win",
  *      "Version": "1.0.0.0",
  *      "Args": "",
  *      "Name": "GK WLAN (GKEnterprise)",
  *      "Order": 999999,
  *      "PreRelease": false,
  *      "AllowReinstall": false,
  *      "DependsOn": [],
  *      "AutoUpgrade": true,
  *      "AutoUpgradeStaggered": "",
  *      "GroupName": "Glueckkanja",
  *      "Hidden": false,
  *      "Mandatory": false

### Policies  

-    "Policies": 
  *      "SMimeEnabled": false,
  *      "OsActivationEnabled": false,
  *      "SetTimeserver": ["time.windows.com", "time.apple.com"],
  *      "TrustedSites": ["file://glueckkanja.net", "https://glueckkanja.net", "https://guk.sharepoint.com", "https://guk-my.sharepoint.com"],
  
  *     "RequireSecurityFeatures": 
    *          "WinVersion": "Win7",
    *          "BitlockerEnabled": null,
        + If set to "true", Bitlocker will be enforced if the device has a TPM. 
        + The following key value is changed to allow Bitlocker force: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\BitLocker; Value: PreventDeviceEncryption set to null/false
        + The Bitlocker key is synced to AAD if the client is AAD joined, otherwise, no backup will be made.
    *          "FirewallEnabled": true,
    *          "AvEnabled": null,
    *          "EnvironmentCheck": null
       
  *      "AwsAccess": 
    *          "AccessKey": "AKIAIHFASK3VCX4EWCAA",
    *          "SecretKey": "xxxxxxxxxxxxxxxxxxxxx"
      
  *     "DisableExplorerLibraries": true,
  
  *     "Rms": 
    *         "Enabled": null,
    *         "Hostname": "12323815-123c-123a-1230-123aab12ba3a.rms.eu.aadrm.com"
        
  *     "OneDrive": 
    *         "Enabled": false,
    *         "DisplayName": "OneDrive Business",
    *         "FolderRedirection": false,
    *         "DisableOneDrivePersonal": false,
    *         "DisableStartupShortcut": false
     
   *     "Office":
     *         "NoDomainKey": false,
     *         "SetGenericCredentials": false,
     *         "SetLyncUsername": false
        
### Client

 - "Client": 
  *      "IsPrimaryOfUser": true
          + Autogenerated by the server
          
The *IsPrimaryOfUser* attribute is set when the RealmJoin client on the device contacts the backend for the first time. The user who is signed on during this process is registered as primary user of the device. 
Mandatory packages will only be installed when the primary user is logged in. If the *makeAdmin* property is set in the user/group settings, the primary user is promoted to administrator. 
It is possibly to manually set another user to the primary of the device. If a device is decomissioned and given another user without changing the primary, the old primary user might persist in the backend.

### Signatures  
RealmJoin provides Outlook with signature files. Those files can be found in:  
* %userprofile%\AppData\Roaming\Microsoft\Signatures
    * .\anyname.txt
    * .\anyname.htm

The following fields for signatures are extracted from the Microsoft Graph API and may be used: 

```
Graph_User_BusinessPhone
Graph_User_City
Graph_User_CompanyName
Graph_User_Country
Graph_User_Department
Graph_User_DisplayName
Graph_User_GivenName
Graph_User_Id
Graph_User_JobTitle
Graph_User_Mail
Graph_User_MobilePhone
Graph_User_OfficeLocation
Graph_User_PostalCode
Graph_User_State
Graph_User_StreetAddress
Graph_User_Surname
```
