# AzureS2S-AVMFritz-Box7490
Setup script for Azure S2S VPN and config for AVM Fritz!Box 7490

If it breaks stuff or it doesnt work, i take no responsibility. I assume some Azure knowledge to use the details here.

Run the commands from the powershell script one at a time. You will need to install the Azure Powershell extensions beforehand.

In the Fritz!Box 7490 config file edit the lines before uploading it to your VPN settings page on the router:
- replace '123.457.789.00' with your Azure Public IP on your Virtual Network Gateway.
- repalce 'xxxxxxxxxxxxx.myfritz.net' with your DynDNS or MyFritz.NET hostname.
- replace 'yoursecretkey' with the preshared key you used in the Azure local network gateway connection setup.

P.S. Sorry this isnt a work of art, but it worked for me. so thats all that matters.

Also you might need to check your ISP doesnt have a "firewall" enabled by default, you can probably check this on your ISP's website/account page. At the same time make sure "Native 'dual-stack' IPv4 and IPv6 enabled" is NOT configured, and disable IPv6 on your Fritz!Box. This can be enabled if your ISP uses IPv6, you only want an IPv4 address which you will need for the Azure setup. 

Its probably easier if you have a static IP on your ISP which will get around having to update your Azure settings whenever your ISP changes your dynamic IP, you cant use DynDNS in the Azure connection setup (yet). The only way around it is to run a automated update script for your connection. The script 'EndpointLNG-IPUpdate' is what i use in an Automation Powershell Runbook to update my DynDNS IP once per hour. You will need to set your DynDNS name as a variable in the runbook.
