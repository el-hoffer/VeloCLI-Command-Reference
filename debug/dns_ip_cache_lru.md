#	--dns_ip_cache_lru [v4 | v6 | all]

##	Description
Displays the contents of the DNS IP address cache, which stores recently resolved domain names and their corresponding IP addresses. The cache follows a Least Recently Used (LRU) eviction policy, meaning that when the cache is full, the oldest, least accessed entries are removed to make space for new ones.

##  Arguments (optional)
| Argument | Description |
|---|---|
| v4 | Displays only IPv4 DNS cache entries. |
| v6 | Displays only IPv6 DNS cache entries. |
| all | Displays all DNS cache entries (both IPv4 and IPv6). This is the default if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --dns_ip_cache_lru
NAME                                 ADDRESS  AGE(s)  SOURCE  REFCNT  APPID
.veco12-kiad1.velocloud.net   152.65.224.129       2     DNS       2      0
.api.prod.nsxti.vmware.com     34.36.111.205      86     DNS       2      0
.gateway.zscalerthree.net      170.85.15.129      95     DNS       2      0
.gateway.zscalerthree.net     165.225.216.34      95     DNS       2      0
np-edge.itunes.apple.com        3.55.220.154     741     DPI       2      0
```

##  Field descriptions
| Column  | Description |
|---|---|
| NAME    | The fully qualified domain name (FQDN) or hostname that was resolved. |
| ADDRESS | The IP address (IPv4 or IPv6) resolved for the corresponding NAME. |
| AGE(s)  | The age of the cache entry in seconds, indicating how long ago the entry was last refreshed or added. |
| SOURCE  | The source from which the DNS resolution was obtained (`DNS` for entries derived from DNS snooping or `DPI` for entries observed via deep packet inspection in HTTP/SNI headers). |
| REFCNT  | Reference count indicating how many active flows are currently using this cached DNS entry. |
| APPID   | Application ID. This may be used internally by the VeloCloud Edge to associate the DNS entry with a specific custom application definition. |