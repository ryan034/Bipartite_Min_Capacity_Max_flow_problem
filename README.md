Specialized max flow problem involving an bipartite graph. Finds the minimum capacity of the edges leading from the source needed to achieve maximum flow between the two independent sets. Has O(logV*VE^2) complexity where V is the number of vertices and E is the number of edges.

The example application below involves the senario between donors and celebrities.

```
donors = {'abe': ['abi'],
'bob': ['abi'],
'cath': ['abi', 'dee', 'bea', 'col'],
'dan': ['abi', 'adam'],
'fay': ['abi', 'dee', 'jon', 'hope', 'fred'],
'gav': ['gay', 'abi'],
'hal': ['abi'],
'ian': ['ivy', 'jon', 'adam'],
'jess': ['abi', 'dee']}   
      
celebs =  ['abi', 'adam', 'col', 'ivy', 'jon', 'dee', 'fred', 'bea', 'hope', 'gay']     

result = min_capacity_max_flow(donors, celebs)
bipartite_graph = result[0]
min_cap = result[1] 
print("Maximum number of games required by any one celebrity = " + str(min_cap) + ":") 
print_pairing(bipartite_graph, 's', 't', min_cap, celebs)
```

```
Maximum number of games required by any one celebrity = 3:
abi->bob
abi->abe
abi->hal
adam->dan
adam->ian
col->cath
jon->fay
dee->jess
gay->gav
```
