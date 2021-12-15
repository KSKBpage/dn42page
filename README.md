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

## KSKB-AS (AS4242421817)

* ASN : `AS4242421817`
* Multiprotocol BGP: `supported`
* Extended next hop: `supported`
* Architecture: Normal linux distribution.

Autopeer URL & Lookong Glass     | Location                     | Accept New Peer   | Plan    |Bandwidth|Public IP  | SLA   |
---------------------------------|------------------------------|-------------------|---------|---------|-----------|-------|
https://dn42tw.pages.dev         | Taiwan                       | O                 | My PC   | 100mbps |Δ (dynamic)| No    |

### Route Propagation Graph
[![RPG1817](https://bgp-api.strexp.net/as_graph/AS4242421817)](https://bgp42.strexp.net/asInfo/4242421817)

## Kusakabe-Neo (AS4201271111)
* ASN : `AS4201271111`
* **Host in Azure app service, no exposed ports**
* Multiprotocol BGP: `supported`
* Extended next hop: `supported`
* **No Clearnet Endpoint! You have to provide your endpoint(IPv4 only)!**
* **ICMP packets are filtered** out at the public endpoint by the service provider, please **use tcpping to the port 80** of following URLs to measure the latency
* Architecture: [RootlessRouter-UML](https://github.com/KusakabeSi/RootlessRouter-UML/)
* Server status: https://42status.kskb.eu.org/

Autopeer URL & Lookong Glass     | Location                     | Open Peering | Plan    |Bandwidth |Public IP| SLA   |
---------------------------------|------------------------------|--------------|---------|--------- |---------|-------|
https://dn42jp.azurewebsites.net |Japan Tokyo                   | O            | F1 plan | 2mbps    | X       | No    |
https://dn42ch.azurewebsites.net |Switzerland Zürich            | O            | F1 plan | 2mbps    | X       | No    |
https://dn42ca.azurewebsites.net |Canada Toronto                | O            | F1 plan | 2mbps    | X       | No    |
https://dn42au.azurewebsites.net |Australia Canberra            | O            | F1 plan | 2mbps    | X       | No    |
https://dn42uae.azurewebsites.net|United Arab Emirates Dubai    | O            | F1 plan | 2mbps    | X       | No    |
https://appsg.azurewebsites.net  |Singapore                     | O            | B1 plan | 100mbps  | X       | 99.95%|
https://dn42usw.azurewebsites.net|United States Washington      | Δ (unstable) | F1 plan | 2mbps    | X       | No    |          
https://dn42hk.azurewebsites.net |Hong Kong                     | Δ (unstable) | F1 plan | 2mbps    | X       | No    |          
https://dn42nl.azurewebsites.net |Netherlands                   | Δ (unstable) | F1 plan | 2mbps    | X       | No    |               


### Route Propagation Graph
[![RPG1111](https://bgp-api.strexp.net/as_graph/AS4201271111)](https://bgp42.strexp.net/asInfo/4201271111)

## Dynamic IP

This is an example crontab which cam resolve the ip periodically to prevent lost connection after dynamic chabged.
```
*/10 * * * * wg set dn42-kskb peer "{wireguard public key}" endpoint "{peer wg endpoint}"
```
