#	--set_link_state_up [interface logical name]

##	Description
This command is used to manually revert WAN links to the UP state after disabling with the `debug --set_link_state_down <interface_logical_name>` command.

##  Arguments
| Argument                 | Description                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| `interface logical name` | **Required.** Specifies the logical name of the interface whose state is to be set to UP (e.g., `GE1`, `SFP1`, `eth0`). |

##  Example Usage
To set the link `GE1` to the UP state:
```
example_com:velocli> debug --set_link_state_up GE1
[
  {
    "Result": "success"
  }
]
```
A successful execution of this command (e.g., `debug --set_link_state_up GE1`) would typically result in a confirmation message or no output if the operation is successful. The exact output for a successful command may vary.