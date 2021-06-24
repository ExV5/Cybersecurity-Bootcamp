1. Command used: fping 15.199.95.91 15.199.94.91 11.199.158.91 167.172.144.11 11.199.141.91
   Potential vulnerability with IP 167.172.144.11
   
   167.172.144.11 is alive
   15.199.95.91 is unreachable
   15.199.94.91 is unreachable
   11.199.158.91 is unreachable
   11.199.141.91 is unreachable
   OSI Layer 3 "Network"
   
2. nmap -sS 167.172.144.11
   vulnerability that can allow people to SSH into system with credentials are known.
   
   Port 22/tcp is open.
   OSI Layer 4 "Transport"
   
3. ssh jimi@167.172.144.11
   cd etc
   cat hosts
   hacker is redirecting traffic to rollingstone.com to a different IP address
   
   98.137.246.8 rollingstone.com
   nslookup 98.137.246.8
   8.246.137.98.in-addr.arpa	name = unknown.yahoo.com.
   Using google the provided hostname is media-router-fp72.prod.media.vip.gq1.yahoo.com
   OSI Layer 7 "Application"
   
4. Potential "ARP poisoning attack" to steal traffic but using a malicious server
   
   [Duplicate IP address detected for 192.168.47.200 (00:0c:29:1d:b3:b1) - also in use by 00:0c:29:0f:71:a3 (frame 4)]
    [Frame showing earlier use of IP address: 4]
    [Seconds since earlier frame seen: 10]

   E-mail send asking for 1 million dollars to provide username and password since post 22 has been left open.
   
   HTML Form URL Encoded: application/x-www-form-urlencoded
    Form item: "0<text>" = "Mr Hacker"
    Form item: "0<label>" = "Name"
    Form item: "1<text>" = "Hacker@rockstarcorp.com"
    Form item: "1<label>" = "Email"
    Form item: "2<text>" = ""
    Form item: "2<label>" = "Phone"
    Form item: "3<textarea>" = "Hi Got The Blues Corp!  This is a hacker that works at Rock Star Corp.  Rock Star has left port 22, SSH open if you want to hack in.  For 1 Milliion Dollars I will provide you the user and password!"
    Form item: "3<label>" = "Message"
    Form item: "redirect" = "http://www.gottheblues.yolasite.com/contact-us.php?formI660593e583e747f1a91a77ad0d3195e3Posted=true"
    Form item: "locale" = "en"
    Form item: "redirect_fail" = "http://www.gottheblues.yolasite.com/contact-us.php?formI660593e583e747f1a91a77ad0d3195e3Posted=false"
    Form item: "form_name" = ""
    Form item: "site_name" = "GottheBlues"
    Form item: "wl_site" = "0"
    Form item: "destination" = "DQvFymnIKN6oNo284nIPnKyVFSVKDX7O5wpnyGVYZ_YSkg==:3gjpzwPaByJLFcA2ouelFsQG6ZzGkhh31_Gl2mb5PGk="
    Form item: "g-recaptcha-response" = "03AOLTBLQA9oZg2Lh3adsE0c7OrYkMw1hwPof8xGnYIsZh8cz5TtLwl8uDMZuVOls6duzyYq2MTzsVHYzKda77dqzzNUwpa6F5Tu6b9875yKU1wZHpfOQmV8D7OTcx2rnGD6I8s-6qvyDAjCuS6vA78-iNLNUtWZXFJwleNj3hPquVMu-yzcSOX60Y-deZC8zXn8hu4c6u
	OSI Layer 2 "Data Link"
