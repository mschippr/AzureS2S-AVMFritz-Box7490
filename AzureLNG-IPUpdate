# get automation variables
$dynamicDnsHostname = Get-AutomationVariable -Name 'dynamicDnsHostname'

$Conn = Get-AutomationConnection -Name AzureRunAsConnection
Add-AzureRMAccount -ServicePrincipal -Tenant $Conn.TenantID `
-ApplicationId $Conn.ApplicationID -CertificateThumbprint $Conn.CertificateThumbprint

# Get IPs
$Uri = 'https://dns.google.com/resolve?name={0}&amp;type=A' -f $dynamicDnsHostname
$currentIp = (Invoke-RestMethod -Uri $URI).Answer.data -replace '^\d+\s'

$lnGw = Get-AzureRmLocalNetworkGateway -ResourceGroupName EastUS_RG -Name EndpointLNG
$lnGwIP = $lnGw.GatewayIpAddress

# compare IPs and update if required
If ($currentIp -ne $lnGwIP) {
  Write-Output "Updating Local Network Gateway IP to $currentIp"
  $lnGw.GatewayIpAddress = $currentIp
  Set-AzureRmLocalNetworkGateway -LocalNetworkGateway $lnGw
}
Else {
  Write-Output 'Local Network GW IP is correct'
}
