#	--dns_ip_cache_flush [IP ADDRESS | v4 | v6 | all]

##	Description
This command is used to flush the DNS IP cache on the VeloCloud Edge. Clearing the cache can be useful for troubleshooting DNS resolution issues or ensuring that the Edge fetches the latest DNS records.

##  Arguments (optional)
| Argument     | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| `IP ADDRESS` | Flushes the cache entry for the specified IP address.                       |
| `v4`         | Flushes all IPv4 entries from the DNS IP cache.                             |
| `v6`         | Flushes all IPv6 entries from the DNS IP cache.                             |
| `all`        | Flushes all entries (both IPv4 and IPv6) from the DNS IP cache. This is the default action if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --dns_ip_cache_flush
{
  "ALERT": "DNS cache cleaned up"
}
```

##  Field descriptions
The command output is a JSON message confirming the action.