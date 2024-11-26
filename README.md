<h1>DNS Query</h1>
<p1> This tutorial outlines how to query DNS, flush DNS, delete a specific record from the DNS. It also covers how to regenerate DNS records, create DNS “A” record manually, not only but also how to create Reverse lookup zones and PTR records. Lastly, a DNS replication server is installed and configured</p1>

<h3>*Disply DNS</h3>
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

<p>2. 2.Return to the “Windows 10” machine On the command prompt, type <b><i>"ipconfig /registerdns"</i> </b></p>
<p align="center"><img src="https://i.imgur.com/NFieBcE.png" height="50%" width="50%"/>

<p>3. To confirm Windows 10 dns has been registered. go to the “SERVER” machine. On the “DNS Manager”, right click in the open white area and select “Refresh”. If the record does not show up, wait a few minutes and refresh again.</p>
<p align="center"><img src="https://i.imgur.com/4FsfXuZ.png" height="50%" width="50%"/>

<br>
<br>

<h3>*Create DNS “A” record manually </h3>

<p>1. 1.On “DNS manager”, right click the white area and select “New Host (A or AAAA)”.Hostname: Printer1, IP: 192.168.10.210</p>
<p align="center"><img src="https://i.imgur.com/F93Bg6b.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/GT8AXzc.png" height="50%" width="50%"/>
<p align="center"><img src="https://i.imgur.com/EA3jDYX.png" height="50%" width="50%"/>

<p>2. On the Command Prompt of the client VM, ping the hostname Printer1 </p>
<p align="center"><img src="https://i.imgur.com/DderyNV.png" height="50%" width="50%"/>

<h4> Note: You can also use the nslookup tool to query DNS and obtain the mapping between a domain name and its IP address</h4>
<br>
<br>

<h3>*Reverse lookup zones and PTR records</h3>
<p>1. To create a Reverse lookup zones and PTR records; While on the DNS manager page, expand your ADDS-Server, right click on Reverse lookup zones folder from the dropdown and click on new zone.</p>
<p align="center"><img src="https://i.imgur.com/uJielaP.png" height="50%" width="50%"/>

<p>2. </p>



<p align="center"><img src="" height="50%" width="50%"/>
