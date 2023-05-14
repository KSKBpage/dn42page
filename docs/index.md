# Peer with Kusakabe Shi
This page provides the information to get started on peering with the `KSKB-NETWORK` and `Kusakabe-Neo`  network

I operates 2 networks `KSKB-NETWORK(AS4242421817)` and `Kusakabe-Neo(AS4201271111)`  
They are fully isolated except peering with eBGP to help me experiment different things.  
For example, they use different architecture and different routing policy.  
I use two ASN for them for batter isolation, welcome to peer with **both** my network!  

## What is DN42?

[DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) is a big dynamic VPN, which employs Internet technologies (BGP, whois database, DNS, etc) for educational and amateur scientific research purposes. Participants connect to each other using network tunnels (GRE, OpenVPN, Tinc, IPsec, Wireguard) and exchange routes thanks to the BGP. 

Network addresses are assigned in the `172.20.0.0/14` and `10.0.0.0/8` range and private AS numbers are used as well as IPv6 addresses from the ULA-Range (`fd00::/8`) 

[DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) can be used to learn networking and to connect private networks, such as hackerspaces or community networks. But above all, experimenting with routing in [DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) is fun!

## Peering Requests

If you’d like to peer with me, you can...

1. Contact me on telegram https://t.me/KusakabeShi
2. Contact me on irc nickname `kskb`
3. Contact me via email `dn42@kskb.eu.org`
4. Use AutoPeer service listed below

### Peering Requirements
To peer with me, you must meet the following requirements:

1. Latency to my node <= 100 ms
1. You must implement ROA checks
2. Contact information in the registry must always be up to date and admins must respond when contacted

There are 2 **additional requirement** for `Kusakabe-Neo(AS4201271111)`

1. You must have a public IPv4 endpoint on your side.
2. You must have at least two peerings already established with other DN42 networks


## Symbol

Generally, the symbol means: 

Symbol  | Means             
--------|----------
O| positive  
Δ| partially positive  
X| negative  

In the IP section

Symbol  | Means             
--------|----------
O| This node have public IP. <br>You can peer with this node even if you are behind NAT.
Δ| This node doesn't have public IP, it's behind NAT.<br>You have to provide your endpoint
X| Not accessable

## BGP support
Peer with Multiprotocol BGP and Extended next hop over IPv6 link local address is preffered

* Multiprotocol BGP: `supported and preferred`
* Extended next hop: `supported and preferred`

## KSKB-NETWORK (AS4242421817)
* ASN : `AS4242421817`
* Routing policy: Cold-potato Routing
* Architecture: Normal linux distribution.
* Supported Tunnel Types
  * Wireguard
  * OpenVPN
* Topology:
  * ![image](https://user-images.githubusercontent.com/73118488/177179872-593e59b7-1ebb-459b-a6d4-2c448e431cbb.png) 

Autopeer URL & Lookong Glass                          |Open Peering| Hosting                                    |Bandwidth|IPv4            |IPv6            |
------------------------------------------------------|------------|--------------------------------------------|---------|----------------|----------------|
[Taiwan](info/#taiwan)                                | O          | PC at my home                              | 250Mbps | O[^dynamicip]  | O[^dynamicip]  |
[Japan](info/#japan)                                  | O          | [CNTUG Infra Labs](https://cloudnative.tw/)| 1Gbps   | O              | O              |
[Hong Kong](info/#hong-kong)                          | O          | Licson's Machine                           | 1Gbps   | O              | O              |
[Singapore](info/#singapore)                          | O          | Oracle Cloud                               | 500Mbps | O              | O              |
[Germany](info/#germany)                              | O          | HTTPX's Machine                            | 1Gbps   | O              | O              |
[Netherlands](info/#netherlands)                      | O          | Zero IX                                    | 1Gbps   | O              | O              |
[United States Fremont](info/#united-states-fremont)  | O          | [Skywolf Cloud](https://skywolf.cloud/)    | 1Gbps   | O              | O              |
[China Changsha](info/#china-changsha)                | Δ (Manual) | MQ's Machine                               | 100Mbps | O              | X              |
[China Beijing](info/#china-beijing)                  | Δ (Manual) | Lama's Machine                             | 40Mbps  | O              | X              |


### Route Propagation Graph for KSKB-Network (AS4242421817)
[![RPG1817](https://dn42.tools/pathimg/rt-fd28:cb8f:4c92::_48)](https://dn42.tools/as/4242421817#connectivity)

## Kusakabe-Neo (AS4201271111)
* ASN : `AS4201271111`
* Routing policy: Hot-potato Routing
* ISP: Azure App Service
* **ICMP packets are filtered** by the Azure, **use tcpping** to measure the latency
* Architecture: [RootlessRouter-UML](https://github.com/KusakabeSi/RootlessRouter-UML/)
* Server status: https://42status.kskb.eu.org/
* Supported Tunnel Types
  * Wireguard
* Topology:
  * ![image](https://user-images.githubusercontent.com/73118488/158076242-0bbfaea6-b71e-4deb-a4d4-e92662ac4541.png)
  * [Etherguard](https://github.com/KusakabeSi/EtherGuard-VPN)

Autopeer URL & Lookong Glass     | Location                     | Open Peering | Plan   |Bandwidth |IPv4 |IPv6 |
---------------------------------|------------------------------|--------------|--------|--------- |-----|-----|
https://dn42hk.azurewebsites.net |Hong Kong                     | O            | F1     | 2mbps    | Δ   | X   |      
https://dn42jp.azurewebsites.net |Japan Tokyo                   | O            | F1     | 2mbps    | Δ   | X   |
https://dn42sg.azurewebsites.net  |Singapore                     | O            | F1     | 2mbps  | Δ   | X   |
https://appusw.azurewebsites.net|United States Washington      | O            | B1     | 2mbps    | Δ   | X   |
https://dn42ca.azurewebsites.net |Canada Toronto                | O            | F1     | 2mbps    | Δ   | X   |
https://dn42ch.azurewebsites.net |Switzerland Zürich            | O            | F1     | 2mbps    | Δ   | X   |
https://dn42nl.azurewebsites.net |Netherlands                   | O            | F1     | 2mbps    | Δ   | X   |       
https://dn42au.azurewebsites.net |Australia Canberra            | O            | F1     | 2mbps    | Δ   | X   |
https://dn42uae.azurewebsites.net|United Arab Emirates Dubai    | O            | F1     | 2mbps    | Δ   | X   |

### Route Propagation Graph for Kusakabe-Neo (AS4201271111)
[![RPG1111](https://dn42.tools/pathimg/rt-fd10:127:e00f:aca::_64)](https://dn42.tools/as/4201271111#connectivity)

## Dynamic IP

This is an example crontab which cam resolve the ip periodically to prevent lost connection after my IP dynamic changed.
```
* * * * * wg set dn42-kskb peer "{peer public key}" endpoint "{peer wg endpoint}"
```

[^dynamicip]: Dynamic IP on my side, please set a cronjob to prevent lost connection after my IP changed.  
[^limitedport]: Only 9 external port available in my side, contact me if you don't have external port
