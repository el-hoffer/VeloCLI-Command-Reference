# --set_link_state_down &lt;interface_logical_name&gt;

## Description
Administratively sets the internal operational state of a specified WAN link on the VeloCloud Edge to DOWN. This command is typically used for diagnostic or testing purposes, such as:
*   Simulating a link failure to observe SD-WAN failover behavior, including how traffic is re-routed over remaining active paths and how Dynamic Multipath Optimization™ (DMPO) adapts.
*   Testing specific policy configurations, for example, how business policies react to link outages or to verify Conditional Backhaul (CBH) functionality.
*   Isolating a potentially problematic link for troubleshooting without needing to physically disconnect cables, allowing for focused diagnostics.

When a link's state is set to DOWN using this command, the VeloCloud Edge will cease to consider it for building tunnels (paths) or for forwarding user traffic. The link status will also be reported as down to the VeloCloud Orchestrator, however this avoids the need to push a configuration change and associated edge service restarts.  To bring the link back UP, a corresponding command `debug --set_link_state_up <interface_logical_name>` can be used.  Edge service restarts, reboots, HA failovers, etc. will also revert links back to their configured state.

## Arguments
| Argument                 | Description                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| `interface_logical_name` | **Required.** The logical identifier of the WAN interface to be set to the DOWN state. Common examples include `GE1`, `GE2`, `SFP1`, `USB1`, etc.

## Example Usage
To set the link `GE1` to the DOWN state:
```
example_com:velocli> debug --set_link_state_down GE1
[
  {
    "Result": "success"
  }
]
```

## Field Descriptions
| Column | Description |
|---|---|
| N/A    | This command does not produce tabular output. Upon successful execution, it returns a confirmation message indicating that the link state has been changed successfully. |