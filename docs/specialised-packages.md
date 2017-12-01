# Specialised Packages

## WLAN packages
Glück&Kanja provides two different approaches to WLAN packages, which allow the configuration of WLAN profiles via RealmJoin.  
Both packages contain a *wifi.xml* file, that can be configured with the assignment arguments in the RealmJoin portal. 
The editing is embedded within a powershell script and the configured *wifi.cml* is added as *wifiCustom.xml* to the device using netsh:  
``netsh wlan add profile filename = "wifiCustom.xml"``. 
Customer-flavoured WLAN packages can be requested from Glück&Kanja.

### WPA2-Enterprise package *AddWlanProfileEnt*
The WPA2-Enterprise package has to be assigned with the parameters:   
* SSID: mandatory  
* Encryption: optional, default value is "AES"

Argumentsynthax:  
``-SSID "xyz" [-Encryption "xyz"]``

### WPA2-PSK package *AddWlanProfilePsk *
The WPA2-PSK package has to be assigned with the parameters:   
* SSID: mandatory  
* PreSharedKey: madatory
* Encryption: optional, default value is "AES"

Argumentsynthax:  
``-SSID "xyz" -PreSharedKey "xyz" [-Encryption "xyz"]``

