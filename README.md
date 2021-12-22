# Peer with Kusakabe Si
This page provides the information to get started on peering with the `Kusakabe-Neo` and `KSKB-AS` network

## What is DN42?

[DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) is a big dynamic VPN, which employs Internet technologies (BGP, whois database, DNS, etc) for educational and amateur scientific research purposes. Participants connect to each other using network tunnels (GRE, OpenVPN, Tinc, IPsec, Wireguard) and exchange routes thanks to the BGP. 

Network addresses are assigned in the `172.20.0.0/14` and `10.0.0.0/8` range and private AS numbers are used as well as IPv6 addresses from the ULA-Range (`fd00::/8`) 

[DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) can be used to learn networking and to connect private networks, such as hackerspaces or community networks. But above all, experimenting with routing in [DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) is fun!

## Peering Requests

If you’d like to peer with me, you can...
1. Contact me on telegram https://t.me/KusakabeSi
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

### Supported Tunnel Types

Wireguard only

## Topology

I operates 2 networks `KSKB-AS(AS4242421817)` and `Kusakabe-Neo(AS4201271111)` which uses different architecture and host at different location.  
This two networks are fully isolated except they are peering with eBGP.

![image](https://user-images.githubusercontent.com/73118488/141317915-985c2c12-4cad-4956-a622-67123023de5d.png)

* [Etherguard](https://github.com/KusakabeSi/EtherGuard-VPN)

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
* Multiprotocol BGP: `supported`
* Extended next hop: `supported`

## KSKB-AS (AS4242421817)
* ASN : `AS4242421817`
* Architecture: Normal linux distribution.

Autopeer URL & Lookong Glass     | Location                     | Open Peering | Plan    |Bandwidth|IPv4 |IPv6 |
---------------------------------|------------------------------|--------------|---------|---------|-----|-----|
https://kskb42.pages.dev/tw      | Taiwan                       | O            | My PC   | 100mbps | O[^dynamicip]  | O[^dynamicip]  |
https://kskb42.pages.dev/de      | Germany                      | O            | HZ-FREE | 500mbps | Δ[^limitedport]  | Δ   |
https://noyes42.kskb.eu.org      | United States                | Δ[^noyexix]  | NoyesIX[^noyexix] | 100mbps | X  | O   |

## Kusakabe-Neo (AS4201271111)
* ASN : `AS4201271111`
* ISP: Azure App Service
* **ICMP packets are filtered** by the Azure, **use tcpping** to measure the latency
* Architecture: [RootlessRouter-UML](https://github.com/KusakabeSi/RootlessRouter-UML/)
* Server status: https://42status.kskb.eu.org/

Autopeer URL & Lookong Glass     | Location                     | Open Peering | Plan   |Bandwidth |IPv4 |IPv6 |
---------------------------------|------------------------------|--------------|--------|--------- |-----|-----|
https://dn42jp.azurewebsites.net |Japan Tokyo                   | O            | F1     | 2mbps    | Δ   | X   |
https://dn42ch.azurewebsites.net |Switzerland Zürich            | O            | F1     | 2mbps    | Δ   | X   |
https://dn42ca.azurewebsites.net |Canada Toronto                | O            | F1     | 2mbps    | Δ   | X   |
https://dn42au.azurewebsites.net |Australia Canberra            | O            | F1     | 2mbps    | Δ   | X   |
https://dn42uae.azurewebsites.net|United Arab Emirates Dubai    | O            | F1     | 2mbps    | Δ   | X   |
https://appsg.azurewebsites.net  |Singapore                     | O            | B1     | 100mbps  | Δ   | X   |
https://dn42usw.azurewebsites.net|United States Washington      | O            | F1     | 2mbps    | Δ   | X   |          
https://dn42hk.azurewebsites.net |Hong Kong                     | O            | F1     | 2mbps    | Δ   | X   |          
https://dn42nl.azurewebsites.net |Netherlands                   | O            | F1     | 2mbps    | Δ   | X   |               

### Route Propagation Graph for KSKB-AS (AS4242421817)
[![RPG1817](https://bgp-api.strexp.net/as_graph/AS4242421817)](https://bgp42.strexp.net/asInfo/4242421817)

### Route Propagation Graph for Kusakabe-Neo (AS4201271111)
[![RPG1111](https://bgp-api.strexp.net/as_graph/AS4201271111)](https://bgp42.strexp.net/asInfo/4201271111)

## Dynamic IP

This is an example crontab which cam resolve the ip periodically to prevent lost connection after dynamic chabged.
```
*/10 * * * * wg set dn42-kskb peer "{wireguard public key}" endpoint "{peer wg endpoint}"
```

[^dynamicip]: Dynamic IP on my side, please set a cronjob to prevent lost connection after my IP chabged.
[^limitedport]: Only 9 external port available in my side, contact me if you don't have external port
[^noyexix]: Peering via IX only, please join [NoiesIX](https://piao.nicholas.wang/) to peer with me!
