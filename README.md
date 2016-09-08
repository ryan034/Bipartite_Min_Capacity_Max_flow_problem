Specialized max flow problem involving an bipartite graph. Finds the minimum capacity of the edges leading from the source needed to achieve maximum flow between the two independent sets. Has O(logV*VE^2) complexity where V is the number of vertices and E is the number of edges.

The example application below involves the senario between a set of donors and a set of celebrities. Every donor has a list of preferred celebrities, one of which will be invited to play a game of golf with them. We need to schedule each celebrity to make sure the maximum number of games any one celebrity has to play is at the minimum, assuming every donor must get a game.  

Contains two routines, min_capacity_max_flow(donor_dict, celeb_list) and print_pairing(flow_network, source, sink, min_cap, celeb_list) and the FlowNetwork(object) and Edge(object) classes.

min_capacity_max_flow(donor_dict, celeb_list) inputs a dictionary of donors whos respective values are a list of their preferred celebrities; and the list of all celebrities. It constructs the flow network bipartite graph with donor vertices on one side and celebrity vertices on the other. Every celebrity vertex is connected to a donor vertex if and only if    


eg.
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
Output:
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
