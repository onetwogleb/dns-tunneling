## General info
DNS tunnels inside DoH

* Type: Course project
* Subject: Network Securiry
* Institution: SCE - Shamoon College of Engineering

## Description

The goal of the project is to detect (classify) DNS tunnels inside DoH
connections with mixed traffic (benign DoH and DNS tunnels over DoH).

**DNS Tunnel** = encapsulating TCP connection into DNS queries
(requests and responses)

**Malicious traffic** = a DNS tunnel, e.g., covert tunnels

**DoH proxy**, which translates classical unencrypted DNS traffic into
encrypted DoH

## Project architecture

![architecture](https://user-images.githubusercontent.com/73392242/122454886-7a6da100-cfb4-11eb-9582-4403334f3117.png)

As you can see configuration is deployed on laptop (Windows OS) with 3 virtual machines (two of them used for DNS tunneling and one as DoH Proxy). 

Also we need an own domain with special resource records. We have main domain `onetwogleb.tech`, subdomain as **A** record `home.onetwogleb.tech` and **NS** record `tunnel.onetwogleb.tech` which uses **A** record as DNS server.


## Configuration

*	Proxy: [DoH Proxy](https://github.com/facebookexperimental/doh-proxy)
*	Tool for DNS tunneling: [dns2tcp](https://github.com/alex-sector/dns2tcp)
*	Link types: Ethernet | Wi-Fi
*	Resolver: Cloudflare

DoH proxy is deployed on VM Zorin OS. We used doh-stub part of this proxy and forwarded all requests to **dns-cloudflare.com**

For perfoming DNS tunneling dns2tcp was installed on two VMs – Debian (server side) and elementaryOS (client side). 

## Capturing traffic

Different networks (Ethernet and Wi-Fi) and different actions were perfomed to generate traffic (mostly web-browsing).

PCAP files dated 19-23 May were collected using Apple device (iPhone).

And PCAP files dated since 24 May were collected using standard router with Ethernet cabel and Wi-Fi network.

For generating traffic were used normal actions of an internet user and also clicker programs which opened random web-sites via special resources.

## About repo

This repo contains two folders with PCAP files (doh and ndoh) and PCAP file with tunnel example.

- doh folder contains two folders (ethernet and wifi)

- ndoh folder contains PCAP file with ndoh traffic and keylog file with TLS keys
