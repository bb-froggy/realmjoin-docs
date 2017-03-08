# Network Requiremens

## No-Proxy

Initial deployment needs direct internet access. No proxy would be ideal, a transparent proxy should be ok (if really transparent). If there is a proxy unavoidable as a minimum requirement the following services/addresses need to be directly accessible (not recommended, list might not be exhaustive):  
  
* Azure
* Office 365
* Windows Update
  
For a list of the corresponding IP ranges please see 

**Microsoft Azure Datacenter IP Ranges:** https://www.microsoft.com/en-us/download/details.aspx?id=41653  
  
This file contains the compute IP address ranges (including SQL ranges) used by the Microsoft Azure Datacenters. A new xml file will be uploaded every Wednesday (Pacific Time) with the new planned IP address ranges. New IP address ranges will be effective on the following Monday (Pacific Time). Please download the new xml file and perform the necessary changes on your site before Monday.
  
**Office 365 URLs and IP address ranges:** https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2  
  
**WARNING:** IP addresses filtering alone isn’t a complete solution due to dependencies on internet based services such as Domain Name Services, Content Delivery Networks (CDNs), Certificate Revocation Lists, and other third party or dynamic services. These dependencies include dependencies on other Microsoft services such as the Azure Content Delivery Network and will result in network traces or firewall logs indicating connections to IP addresses owned by third parties or Microsoft but not listed on this page. These unlisted IP addresses, whether from third party or Microsoft owned CDN and DNS services are dynamically assigned and can change at any time.  

## No VLans / No WLAN-Isolation / No Port-Isolation
  
For BranchCache to be effective the clients need to be able to communicate directly with each other. So they shouldn't be separated by different VLans, WLAN-Isolation or Port-Isolation. For mass rollouts "BranchCache Servers" with pre-populated caches are recommended. BranchCache is limited to a single subnet, if a site has multiple subnets the "BranchCache Servers" must be placed in the same subnet as the clients to be effective.  
