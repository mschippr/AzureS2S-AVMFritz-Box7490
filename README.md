# AzureS2S-AVMFritz-Box7490
Setup script for Azure S2S VPN and config for AVM Fritz!Box 7490

If it breaks stuff or it doesnt work, i take no responsibility.

Run the commands from the powershell script one at a time. You will need to install the Azure Powershell extensions beforehand.

P.S. Sorry this isnt a work of art, but it worked for me. so thats all that matters.

Also you might need to check your ISP doesnt have a "firewall" enabled by default, you can probably check this on your ISP's website/account page. At the same time make sure "Native 'dual-stack' IPv4 and IPv6 enabled" is NOT configured, and disable IPv6 on your Fritz!Box. This can be enabled if your ISP uses IPv6, you only want an IPv4 address which you will need for the Azure setup. Its probably easier if you have a static IP on your ISP which will get around having to update your Azure settings whenever your ISP changes your dynamic IP, you cant use DynDNS in the Azure connection setup (yet). If you find a way let me know.
