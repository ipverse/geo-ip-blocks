# geo-ip-blocks

## 🔍 Try it online

Look up any IP address or prefix at **[Lens by ipverse](https://lens.ipverse.net)** to see its country and AS information.

## Overview

> **New repo alert:** Don't let the star count fool you - the prefixes are here, the stars are just still propagating. Being freshly launched, there may be a few bugs crawling around. If you spot one, please report it in the [feedback repo](https://github.com/ipverse/feedback).

Daily-updated IPv4 and IPv6 prefixes by country, derived from network registration data.

This dataset reflects the country codes in actual network registration records - capturing sub-allocations and reassignments (SWIP) that RIR delegation files miss. Keep in mind this is where operators *registered* their blocks, which doesn't always match where traffic actually originates.

Prefixes are aggregated (adjacent and overlapping CIDR blocks are merged where possible) and filtered by size (IPv4 ≤ /28, IPv6 ≤ /56). If these lists are too large for your use case, check out [country-ip-blocks](https://github.com/ipverse/country-ip-blocks) which uses RIR delegation files and produces smaller lists.

Available formats: JSON and plaintext

**JSON format**:
```json
{
  "country": "Marshall Islands",
  "countryCode": "MH",
  "exportMode": "aggregated",
  "prefixes": {
    "ipv4": [
      "23.181.56.0/24",
      "64.86.23.0/24",
      "103.202.148.0/22"
    ],
    "ipv6": [
      "2001:4b28:4c00::/40",
      "2405:400::/32"
    ]
  }
}
```

**Plaintext format** (Marshall Islands IPv4):
```
# Country: Marshall Islands (MH)
# Address family: IPv4
# Export mode: Aggregated
#
23.181.56.0/24
64.86.23.0/24
103.202.148.0/22
```

**Plaintext format** (Marshall Islands IPv6):
```
# Country: Marshall Islands (MH)
# Address family: IPv6
# Export mode: Aggregated
#
2001:4b28:4c00::/40
2405:400::/32
```

## How to use

Download the prefixes for a specific country (Marshall Islands in these examples):

**Marshall Islands in JSON format:**
```bash
curl https://raw.githubusercontent.com/ipverse/geo-ip-blocks/master/country/mh/mh.json
```

**Marshall Islands IPv4 addresses:**
```bash
curl https://raw.githubusercontent.com/ipverse/geo-ip-blocks/master/country/mh/mh-ipv4.txt
```

**Marshall Islands IPv6 addresses:**
```bash
curl https://raw.githubusercontent.com/ipverse/geo-ip-blocks/master/country/mh/mh-ipv6.txt
```

### Firewall integration

If you plan to use this data for firewalling purposes, have a look at:

- [ipset-blacklist](https://github.com/trick77/ipset-blacklist) - ipset/iptables based Bash script, IPv4 only
- [ipverse-tools-crowdsec](https://github.com/ipverse/tools/blob/main/crowdsec/README.md) - Ban prefixes using Crowdsec's `cscli` command

## Use cases
- Geo-based access control and traffic routing
- Block traffic by country at the firewall
- Network research and statistical analysis
- Threat hunting and security research
- Compliance-based IP filtering
- Pretty much anything where you need to map country codes to IP prefixes

## Related projects

- **[country-ip-blocks](https://github.com/ipverse/country-ip-blocks)**: Country-level IP blocks from RIR delegation files (less granular, but authoritative)
- **[as-ip-blocks](https://github.com/ipverse/as-ip-blocks)**: IP blocks by autonomous system number (ASN) from BGP routing data

## Questions or issues?

Head over to the [feedback repository](https://github.com/ipverse/feedback) if you have questions, issues, or suggestions.

## License

This data is released under [CC0 1.0 Universal](LICENSE).
