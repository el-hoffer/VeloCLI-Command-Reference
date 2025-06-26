#	`--ctx_log_toggle [all|TID] [1|0]`

##	Description
The `--ctx_log_toggle` command enables or disables context logging for threads on the VeloCloud Edge. Context logging provides detailed, thread-specific information useful for diagnostics and is enabled for all threads by default. The command requires specifying a target for the logging (either all threads or a specific Thread ID) and the desired state (enable or disable).

##  Arguments
The command requires two positional arguments:

| Argument         | Description                                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `all` or `TID`   | (First positional argument, required) Specifies the target for context logging. <br> - `all`: Applies the logging state to all threads. <br> - `TID`: Applies the logging state to a specific thread, identified by its Thread ID. Replace `TID` with the actual numerical thread identifier. |
| `1` or `0`       | (Second positional argument, required) Specifies the action for context logging. <br> - `1`: Enables context logging for the specified target. <br> - `0`: Disables context logging for the specified target. |

##  Example usage

```
example_com:velocli> debug --ctx_log_toggle 22081 0
{
  "Success": "Success"
}
```


##  Field descriptions
This command is used to perform an action (toggling logging status) and does not produce tabular output with distinct fields, instead a status of the operation is provided.