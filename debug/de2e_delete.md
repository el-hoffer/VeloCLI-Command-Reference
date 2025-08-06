#	--de2e_delete &lt;vceid&gt;

##	Description
Tears down Dynamic Edge to Edge (DE2E) tunnels to the specified VeloCloud Edge (VCE). This command is used to manually remove dynamically established tunnels to a particular peer Edge.

##  Arguments
| Argument  | Description |
|-----------|-------------|
| `&lt;vceid&gt;` | Required. The UUID of the VeloCloud Edge (VCE) to which existing Dynamic Edge to Edge (DE2E) tunnels should be torn down. This ID can be found using the `debug --de2e_print` print command. |

##  Example usage
```
example_com:velocli> debug --de2e_delete 82354916-b421-4c48-b3b5-6e0a06795804
{'vceid': '82354916-b421-4c48-b3b5-6e0a06795804'}
{
  "DE2E": "Dynamic tunnel tear down command issued!!"
}
```

##  Field descriptions
This command outputs the target edge ID and a confirmation of the tunnel deletion being issued.