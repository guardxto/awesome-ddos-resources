# Awesome DDoS Resources

A curated list of standards, guides, open-source tools, public data and incident write-ups on denial-of-service attacks and how to keep websites and networks online.

Everything here is for defending systems you run. There are no attack tools, stressers or booters on this list, and pull requests that add them are closed.

This list is maintained by [GuardX](https://guardx.to), a DDoS protection provider, and links to GuardX in three places, each marked. Everything else is chosen on merit, and competitors are listed like anyone else.

## Contents

- [Standards and RFCs](#standards-and-rfcs)
- [Guides and advisories](#guides-and-advisories)
- [Web server and origin hardening](#web-server-and-origin-hardening)
- [Open-source defence tools](#open-source-defence-tools)
- [Load testing your own systems](#load-testing-your-own-systems)
- [Data and reports](#data-and-reports)
- [Incident write-ups](#incident-write-ups)
- [Research](#research)
- [Providers](#providers)

## Standards and RFCs

- [RFC 4732: Internet Denial-of-Service Considerations](https://www.rfc-editor.org/info/rfc4732) - The IAB's overview of DoS attack types and the defences that exist at each layer.
- [RFC 2827 / BCP 38: Network Ingress Filtering](https://www.rfc-editor.org/info/rfc2827) - Filtering spoofed source addresses at the network edge, the precondition for stopping reflection attacks.
- [RFC 4987: TCP SYN Flooding Attacks and Common Mitigations](https://www.rfc-editor.org/info/rfc4987) - How SYN floods work and the trade-offs of SYN cookies, caches and other mitigations.
- [RFC 7999: BLACKHOLE Community](https://www.rfc-editor.org/info/rfc7999) - The well-known BGP community for remotely triggered blackholing of attacked prefixes.
- [RFC 8955: Dissemination of Flow Specification Rules](https://www.rfc-editor.org/info/rfc8955) - BGP Flow Specification, used to push traffic filters to routers.
- [RFC 8612: DOTS Requirements](https://www.rfc-editor.org/info/rfc8612) - Requirements for DDoS Open Threat Signaling between networks under attack and mitigation providers.
- [RFC 9132: DOTS Signal Channel](https://www.rfc-editor.org/info/rfc9132) - The protocol that carries mitigation requests, even while the link is congested.
- [RFC 6585: Additional HTTP Status Codes](https://www.rfc-editor.org/info/rfc6585) - Defines 429 Too Many Requests for rate limiting.
- [MANRS](https://www.manrs.org/) - Mutually Agreed Norms for Routing Security, including anti-spoofing actions for network operators.

## Guides and advisories

- [CISA: Understanding and Responding to DDoS Attacks](https://www.cisa.gov/resources-tools/resources/understanding-and-responding-distributed-denial-service-attacks) - Joint guidance from CISA, FBI and MS-ISAC on preparing for and responding to attacks.
- [NCSC: Denial of Service (DoS) guidance](https://www.ncsc.gov.uk/collection/denial-service-dos-guidance-collection) - The UK National Cyber Security Centre's guidance on understanding, preparing for and responding to DoS.
- [CISA: UDP-Based Amplification Attacks](https://www.cisa.gov/news-events/alerts/2014/01/17/udp-based-amplification-attacks) - Alert TA14-017A with amplification factors per protocol and mitigations.
- [OWASP Denial of Service Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Denial_of_Service_Cheat_Sheet.html) - Application-level DoS weaknesses and how to avoid them in code.
- [OWASP Automated Threats to Web Applications](https://owasp.org/www-project-automated-threats-to-web-applications/) - A taxonomy of automated abuse such as scraping, credential stuffing and denial of inventory.
- [Under DDoS attack? What to do right now](https://guardx.to/under-attack) - First-hour checklist for a website under attack. *(by the maintainers of this list)*

## Web server and origin hardening

- [nginx: ngx_http_limit_req_module](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html) - Reference for request rate limiting in nginx.
- [Rate Limiting with NGINX](https://blog.nginx.org/blog/rate-limiting-nginx) - Walkthrough of limit_req with bursts, delays and allow lists.
- [Apache mod_reqtimeout](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) - Timeouts for slow request headers and bodies, the standard defence against Slowloris.
- [HAProxy rate limiting: four examples](https://www.haproxy.com/blog/four-examples-of-haproxy-rate-limiting) - Stick tables for per-client request rates and connection limits.
- [Linux IP sysctl documentation](https://docs.kernel.org/networking/ip-sysctl.html) - Kernel settings such as tcp_syncookies and backlog sizes.
- [nftables wiki](https://wiki.nftables.org/) - Documentation for the Linux packet filter, including sets and rate limits.
- [origin-configs](https://github.com/guardxto/origin-configs) - Tested nginx, Caddy, Apache and HAProxy configs for running behind a reverse proxy or CDN, plus an nftables origin lock. *(by the maintainers of this list)*

## Open-source defence tools

- [fail2ban](https://github.com/fail2ban/fail2ban) - Bans addresses that trip patterns in log files.
- [CrowdSec](https://github.com/crowdsecurity/crowdsec) - Log-based detection with shared blocklists and bouncers for web servers and firewalls.
- [Coraza](https://github.com/corazawaf/coraza) - OWASP web application firewall in Go, compatible with ModSecurity rules.
- [OWASP CRS](https://github.com/coreruleset/coreruleset) - The Core Rule Set for ModSecurity-compatible WAFs.
- [ModSecurity](https://github.com/owasp-modsecurity/ModSecurity) - The long-standing open-source WAF engine for Apache, nginx and IIS.
- [FastNetMon](https://github.com/pavel-odintsov/fastnetmon) - DDoS detection from sFlow, NetFlow, IPFIX and port mirroring.

## Load testing your own systems

Use these only against systems you own or have written permission to test.

- [k6](https://github.com/grafana/k6) - Scriptable load testing in JavaScript.
- [Vegeta](https://github.com/tsenart/vegeta) - HTTP load testing at a constant request rate.
- [wrk](https://github.com/wg/wrk) - Small, fast HTTP benchmarking tool.
- [Locust](https://github.com/locustio/locust) - Load tests written in Python, with a web UI.

## Data and reports

- [Cloudflare Radar: network layer security](https://radar.cloudflare.com/security/network-layer) - Public statistics on network-layer DDoS attacks.
- [NETSCOUT DDoS Threat Intelligence Report](https://www.netscout.com/threatreport) - Twice-yearly report on attack volumes, vectors and targets.
- [Shadowserver dashboard](https://dashboard.shadowserver.org/) - Public data on exposed and abusable services, including amplifiers.

## Incident write-ups

- [GitHub: February 28th DDoS incident report](https://github.blog/news-insights/company-news/ddos-incident-report/) - The 2018 memcached amplification attack on GitHub and how it was handled.
- [KrebsOnSecurity hit with record DDoS](https://krebsonsecurity.com/2016/09/krebsonsecurity-hit-with-record-ddos/) - The 2016 Mirai-driven attack on a journalist's site.
- [Google Cloud: the HTTP/2 Rapid Reset attack](https://cloud.google.com/blog/products/identity-security/how-it-works-the-novel-http2-rapid-reset-ddos-attack) - How the 2023 Rapid Reset attack worked.
- [Cloudflare: HTTP/2 Rapid Reset, deconstructed](https://blog.cloudflare.com/technical-breakdown-http2-rapid-reset-ddos-attack/) - Technical breakdown of the same attack from another provider.
- [CVE-2023-44487](https://nvd.nist.gov/vuln/detail/CVE-2023-44487) - The NVD entry for HTTP/2 Rapid Reset, with affected software.

## Research

- [Understanding the Mirai Botnet](https://www.usenix.org/conference/usenixsecurity17/technical-sessions/presentation/antonakakis) - USENIX Security 2017 study of Mirai's growth, targets and attacks.
- [Amplification Hell: Revisiting Network Protocols for DDoS Abuse](https://www.ndss-symposium.org/ndss2014/ndss-2014-programme/amplification-hell-revisiting-network-protocols-ddos-abuse/) - NDSS 2014 measurement of amplification factors across UDP protocols.

## Providers

Commercial DDoS protection, in alphabetical order. Listing is not an endorsement.

- [Akamai](https://www.akamai.com/solutions/ddos-protection) - DDoS protection for networks, DNS and applications. United States.
- [Bunny.net](https://bunny.net/shield/) - CDN with Bunny Shield for WAF and DDoS mitigation. Slovenia.
- [Cloudflare](https://www.cloudflare.com/products/ddos/) - CDN with DDoS mitigation for websites and networks. United States.
- [Fastly](https://www.fastly.com/products/ddos-protection) - Edge cloud with DDoS protection for applications. United States.
- [Gcore](https://gcore.com/ddos-protection) - DDoS protection for servers and websites. Luxembourg.
- [GuardX](https://guardx.to/ddos-protection) - WAF, DDoS protection and CDN for websites and APIs, operated in the EU. Germany. *(maintainer of this list)*
- [Imperva](https://www.imperva.com/products/ddos-protection-services/) - DDoS protection for websites, networks and DNS. United States, part of Thales.
- [Link11](https://www.link11.com/en/) - DDoS protection and WAF. Germany.
- [Myra Security](https://www.myrasecurity.com/en/) - DDoS protection, WAF and CDN. Germany.
- [OVHcloud Anti-DDoS](https://www.ovhcloud.com/en/security/anti-ddos/) - DDoS mitigation included with OVHcloud hosting. France.

## Contributing

Suggestions are welcome, see [contributing.md](contributing.md). Entries are checked by hand before they are added.

## License

[CC0 1.0](LICENSE): to the extent possible under law, the maintainers have waived all copyright and related rights to this list.
