Mission 1
  - Determine and document the mail servers for starwars.com using NSLOOKUP.
Non-authoritative answer:
starwars.com	mail exchanger = 5 alt1.aspx.l.google.com.
starwars.com	mail exchanger = 10 aspmx2.googlemail.com.
starwars.com	mail exchanger = 10 aspmx3.googlemail.com.
starwars.com	mail exchanger = 5 alt2.aspmx.l.google.com.
starwars.com	mail exchanger = 1 aspmx.l.google.com.

  - Explain why the Resistance isn't receiving any emails.
The MX record is not set to the correct mail servers

  - Document what a corrected DNS record should be.
Non-authoritative answer:
starwars.com	mail exchanger = asltx.l.google.com.
starwars.com	mail exchanger = asltx.2.google.com.

Mission 2
  - Determine and document the `SPF` for `theforce.net` using NSLOOKUP.
theforce.net	text = "v=spf1 a mx mx:smtp.secureserver.net include:aspmx.googlemail.com ip4:104.156.250.80 ip4:45.63.15.159 ip4:45.63.4.215"

  - Explain why the Force's emails are going to spam.
DNS record have not been updated with the recently changed mail server

  - Document what a corrected DNS record should be.
theforce.net	text = "v=spf1 a mx mx:smtp.secureserver.net include:aspmx.googlemail.com include:45-23-176-21.lightspeed.rcsntx.sbcglobal.net ip4:104.156.250.80 ip4:45.63.15.159 ip4:45.63.4.215"

Mission 3
  - Document how a CNAME should look by viewing the CNAME of `www.theforce.net` using NSLOOKUP.
Non-authoritative answer:
www.theforce.net	canonical name = theforce.net.
  
  - Explain why the sub page of `resistance.theforce.net` isn't redirecting to `theforce.net`.
DNS CNAME record is missing reference for resistance.theforce.net to www.theforce.net
  
  - Document what a corrected DNS record should be.
Non-authoritative answer:
www.theforce.net	canonical name = theforce.net
resistance.theforce.net    canonical name = theforce.net

Mission 4
  - Confirm the DNS records for `princessleia.site`.
Non-authoritative answer:
princessleia.site	nameserver = ns25.domaincontrol.com.
princessleia.site	nameserver = ns26.domaincontrol.com.

  - Document how you would fix the DNS record to prevent this issue from happening again.
princessleia.site	nameserver = ns25.domaincontrol.com.
princessleia.site	nameserver = ns26.domaincontrol.com.
princessleia.site	nameserver = ns2galaxybackup.com.

Mission 5

  - View the [Galaxy Network Map](resources/Galaxy_Network_map.png) and determine the `OSPF` shortest path from `Batuu` to `Jedha`.
D, C, E, F, J, I, L, Q, T, V : 1 ,2 ,1, 1, 1, 1, 6, 4, 2, 2

  - Confirm your path doesn't include `Planet N` in its route.
D, C, E, F, J, I, L, Q, T, V

  - Document this shortest path so it can be used by the Resistance to develop a static route to improve the traffic.
Planet Batuu, Planet D, Planet C, Planet  E, Planet F, Planet J, Planet I, Planet  L, Planet Q, Planet T, Planet V, Planet  Jedha

Mission 6

  - Figure out the Dark Side's secret wireless key by using Aircrack-ng.
KEY FOUND! [ dictionary ]

  - Use the Dark Side's key to decrypt the wireless traffic in Wireshark.
wpa-pwd dictionary:linksys

  - Once you have decrypted the traffic, figure out the following Dark Side information:
IP: 172.16.0.101 - MAC: 00:13:ce:55:98:ef
IP: 172:16:0:1   - MAC: 00:0f:66:e3:e4:01

Mission 7
  - View the DNS record from Mission #4.
nslookup -type=TXT princessleia.site

  - The Resistance provided you with a hidden message in the `TXT` record, with several steps to follow.
Non-authoritative answer:
princessleia.site	text = "Run the following in a command line: telnet towel.blinkenlights.nl or as a backup access in a browser: www.asciimation.co.nz"
  
  - Follow the steps from the `TXT` record.
telnet towel.blinkenlights.nl
  
  - Take a screen shot of the results.
