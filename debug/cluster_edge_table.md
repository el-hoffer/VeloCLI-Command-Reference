#	--cluster_edge_table

##	Description
This command displays the mapping table between peer clusters and the VeloCloud Edges associated with them.

##  Arguments
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --cluster_edge_table
[
  {
    "cluster_id": "2e56aa7a-6f8b-4802-a2d1-3be3f97387ae",
    "initiators": [],
    "responder_id": "e1330e2d-632c-40af-8e54-64544ac41647"
  }
]
```

##  Field descriptions
| Column | Description |
|---|---|
| `cluster_id` | Logical ID of the peer cluster |
| `initiators` | Logical ID of cluster member initiators (if any) |
| `responder_id` | Logical ID of assigned destination cluster member. |