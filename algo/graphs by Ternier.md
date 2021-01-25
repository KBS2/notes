# Graphs 

A graph is a set of vertices and a set of links.

A graph can be directed (arcs) or not directed (edges).

Let n = order of the graph (number of vertices).

Vertices will designated by their number. The number does not mean anything.

## First implementation : Adjacency Matrix (GraphMat)

* The adjacency matrix is of size n*n

* Let G be an instance of GraphMat, G.adj[i][j] = information on the link(s) between i and j

    - oriented graph : - 1-graph (no multiple arcs) -> G.adj[i][j] = True if arc (i,j) exists, False otherwise

                       - p-graph -> G.adj[i][j] = x if x arcs (i,j) exist between i and j

    - non oriented graphs : - simple graph (no multiple edges) -> G.adj[i][j] = True if edge (i,j) exists, False otherwise, the link between j and i also exists

                            - multiple graph -> G.adj[i][j] = x if x edges (i,j) exist between i and j, the x links between j and i also exists
 

### Example: adjacency matrix of Figure 1

G.adj =
[
[0,3,1,0,0,0,1,0,0],
[0,0,0,2,0,0,0,0,0],
[0,0,0,0,0,0,1,0,1],
[0,0,0,0,0,0,1,0,0],
[0,0,0,1,0,0,0,0,0],
[0,0,1,0,0,0,1,0,0],
[0,0,0,1,1,0,0,0,0],
[0,0,0,0,0,1,1,0,1],
[0,0,0,0,0,0,0,0,1],
]

**good operations**: knowing if a link exists, adding/removing links, getting the predecessors

**bad operations**: getting the successors, it takes too much space

### Class GraphMat

* G.order -> number of vertices of graph G

* G.directed -> True if G is directed, False otherwise

* G.adj -> adjacency matrix of G in the form of a list of lists


## Second implementation : Adjacency List (Graph)

* The adjacency list is a list of size n (order of the graph). each vertex has its own adjacency list (G.adjlists[i]).

* Let G be an instance of Graph, G.adjlists[i][j] = the jth successor of vertex i

    - oriented graph : - 1-graph (no multiple arcs) -> G.adjlists[i][j] = the jth successor of vertex i

                       - p-graph -> G.adjlists[i][j] = the jth successor of vertex i, elements of G.adjlists[i] can be equal in case of multiple arcs

    - non oriented graphs : - simple graph (no multiple edges) -> G.adjlists[i][j] = the jth successor of vertex i

                            - multiple graph -> G.adjlists[i][j] = the jth successor of vertex i, elements of G.adjlists[i] can be equal in case of multiple edges

## Example: Adjacency List of Figure 1 (multi-oriented graph)

G.adjlists = [
                [1,1,1,2,6], -> adjacency list of vertex 0
                [3,3]
                [6,8]
                [6]
                [3]
                [2,6]
                [3,4]
                [5,6,8]
                [8]
             ]

**good operations**: going through the successors, getting the out-degree, adding links

**bad operations**: removing links, getting predecessors

### Class Graph

* G.order -> number of vertices of graph G

* G.directed -> True if G is directed, False otherwise

* G.adjlists -> adjacency list of G in the form of a list of lists

* G.labels -> extra attribute for THE FUTURE DM, lists of labels for each vertex of the graph. For example, for Figure 3, G.labels = ["algo","maths","prog","archi","élec","phys"]
