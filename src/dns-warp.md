# DNS - WARP

[Cloudflare 1.1.1.1](https://developers.cloudflare.com/1.1.1.1/). is Cloudflare’s public DNS resolver. It offers a fast, free, and private way to browse the Internet. It is available at Windows, Apple IOS and Mac app stores. It Installs and runs without configuring. It uses an encrypted service through DNS over HTTPS (DoH) or DNS over TLS (DoT) for increased security and privacy.

---

## `1.1.1.1` with WARP

### Useful WARP links:
>
> [1111 with WARP is a Better VPN](https://blog.cloudflare.com/1111-warp-better-vpn/)
> 
> [Introducing WARP: Fixing Mobile Internet Performance and Security](https://blog.cloudflare.com/1111-warp-better-vpn/)
> 
> [WARP Client](https://developers.cloudflare.com/warp-client/)

`1.1.1.1` with WARP is the fastest, free, and most secure, most privacy-respecting DNS resolver on the Internet, and is also available at Windows, Apple IOS and Mac app stores. It installs and runs without configuring.

Internet service providers can see every site and app visited, even if they’re encrypted. Some providers may sell this data, or use it to target ads. Cloudflare business model is based on not sell data, or using it to target ads.

The Cloudflare WARP product prevents  snooping by encrypting more of the traffic leaving a device. WARP also provide easy access to some of the other Cloudflare functions, such as [Cloudflare for Teams](https://developers.cloudflare.com/cloudflare-one/)

The Cloudflare WARP client utilizes the more modern Wireguard protocol, which runs in user space to support a broader set of OS options with faster user experience than traditional options. 

The WARP application uses [BoringTunOpen](https://blog.cloudflare.com/boringtun-userspace-wireguard-rust/) external link to encrypt traffic from devices and sends it directly to Cloudflare’s edge network. This ensures the connection is secure and private and prevents third parties from accessing traffic. No VPN needed.

---

## Give it a Test Drive

After installing WARP, check if it is are connected to 1.1.1.1 by visiting [1.1.1.1/help](https://1.1.1.1/help)

If it works for you,  maybe distribute it to others in the company. It may help them by fixing performance and security issues, especially those away from the office and VPN users

---

## WARP Options

`1.1.1.1`WARP has two options: one that blocks only malware and another that blocks both malware and adult content. Install it by changing the DNS IP address settings.

### Malware Blocking 

Change router DNS to:  
`1.1.1.2` 
`1.0.0.2`

### Malware and Adult Content Blocking Together

Change router DNS to:  
`1.1.1.3`  
`1.0.0.3`

---


## WARP with Firewall

If a firewall  restrict Internet traffic, it may need a few changes to allow WARP to connect.

> [WARP Firewall Rules](https://developers.cloudflare.com/cloudflare-one/connections/connect-devices/warp/deployment/firewall)

Client Orchestration API

The WARP client talks with the Cloudflare edge via a standard HTTPS connection for operations like registration or settings changes. To perform these operations, you must allow this IPv4 address:

- IPv4 API Endpoint: `162.159.192.1`

> The Orchestration API endpoint is currently shared with our Consumer WARP Client. In early 2022 we will be splitting this out to its own dedicated IP address.

### ​DoH IP

All DNS requests through WARP are sent via DoH (DNS over HTTPS). The following IP addresses must be reachable for DNS to work correctly.

- Pv4 DoH Address: `162.159.36.1`

- IPv6 DoH Address: `2606:4700:4700::1111`

### ​WARP Ingress IP

These are the IP addresses that the WARP client uses to connect. All traffic from your device to the Cloudflare edge will go through these IP addresses.

- IPv4 Range: `162.159.193.0/24`

- IPv6 Range: `2606:4700:100::/48`

### ​WARP UDP Ports

WARP utilizes UDP for all of its communications. By default, the UDP Port required for WARP is: `UDP 2408`. WARP can fallback to: `UDP 500`, `UDP 1701`, or UDP 4500`.

### ​Creating firewall rules
If your organization does not currently allow Inbound/Outbound communication over the IP addresses and ports described above you must manually add an exception. The rule at a minimum needs to be scoped to the following process based on your platform:

- Windows: `C:\Program Files\Cloudflare\Cloudflare WARP\warp-svc.exe`

- macOS: `/Applications/Cloudflare WARP.app/Contents/Resources/CloudflareWARP`

---





