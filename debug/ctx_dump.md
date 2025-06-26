#	--ctx_dump

##	Description
This command dumps the context buffer information for various threads running on the VeloCloud Edge. This information can be useful for advanced troubleshooting and understanding the state of different processes within the edge daemon.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --ctx_dump
Thread Name       Thread ID  ON
edged.ev_thr          15777   1
edged                 15638   1
link_state_fsm        15685   1
vc_timer_thread       15653   1
edged                 16145   1
```

##  Field descriptions
| Column      | Description                                     |
|-------------|-------------------------------------------------|
| Thread Name | The descriptive name of the thread.             |
| Thread ID   | The unique process identifier for the thread.   |
| ON          | Indicates the context logging status (`1` means logging is enabled, `0` is disabled). |