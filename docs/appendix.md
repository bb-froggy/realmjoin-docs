# Appendix
  
## Protocol Handler

It is possible to install RealmJoin packages using an URL-link.  
The correct format for this command consists of the ``realmjoin:`` call, the subcommand ``install`` and the package ID, e.g. ``generic-google-chrome``.  
The complete link therefore would be written as:  
``realmjoin:install:generic-google-chrome``.  
The package has to be assigned for the user in the RealmJoin backend.  

## NoGraph Option

To install RealmJoin without Graph API consent, the registry key 
``
Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\realmjoin\Parameters\NoGraph
``
can be set to `1`.  
It is also possible to set this key during the installation of RealmJoin as a argument for the *msi*:  
``msiexec /i "RealmJoin.msi" NOGRAPH=1``.
