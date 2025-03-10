# Getting Started with MGraph-DB

This guide will help you install and set up MGraph-DB for your project.

## Installation

```bash
pip install mgraph-db
```
## Basic Usage
```
def test_basic_graph_operations():
    from mgraph_db.mgraph.MGraph import MGraph
    
    # Create a new graph
    mgraph = MGraph()
    
    with mgraph.edit() as edit:
        # Create two nodes
        node1 = edit.new_node(node_data={"value": "First Node"})
        node2 = edit.new_node(node_data={"value": "Second Node"})
        
        # Connect nodes with an edge
        edge = edit.new_edge(from_node_id=node1.node_id, 
                            to_node_id=node2.node_id)
        
        # Verify nodes and edge were created
        assert node1.node_id is not None
        assert node2.node_id is not None
        assert edge.edge_id is not None
    
    # Query the graph
    with mgraph.data() as data:
        nodes = data.nodes()
        edges = data.edges()
        
        assert len(nodes) == 2
        assert len(edges) == 1
```