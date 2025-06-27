#	--denylist_dump

##	Description
This command displays the table of source IP addresses that have been denylisted by the VeloCloud Edge's stateful firewall flood protection mechanism. It also indicates whether stateful firewall denylisting is enabled for IPv4 and IPv6 traffic.

##  Arguments
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --denylist_dump
Stateful Firewall Denylisting : IPv4 : Disabled
                                IPv6 : Enabled
====================== SOURCE-IP LIST ====================
SOURCE-IP       EXPIRES IN(sec)
fd00:5:1:1::2                69

```

##  Field descriptions
| Column/Field | Description |
|---|---|
| Stateful Firewall Denylisting : IPv4 | Indicates if stateful firewall denylisting is `Enabled` or `Disabled` for IPv4 traffic. |
| Stateful Firewall Denylisting : IPv6 | Indicates if stateful firewall denylisting is `Enabled` or `Disabled` for IPv6 traffic. |
| SOURCE-IP | The IP address that has been denylisted. |
| EXPIRES IN(sec) | The remaining time in seconds before the denylisted IP address is removed from the list. |