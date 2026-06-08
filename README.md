\# Networking Task 02: Network Devices \& IP Addressing



\## 📌 Objective

The purpose of this task is to study common network hardware components, classify structural IP address spaces, analyze local configuration scopes, and break down the operational data communication flow during standard domain requests\[cite: 1].



\---



\## 💻 Part A: Network Devices Research



\### 1. Router

\*   \*\*Purpose:\*\* Connects entirely distinct networks together (such as bridging a private local home network to the public Internet) and routes data packets between them\[cite: 1].

\*   \*\*How it Works:\*\* Operates at Layer 3 (Network Layer) of the OSI model. It reads the destination IP addresses of incoming data packets and utilizes its internal routing table to determine the absolute best path (next hop) for the data.

\*   \*\*Real-World Usage:\*\* The standard wireless home gateway provided by an Internet Service Provider (ISP) that allows multiple household devices to share a single internet connection.



\### 2. Switch

\*   \*\*Purpose:\*\* Connects multiple hardware devices together inside the \*same\* Local Area Network (LAN) to facilitate internal data sharing\[cite: 1].

\*   \*\*How it Works:\*\* Operates at Layer 2 (Data Link Layer). It dynamically builds a MAC address table mapping the physical hardware addresses of connected devices to specific physical ports, ensuring data frames are sent directly to the intended recipient rather than broadcasted to everyone.

\*   \*\*Real-World Usage:\*\* An Ethernet switch panel deployed in an academic computer lab or corporate office to link all desktop computers to shared local printers and storage.



\### 3. Hub

\*   \*\*Purpose:\*\* A legacy network hardware component used to connect multiple devices together in a local network segment\[cite: 1].

\*   \*\*How it Works:\*\* Operates at Layer 1 (Physical Layer). It lacks any internal data-routing intelligence. When data arrives at one port, the hub blindly duplicates and broadcasts that signal to every single connected port, which frequently causes data collisions and network congestion.

\*   \*\*Real-World Usage:\*\* Deprecated in modern networking, but occasionally used in specialized legacy environments or for legacy network monitoring where total packet sniffing is required.



\### 4. Access Point (AP)

\*   \*\*Purpose:\*\* Extends the reach of a wired infrastructure network by broadcasting a wireless (Wi-Fi) signal, allowing wireless client devices to connect\[cite: 1].

\*   \*\*How it Works:\*\* Operates primarily at Layers 1 and 2. It acts as a wireless bridge that seamlessly translates digital data packets between airborne radio frequency signals and physical Ethernet cables.

\*   \*\*Real-World Usage:\*\* Enterprise Wi-Fi access points mounted across university corridors and office buildings to provide seamless wireless roaming.



\### 5. Firewall

\*   \*\*Purpose:\*\* Acts as a network security boundary controller that monitors, filters, and blocks unauthorized incoming and outgoing traffic based on pre-set rules\[cite: 1].

\*   \*\*How it Works:\*\* Inspects packet headers and payload states against configured Access Control Lists (ACLs). It analyzes parameters like source/destination IPs, protocols, and port numbers to intercept malicious behavior.

\*   \*\*Real-World Usage:\*\* A corporate perimeter firewall protecting internal database servers from open web probes, or software firewalls running locally on user operating systems.



\### 6. Modem (Modulator-Demodulator)

\*   \*\*Purpose:\*\* Bridges a local digital internal network with the dedicated analog telecommunications infrastructure provided by an ISP\[cite: 1].

\*   \*\*How it Works:\*\* Converts local digital bits into analog signals (modulation) to travel over phone lines, fiber, or coaxial cables, and translates incoming analog signals back into digital data (demodulation) for the router.

\*   \*\*Real-World Usage:\*\* The dedicated physical box sitting next to a fiber terminal entry point that brings raw external internet connectivity into a home or office space.



\---



\## 🔢 Part B: IP Address Classification



| IP Address | Category | Reason for Classification |

| :--- | :--- | :--- |

| \*\*192.168.1.10\*\* | \*\*Private\*\* | Falls squarely inside the Class C RFC 1918 private block (`192.168.0.0` - `192.168.255.255`), which is globally reserved for internal local area networks\[cite: 1]. |

| \*\*10.0.0.5\*\* | \*\*Private\*\* | Falls directly within the Class A RFC 1918 private block (`10.0.0.0` - `10.255.255.255`), reserved strictly for localized network configurations\[cite: 1]. |

| \*\*172.16.5.20\*\* | \*\*Private\*\* | Falls within the standard Class B RFC 1918 private boundary range (`172.16.0.0` - `172.31.255.255`)\[cite: 1]. |

| \*\*8.8.8.8\*\* | \*\*Public\*\* | A globally routable public IP address broadcast across the open internet, famously operating as Google's Primary Public DNS Resolver\[cite: 1]. |

| \*\*1.1.1.1\*\* | \*\*Public\*\* | A globally routable public IP address reachable on the open internet, operating as Cloudflare's Public DNS Resolver\[cite: 1]. |

| \*\*192.168.100.1\*\* | \*\*Private\*\* | Falls within the Class C RFC 1918 private space, widely utilized as default internal admin gateways for local router configurations\[cite: 1]. |



\---



\## 🔍 Part C: Understanding Your Network



Based on the local system hardware metrics extracted from the terminal interface:

\*   \*\*IPv4 Address:\*\* `10.55.194.141`

\*   \*\*Default Gateway:\*\* `10.55.194.49`

\*   \*\*DNS Server:\*\* `10.55.194.49`



\### Analytical Evaluation Questions:

1\.  \*\*Which IP range does your device belong to?\*\*  

&#x20;   The device belongs to the \*\*Class A Private Network Range\*\* (`10.0.0.0` to `10.255.255.255`)\[cite: 1].

2\.  \*\*Is it Public or Private?\*\*  

&#x20;   It is a \*\*Private IP address\*\*\[cite: 1]. It handles traffic strictly within the local area boundary and cannot be routed directly onto the open public internet.

3\.  \*\*What role does your router play in your network?\*\*  

&#x20;   The router acts as the default gateway interface node\[cite: 1]. It serves as the local DHCP server assigning private IPs, manages internal local routing, and executes Network Address Translation (NAT) to map local private requests into a valid public-facing IP space.

4\.  \*\*What would happen if the DNS server stopped working?\*\*  

&#x20;   If the DNS server goes offline, human-readable domain name resolution fails entirely\[cite: 1]. While low-level network connectivity remains functional (meaning you could still open a website if you manually entered its exact public numeric IP address into a browser), attempting to load names like `www.google.com` will result in immediate timeout errors.



\---



\## 🗺️ Part D: Network Communication Flow



Below is the structured lifecycle diagram mapping out exactly how my local station interacts with the DNS server and routes requests directly to Google's server cluster\[cite: 1]:



!\[Network Communication Flow](./diagrams/flow\_topology.png)



\### Communication Step Explanations:

\*   \*\*Step 1: Local Domain Query Check\*\*  

&#x20;   The user's browser looks up its local historical OS cache for a record matching the string domain. If a record is missing, it dispatches an outbound network query to the designated local DNS server asking for the corresponding IP address.

\*   \*\*Step 2: DNS Name Resolution\*\*  

&#x20;   The DNS server cross-references its recursive database cache or hits authoritative roots to locate the exact destination coordinates, returning the verified public destination IP mapping directly back to the local client device.

\*   \*\*Step 3: Direct Web Server Connection\*\*  

&#x20;   Armed with the numeric target coordinates, the browser completely bypasses naming layers, builds standard TCP/IP packet structures with the exact IP header, and routes an HTTPS application request out through the gateway router straight across the WAN to Google's public servers.



\---



\## ⚡ Part E: Practical Command Exercise



\### Operational Metric Evaluation Answers:

1\.  \*\*What IP address did DNS return for Google?\*\*  

&#x20;   The naming resolution process successfully returned Google’s public host infrastructure route, mapping to the global IPv6 destination address: `2404:6800:4007:802::200e`\[cite: 1].

2\.  \*\*Was the ping successful?\*\*  

&#x20;   Yes\[cite: 1]. As shown in the traceroute tracking loops, a successful network data path was maintained directly to the endpoint target node with an active round-trip connection.

3\.  \*\*Why is DNS important before communication begins?\*\*  

&#x20;   Network hardware routers and low-level protocol systems cannot parse or navigate raw alphanumeric strings like "google.com" when moving physical packets\[cite: 1]. DNS is mandatory because it transparently resolves those names into the structural numeric coordinates required to populate network headers before data leaves the system interface.



\---





