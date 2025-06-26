#	--auto_sim_switch

##	Description
Displays the current status of the automatic SIM switching feature on the VeloCloud Edge. This feature allows the Edge to automatically switch to a secondary SIM card if the primary SIM card loses connectivity, ensuring continuous cellular WAN uptime.

##  Arguments
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --auto_sim_switch
============== Auto SIM Switch ==============
status                : DISABLED
```

##  Field descriptions
| Column | Description |
|---|---|
| status | Indicates whether the automatic SIM switching feature is currently `ENABLED` or `DISABLED`. |