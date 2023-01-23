---
layout: post
title: Secure Citrix StoreFront IIS Site
image: 
  path: /assets/img/scripts/security_banner.jpg
description: >
  Set the approved File Extensions and Verbs for a Citrix StoreFront deployment.
categories: [StoreFront, Security]
sitemap: true
---

Citrix StoreFront can be hardened and locked to only use specific file extensions and verbs as documented in the Citrix article found [here](https://docs.citrix.com/en-us/storefront/current-release/secure.html). To implement this open up a Command Prompt as an Administrator on your StoreFront servers and copy the below script into the window.  Once run be sure to restart IIS using the following command

```
IISReset
```
## Secure IIS Commands 

```
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" /section:requestfiltering /fileExtensions.allowunlisted:false "/commit:apphost"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" /section:requestfiltering /verbs.allowunlisted:false "/commit:apphost"

%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /fileExtensions.applyToWebDAV:"False"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.appcache',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.aspx',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.cr',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.css',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.dtd',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.gif',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.htm',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.html',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.ica',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.ico',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.jpg',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.js',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.png',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.svg',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.txt',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.xml',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.dmg',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.exe',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.eot',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.ttf',allowed='True']"
%systemroot%\system32\inetsrv\AppCmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"fileExtensions.[fileExtension='.woff',allowed='True']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering "/commit:apphost"

%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" /section:staticContent /-"[fileExtension='.exe',mimeType='application/octet-stream']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" /section:staticContent /-"[fileExtension='.dll',mimeType='application/x-msdownload']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" /section:staticContent /-"[fileExtension='.csh',mimeType='application/x-csh']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" /section:staticContent "/commit:apphost"

%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /verbs.applyToWebDAV:"False"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"verbs.[verb='GET',allowed='True']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"verbs.[verb='POST',allowed='True']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering /+"verbs.[verb='HEAD',allowed='True']"
%systemroot%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:system.webServer/security/requestFiltering "/commit:apphost"
```