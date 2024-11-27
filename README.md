<h1>DNS Query</h1>
<p1> This tutorial outlines how to query DNS, flush DNS, delete a specific record from the DNS. It also covers how to regenerate DNS records, create DNS “A” record manually, not only but also how to create Reverse lookup zones and PTR records. Lastly, a DNS replication server is installed and configured</p1>

<h3>*Display DNS</h3>
<p>To view the DNS cache on your computer, open PowerShell on your local computer and enter the following command: <b><I>"ipconfig /displaydns</I></b>"</p>
<p align="center"><img src="https://i.imgur.com/uiBKyqh.png" height="50%" width="50%"/>

<h3>*Flush DNS</h3>
<p> Sometimes, accessing a website issues can be resolved by clearing the DNS cache. To do this, enter the command: <b><I>"ipconfig /flushdns"</I></b></p>
<p align="center"><img src="https://i.imgur.com/Jtg244p.png" height="50%" width="50%"/>

<h3>*How to clear a specific record from the cache using PowerShell</h3>
<p>1. Using command prompt <b><i>“Get-DnsServerResourceRecord -ZoneName “Adeniyi.com”</i></b> on the server to pull the resource records. </p>
<p align="center"><img src="https://i.imgur.com/nxvBOAB.png" height="50%" width="50%"/>

<p>2. For this purpose, I will be deleting the “Zino” record. Using the command prompt <b> <i>“Remove-DnsServerResourceRecord -ZoneName “adeniyi.com” -RRType “A” -Name “Zino” -RecordData “192.168.10.218”</i></b><p>
<p align="center"><img src="https://i.imgur.com/en9NinL.png" height="50%" width="50%"/>

<p>3. Using  <b><i>“Get-DnsServerResourceRecord -ZoneName “Adeniyi.com”</i></b> command to view the resource record again to confirm</p>
<p align="center"><img src="https://i.imgur.com/L1ZOOyL.png" height="50%" width="50%"/>
  
<p>4. In addition, I also used the <b><i>"Nslookup Zino"</i></b> Command to check the record we removed from the DNS server</p>
<p align="center"><img src="https://i.imgur.com/AwkaC6j.png" height="50%" width="50%"/>

<br>
<br>

<h1>DNS Records</h1>
<h3>*Re-generate DNS record</h3>

<p>1. On the Server open “DNS Manager”, delete Windows 10 Client machine DNS record </p>
<p align="center"><img src="https://i.imgur.com/vt1dmYb.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/HSUNOh1.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/odSkXmI.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/qWd0lqQ.png" height="50%" width="50%"/>

<p>2. Return to the “Windows 10” machine On the command prompt, type <b><i>"ipconfig /registerdns"</i> </b></p>
<p align="center"><img src="https://i.imgur.com/NFieBcE.png" height="50%" width="50%"/>

<p>3. To confirm Windows 10 dns has been registered. go to the “SERVER” machine. On the “DNS Manager”, right click in the open white area and select “Refresh”. If the record does not show up, wait a few minutes and refresh again.</p>
<p align="center"><img src="https://i.imgur.com/4FsfXuZ.png" height="50%" width="50%"/>

<br>
<br>

<h3>*Create DNS “A” record manually </h3>

<p>1. On “DNS manager”, right click the white area and select “New Host (A or AAAA)”.Hostname: Printer1, IP: 192.168.10.210</p>
<p align="center"><img src="https://i.imgur.com/F93Bg6b.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/GT8AXzc.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/EA3jDYX.png" height="50%" width="50%"/>

<p>2. Open windows powershell on the client VM, ping the hostname Printer1 </p>
<p align="center"><img src="https://i.imgur.com/DderyNV.png" height="50%" width="50%"/>

<h4> Note: You can also use the nslookup tool to query DNS and obtain the mapping between a domain name and its IP address</h4>
<br>
<br>

<h3>*Reverse lookup zones and PTR records</h3>
<p>A reverse lookup zone is a DNS zone that resolves IP addresses to domain names, while PTR(Pointer) records within this zone are used to perform the reverse lookup by pointing an IP address to its associated domain name.</p>

<p>1. <b>To create a Reverse lookup zone</b>; While on the DNS manager page, expand your ADDS-Server, right click on Reverse lookup zones folder from the dropdown and click on new zone.</p>
<p align="center"><img src="https://i.imgur.com/uJielaP.png" height="50%" width="50%"/>

<p>2. The New Zone Wizard opens, click NEXT</p>
<p align="center"><img src="https://i.imgur.com/elausoD.png" height="50%" width="50%"/>

<p>3. You are asked select a Zone type, leave it on Primary zone and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/cbRTi11.png" height="50%" width="50%"/>

<p>4. On the Active Directory Zone Replication Scope screen, select “To all DNS Servers running on domain controller in the domain:adeniyi.com”, then click NEXT</p>
<p align="center"><img src="https://i.imgur.com/OUj4m5o.png" height="50%" width="50%"/>

<p>5. On the Reverse lookup zone screen, select Ipv4 Reverse lookup zone , then click NEXT</p>
<p align="center"><img src="https://i.imgur.com/2MQRTiV.png" height="50%" width="50%"/>

<p>6. On the next page, you are prompted for the Network ID, input this and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/gDOpIFO.png" height="50%" width="50%"/>

<p>7. On the Dynamic Update page, select “To allow only secure dynamic update(recommended for Active Directory)" and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/u3qABLT.png" height="50%" width="50%"/>

<p>8. On the completing the new zone wizard page, review what you created , then click FINISH.</p>
<p align="center"><img src="https://i.imgur.com/pO4lkak.png" height="50%" width="50%"/>


<p>1. <b> To create a PTR Record</b>, while still on the DNS manager page, expand the reverse lookup zones folder, right-click, then select New pointer(PTR). Next input the IP address of the Host IP and the Host name, then click OK</p>
<p align="center"><img src="https://i.imgur.com/Re0KR6u.png" height="50%" width="50%"/>

<p>2. Back on the Reverse lookup zones folder, you can see the PTR record we just created.</p>
<p align="center"><img src="https://i.imgur.com/MREIYXx.png" height="50%" width="50%"/>

<p>3. Open windows powershell and use the nslookup command with the PTR record IP address to confirm.</p>
<p align="center"><img src="https://i.imgur.com/VmmygED.png" height="50%" width="50%"/>

<br>
<br>

<h3>*DNS replication </h3>
<p>DNS replication is the process of copying DNS records from one DNS server to another to ensure consistency and availability of domain name information across multiple servers.</p>
<p>1. First we need to make sure the new server(proposed for DNS replication) is joined to the Domain Server which the DNS server is on. Then install DNS on the newly joined server. I installed DNS using Windows Powershell command; <b><i>“Install-WindowsFeature-Name DNS -IncludeManagementTools"</i></b> </p>
<p align="center"><img src="https://i.imgur.com/NDtzqtV.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/QNfOBrg.png" height="50%" width="50%"/>

<p>2. To Confirm - Go to server manager dashboard, click on Tools and scroll to see that the DNS has been installed</p>
<p align="center"><img src="https://i.imgur.com/xHuhBYT.png" height="50%" width="50%"/>

<h3>*Configure DNS Replication (Secondary DNS)</h3>
<p>1. To configure DNS Replication(Secondary DNS), first we need to allow zone transfers from the main DNS server; From ADDS server manager-dashboard, go to DNS</p>
<p align="center"><img src="https://i.imgur.com/4Xyiky5.png" height="50%" width="50%"/>

<p>2. From the DNS manager, expand ADDS-Server, then under the Forward lookup zones folder, right click on the domain and click on properties.</p>
<p align="center"><img src="https://i.imgur.com/8Nq8VUP.png" height="50%" width="50%"/>

<p>3. From the properties’ page, click on zone transfers, select the “Allow zone transfers” checkbox, then click Apply and click OK</p>
<p align="center"><img src="https://i.imgur.com/MGc51qJ.png" height="50%" width="50%"/>

<P><b>Return to the new Server</b></P>
<br>
<p>1. On the “Server Manager – Dashboard”, navigate to “Tools > DNS”.</p>
<p align="center"><img src="https://i.imgur.com/CH40Dtj.png" height="50%" width="50%"/>

<p>2. Right click on the server and select New zone</p>
<p align="center"><img src="https://i.imgur.com/sdrMaQj.png" height="50%" width="50%"/>

<p>3. The New Zone Wizard opens, click NEXT</p>
<p align="center"><img src="https://i.imgur.com/qlr1Lhi.png" height="50%" width="50%"/>

<p>4. You are asked select a Zone type, select Secondary zone and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/J4N0672.png" height="50%" width="50%"/>

<p>5. On the Forward or Reverse Lookup zones page, click on Forward lookup zone and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/cbzf6UA.png" height="50%" width="50%"/>

<p>6. On the Zone name page, type in the domain name then click NEXT</p>
<p align="center"><img src="https://i.imgur.com/oMn67aj.png" height="50%" width="50%"/>

<p>7. On the Master DNS Servers’ page, in the space to add IP address, type in the ADDS Server’s IP address and hit ENTER</p>
<p align="center"><img src="https://i.imgur.com/4mMk3lb.png" height="50%" width="50%"/>

<p>8. On the Completing the New Zone Wizard page, review the information and click FINISH</p>
<p align="center"><img src="https://i.imgur.com/MSQ7O5m.png" height="50%" width="50%"/>

<p>9. Back on the member server’s DNS manager, you can refresh for the information on the primary zone to show up.</p>
<p align="center"><img src="https://i.imgur.com/lLWMiOF.png" height="50%" width="50%"/>

<br>
<br>
