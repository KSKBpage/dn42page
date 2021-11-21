# Peer with Kusakabe Si
This page provides the information to get started on peering with the `Kusakabe-Neo` and `KSKB-AS` network

## What is DN42?

[DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) is a big dynamic VPN, which employs Internet technologies (BGP, whois database, DNS, etc) for educational and amateur scientific research purposes. Participants connect to each other using network tunnels (GRE, OpenVPN, Tinc, IPsec, Wireguard) and exchange routes thanks to the BGP. 

Network addresses are assigned in the `172.20.0.0/14` and `10.0.0.0/8` range and private AS numbers are used as well as IPv6 addresses from the ULA-Range (`fd00::/8`) 

[DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) can be used to learn networking and to connect private networks, such as hackerspaces or community networks. But above all, experimenting with routing in [DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) is fun!

## Peering Requests

If you’d like to peer with me, you can...
1. Contact me on telegram https://t.me/KusakabeSi
2. Use AutoPeer service listed below

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
* Host in **relative stable** VPS/VM
* Speed : **100mbps**
* Multiprotocol BGP: `supported`
* Extended next hop: `supported`
* Architecture: Normal linux distribution.


### Nodes
#### Taiwan
* DN42 IPv4 : `172.22.77.33`
* DN42 IPv6 : `fd28:cb8f:4c92::33`
* Link local IPv6 : `fe80::42:1817:1`
* Wireguard Public key : `jxCsSXtUSVjaP+eMWOyRsHg3JShQfBFEtyssMKWQaS8=`
* Port: `{20000 + your_asn/10000}`
* Endpoint: `tw.kskb.eu.org`
* Endpoint(IPv4): `4.tw.kskb.eu.org`
* Endpoint(IPv6): `6.tw.kskb.eu.org`
* CronJob: `*/10 * * * * wg set dn42-kskb peer "jxCsSXtUSVjaP+eMWOyRsHg3JShQfBFEtyssMKWQaS8=" endpoint "tw.kskb.eu.org:$Port"`
* AutoPeer: https://tw42.kskb.eu.org
* Hosting in my bedroom-cloud

This node uses dynamic IP, so make sure to set a crontob to resolve my ip periodically to prevent lost connection after my IP chabged.

### Route Propagation Graph
[![RPG1817](https://bgp-api.strexp.net/as_graph/AS4242421817)](https://bgp42.strexp.net/asInfo/4242421817)

## Kusakabe-Neo (AS4201271111)
* ASN : `AS4201271111`
* **Host in relative cheap, low-end container**
* Speed : **2mbps**
* Multiprotocol BGP: `supported`
* Extended next hop: `supported`
* **No Clearnet Endpoint! You have to provide your endpoint(IPv4 only)!**
* ICMP packets are filtered out at the public endpoint by the service provider, please use tcpping to the port 80 of following URLs to measure the latency
* Architecture: [RootlessRouter-UML](https://github.com/KusakabeSi/RootlessRouter-UML/)
* Server status: https://42status.kskb.eu.org/

URL                              | Location  | Accept New Peer
---------------------------------|-------|-------|
https://dn42jpe.azurewebsites.net|Japan Tokyo| O
https://dn42ch.azurewebsites.net |Switzerland Zürich| O
https://dn42ca.azurewebsites.net |Canada Toronto| O
https://dn42au.azurewebsites.net |Australia Canberra| O
https://dn42uae.azurewebsites.net|United Arab Emirates Dubai| O
https://appsg.azurewebsites.net  |Singapore| O
https://dn42usw.azurewebsites.net|United States Washington| Δ (unstable)
https://dn42hk.azurewebsites.net |Hong Kong| Δ (unstable)
https://dn42nl.azurewebsites.net |Netherlands| ? (stability unknown)
https://dn42br.azurewebsites.net |Brazil São Paulo| X (very unstable)


### Route Propagation Graph
[![RPG1111](https://bgp-api.strexp.net/as_graph/AS4201271111)](https://bgp42.strexp.net/asInfo/4201271111)

<!---
### Hong Kong
* DN42 IPv4 : `10.127.111.1`
* DN42 IPv6 : `fd10:127:e00f:1::1`
* Link local IPv6 : `fe80::aa:1111:1`
* Wireguard Public key : `2JHMpwkKaAMuMBrmapx9zqgGDIZOX9HZw5V2c1l66R8=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42hk.azurewebsites.net/
* Accept New Peer: No

### Japan Tokyo
* DN42 IPv4 : `10.127.111.9`
* DN42 IPv6 : `fd10:127:e00f:9::1`
* Link local IPv6 : `fe80::aa:1111:9`
* Wireguard Public key : `2CxGhL9UwlCB3ybwD1OF2Or18vCPgChS0rdh3Nc8S0c=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42jpe.azurewebsites.net/
* Accept New Peer: **Yes**

### Singapore
* DN42 IPv4 : `10.127.111.17`
* DN42 IPv6 : `fd10:127:e00f:11::1`
* Link local IPv6 : `fe80::aa:1111:11`
* Wireguard Public key : `7TIbiifNzh8HxLUM8cBvwmBo/kuaCAUCRahbBMoVA1Q=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42sg.azurewebsites.net/
* Accept New Peer: No

### United States Washington
* DN42 IPv4 : `10.127.111.33`
* DN42 IPv6 : `fd10:127:e00f:21::1`
* Link local IPv6 : `fe80::aa:1111:21`
* Wireguard Public key : `ffcWCDuBP3YdufFzOaiW2QeZLFG/GXg4QfbWTZ6LVz8=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42usw.azurewebsites.net/
* Accept New Peer: No

### Canada Toronto
* DN42 IPv4 : `10.127.111.51`
* DN42 IPv6 : `fd10:127:e00f:33::1`
* Link local IPv6 : `fe80::aa:1111:33`
* Wireguard Public key : `2FSX+6N/PwfipN/jXMj++4mabFQj25MXDy51mnnz3AA=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42ca.azurewebsites.net/
* Accept New Peer: **Yes**

### Switzerland Zürich
* DN42 IPv4 : `10.127.111.65`
* DN42 IPv6 : `fd10:127:e00f:41::1`
* Link local IPv6 : `fe80::aa:1111:41`
* Wireguard Public key : `YnoqhBTjO0+2vj/1lXqzOmvKeCwZ4q3BJzNyxN/zQ00=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42ch.azurewebsites.net/
* Accept New Peer: **Yes**

### United Kingdom London
* DN42 IPv4 : `10.127.111.66`
* DN42 IPv6 : `fd10:127:e00f:42::1`
* Link local IPv6 : `fe80::aa:1111:42`
* Wireguard Public key : `9pNKpUdPSERqELcTCcvOLSeZsSSyw3kNFYmZ7epZZ0k=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42uk.azurewebsites.net/
* Accept New Peer: No

### Australia Canberra
* DN42 IPv4 : `10.127.111.81`
* DN42 IPv6 : `fd10:127:e00f:51::1`
* Link local IPv6 : `fe80::aa:1111:51`
* Wireguard Public key : `Q7KOnB3xhaTNpszgozEXdq1cxBpYIX1JUMNV5J5JMwo=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42au.azurewebsites.net/
* Accept New Peer: **Yes**

### United Arab Emirates Dubai
* DN42 IPv4 : `10.127.111.89`
* DN42 IPv6 : `fd10:127:e00f:59::1`
* Link local IPv6 : `fe80::aa:1111:59`
* Wireguard Public key : `TfGP1jK/47H6hv1zrujkDnWvTAWhEJ5baB12JehB6gw=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42uae.azurewebsites.net/
* Accept New Peer: **Yes**

### Brazil São Paulo
* DN42 IPv4 : `10.127.111.97`
* DN42 IPv6 : `fd10:127:e00f:61::1`
* Link local IPv6 : `fe80::aa:1111:61`
* Wireguard Public key : `ByCBNxD2Hze3i6dor7EHTdVfPEccdAebmmfE1k94ex8=`
* Endpoint: `(Not available)`
* Autopeer & looking glass: https://dn42br.azurewebsites.net/
* Accept New Peer: No
-->
