---
date created: Monday, February 9th 2026, 8:48:59 am
date modified: Monday, February 9th 2026, 8:50:50 am
tags:
  - dns
  - ip
  - dig
  - networking
---

# ipasn.net DNS tricks

source for the things below: https://blog.apnic.net/2026/02/09/from-the-stupid-dns-tricks-department-ipasn-net/

- Query an IPv4 prefix directly (no octet-reversal) to get compact origin-ASN mapping data from `ipasn.net`

```shell
dig +short TXT 216.88.0.0.origin.asn.ipasn.net
```

- Query an IPv6 prefix directly to get compact origin-ASN mapping data for IPv6

```shell
dig +short TXT 2401:2000:6660::.origin6.asn.ipasn.net
```

- Get the full enriched record for an IP (BGP visibility, prefix, ASN, org, country, RIR, registration, and RPKI fields)

```shell
dig +short TXT 216.88.0.0.ipasn.net
```

- Request the same enriched IP record as JSON-formatted TXT output for easier machine parsing

```shell
dig +short TXT 216.88.0.0.json.ipasn.net
```

- Resolve a hostname through the `ipasn.net` DNS backend and return an enriched record for the default address family

```shell
dig +short TXT www.potaroo.net.dns.ipasn.net
```

- Resolve a hostname but force IPv4 (`A`) lookup

```shell
dig +short TXT www.potaroo.net.a.dns.ipasn.net
```

- Resolve a hostname but force IPv6 (`aaaa`) lookup

```shell
dig +short TXT www.potaroo.net.aaaa.dns.ipasn.net
```

- Query a single attribute (`cc`) to return only the country code for an IP

```shell
dig +short TXT 216.88.0.0.cc.ipasn.net
```

- Query a single RPKI-focused attribute (`rpki`) for concise validation/prefix/AS/TAL details

```shell
dig +short TXT 216.88.0.0.rpki.ipasn.net
```
