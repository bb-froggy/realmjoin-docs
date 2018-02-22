# FAQ

## Which links should I bookmark?
* RealmJoin Admin Console  
  
  <https://realmjoin-web-staging.azurewebsites.net/>  
* RealmJoin Uploader / Package Request  
  
  <https://Realmjoin-uploader.azurewebsites.net>  
* Gitlab Packages  
  
  <https://gitlab.glueckkanja.net/>  
* Documentation  
  
  <https://realmjoin.readthedocs.io/>  

## Am I able to maintain my own packages and updates
Yes. RealmJoin offers packageing-as-a-service but you may also check in ready-to-use packages. In addition it is possible to use additional deployment repositories completely maintained independently. 

## Which platforms are supported?
RealmJoin v4 is only available for Windows 10.

## I do not see my groups in the Admin Console
The sync between Azure AD and RealmJoin is scheduled every 15 minutes and based on your custom pattern ruleset.

## How to enter the *Debug Mode* in RealmJoin client?
Click on the RealmJoin tray icon while pressing STRG and Shift on the Keyboard. For a detailed description of the *debug mode* see chapter *troubleshooting*.

## I accidentally uninstalled software using the Windows Apps control  
Force reinstall by using the *debug mode*.

## Can I get rid of Bloatware using RealmJoin?
TBD
<!--Bloatware: 
Installer von Bloatware uninstaller, nicht einfach, da auch von MS Seite über den Store Software vorinstalliert wird
StandardBloatware, und Hersteller eigene Software, kann schwierig bereinigt werden, ggf neu aufzusetzen
"Win 10 Push Button Reset" soll zu Clean Windows f�hren, dann ist man im OOBE (f�r AAD Join), aber ist noch nicht fix-->

## Is RealmJoin providing an uninstall of software?
A general uninstall feature is currently not implemented. Choco packages provide a generic uninstall component which would be usable for RealmJoin, but because of the volatile history of unattends and the sometimes unpredictable issues with incomplete uninstalls we have decided against using it. 

In real world there are typically three reasons to uninstall software:

* The license should be re-used for a different user. In this case it's easy to just create a package to enable/disable a license for a user.
* The software needs to be removed because of [choose your reason]. In this case a dedicated remove-software-package can be created.
* There is a newer version of the software. This is not a reason to use an uninstall command but instead it is a common practice for every software package used by RealmJoin to 'clean' any precursory binaries or settings.

## Should I use the applications internal auto updater or not?
TBD

## How can I manage the RJ Tenants?
TBD

## Re-Install failed software installations
RealmJoin tries to redo failed installations on the next three logons. If the installations still fails the package is marked as permanent-failed. To reinstall it at a later time use "Retry base installation" in *debug mode*.

## Since the packages are based on open protocols, can others access my packages?
Yes. NuGet and Chocolatey repositories are based on open protocols. Using search commands one is able to find all repositories that are hosted on the GK tenant. Since packages **should not** contain personalized information like licenses or user specific data, there is no potential harm in e.g. installing a Office package with a different companies name in the package description. 
It is in principle possible to host the RealmJoin   

## What Firewall/Proxy settings do I have to configure?
Please check chapter *Technical* section *Requirements* for detailed information on the RealmJoin connections.  

## Does G&K have any recommendations on workflows?  
TBD
<!--
## Who can see my packages  
TBD
Aktuell k�nnen nat�rlich auf "Fremdkunden" Pakete geladen werden, repositories sind global verf�gbar, daher sind die Pakete ohne Security Info; Isolation kommt, ist aber nicht so einfach, da die choco protokolle offen sind, Trennung ist jetzt schon durch eigene Infrastructure m�glich
Realmjoin-uploader.azurewebsites.net  -->