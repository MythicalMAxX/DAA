<h2 id="minimum-spanning-tree">Minimum Spanning Tree:</h2>
<p>A minimum spanning tree (MST) is a tree that spans all the vertices in a connected, undirected graph and has the minimum possible total edge weight. Finding the minimum spanning tree is a classic problem in graph theory with practical applications, such as designing efficient networks and infrastructure.</p>
<p>One of the most well-known algorithms for finding the minimum spanning tree is Prim&#39;s algorithm. Another popular algorithm is Kruskal&#39;s algorithm. Both algorithms guarantee that the resulting tree has the minimum total edge weight.</p>
<h3 id="prims-algorithm">Prim&#39;s Algorithm:</h3>
<ol>
<li><p><strong>Initialization:</strong></p>
<ul>
<li>Start with an arbitrary vertex as the initial tree.</li>
<li>Set the key (minimum weight) of all other vertices to infinity.</li>
</ul>
</li>
<li><p><strong>Grow the Tree:</strong></p>
<ul>
<li>Repeat until all vertices are included in the tree:<ul>
<li>Select the vertex with the minimum key that is not yet in the tree.</li>
<li>Add the selected vertex to the tree.</li>
<li>Update the keys of adjacent vertices if they have smaller weights.</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>Termination:</strong></p>
<ul>
<li>When all vertices are included, the algorithm terminates, and the result is a minimum spanning tree.</li>
</ul>
</li>
</ol>
<h3 id="kruskals-algorithm">Kruskal&#39;s Algorithm:</h3>
<ol>
<li><p><strong>Initialization:</strong></p>
<ul>
<li>Sort all the edges in the graph in non-decreasing order of their weights.</li>
</ul>
</li>
<li><p><strong>Grow the Tree:</strong></p>
<ul>
<li>Repeat until the tree has (n-1) edges (where (n) is the number of vertices):<ul>
<li>Select the smallest edge that does not form a cycle with the edges already chosen.</li>
<li>Add the selected edge to the tree.</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>Termination:</strong></p>
<ul>
<li>When the tree has (n-1) edges, the algorithm terminates, and the result is a minimum spanning tree.</li>
</ul>
</li>
</ol>
<h3 id="example">Example:</h3>
<p>Consider the following graph:</p>
<pre><code>       2    3
   A---B----C
   |\      /|
   | \1   / |
   |  \  /  |
   |   \/   |
   |   /\   |
   |  /  4  |
   | /      |
   D--------E
       5
</code></pre>
<p>Applying Prim&#39;s algorithm starting from vertex A:</p>
<ol>
<li>A-B (weight 2)</li>
<li>B-C (weight 3)</li>
<li>A-D (weight 5)</li>
<li>D-E (weight 1)</li>
</ol>
<p>Resulting Minimum Spanning Tree:</p>
<pre><code>   A---B
   |   |
   D---E
</code></pre>
<p>Applying Kruskal&#39;s algorithm:</p>
<ol>
<li>E-D (weight 1)</li>
<li>A-B (weight 2)</li>
<li>B-C (weight 3)</li>
</ol>
<p>Resulting Minimum Spanning Tree:</p>
<pre><code>   A---B
   |   |
   D---E
</code></pre>
<h3 id="real-life-example">Real-Life Example:</h3>
<p>In a telecommunication network, the vertices can represent cities, and the edges can represent the connections between them with associated costs or distances. Finding the minimum spanning tree helps in designing a network that connects all cities with the minimum total cost, ensuring efficient communication while minimizing infrastructure expenses.</p>
<h2 id="prims-algorithm-1">Prim&#39;s Algorithm</h2>
<p>Prim&#39;s algorithm is a greedy algorithm used to find the minimum spanning tree (MST) of a connected, undirected graph. The algorithm grows the MST one vertex at a time, always selecting the vertex that has the smallest edge connecting it to the current MST. The process continues until all vertices are included in the MST.</p>
<p>Here are the steps of Prim&#39;s algorithm:</p>
<ol>
<li><p><strong>Initialization:</strong></p>
<ul>
<li>Start with an arbitrary vertex as the initial tree.</li>
<li>Set the key (minimum weight) of all other vertices to infinity.</li>
</ul>
</li>
<li><p><strong>Grow the Tree:</strong></p>
<ul>
<li>Repeat until all vertices are included in the tree:<ul>
<li>Select the vertex with the minimum key that is not yet in the tree.</li>
<li>Add the selected vertex to the tree.</li>
<li>Update the keys of adjacent vertices if they have smaller weights.</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>Termination:</strong></p>
<ul>
<li>When all vertices are included, the algorithm terminates, and the result is a minimum spanning tree.</li>
</ul>
</li>
</ol>
<h3 id="pseudocode">Pseudocode:</h3>
<pre><code class="language-plaintext">function Prim(graph):
    Initialize an empty set MST to store the minimum spanning tree.
    Select an arbitrary starting vertex s.
    Initialize keys for all vertices with infinity, except for s, which is 0.

    Create a priority queue Q and insert all vertices with their respective keys.

    while Q is not empty:
        u = extractMin(Q)
        Add u to MST.

        for each neighbor v of u:
            if v is in Q and weight(u, v) &lt; key[v]:
                key[v] = weight(u, v)
                decreaseKey(Q, v, key[v])

    return MST
</code></pre>
<h3 id="example-1">Example:</h3>
<p>Consider the following graph:</p>
<pre><code>       2    3
   A---B----C
   |\      /|
   | \1   / |
   |  \  /  |
   |   \/   |
   |   /\   |
   |  /  4  |
   | /      |
   D--------E
       5
</code></pre>
<p>Applying Prim&#39;s algorithm starting from vertex A:</p>
<ol>
<li>A-B (weight 2)</li>
<li>B-C (weight 3)</li>
<li>A-D (weight 5)</li>
<li>D-E (weight 1)</li>
</ol>
<p>Resulting Minimum Spanning Tree:</p>
<pre><code>   A---B
   |   |
   D---E
</code></pre>
<h3 id="real-life-example-1">Real-Life Example:</h3>
<p>In a computer network, vertices could represent routers or network nodes, and edges could represent the connections between them with associated costs or latencies. By applying Prim&#39;s algorithm, network engineers can find the minimum spanning tree, which helps in designing an efficient network with the minimum total connection cost, ensuring reliable and cost-effective communication.</p>
<h2 id="kruskals-algorithm-1">Kruskal&#39;s Algorithm</h2>
<p>Kruskal&#39;s algorithm is another popular greedy algorithm used for finding the minimum spanning tree (MST) of a connected, undirected graph. Similar to Prim&#39;s algorithm, Kruskal&#39;s algorithm grows the MST by adding edges one at a time, always selecting the edge with the smallest weight that does not form a cycle with the edges already included.</p>
<p>Here are the steps of Kruskal&#39;s algorithm:</p>
<ol>
<li><p><strong>Initialization:</strong></p>
<ul>
<li>Sort all the edges in the graph in non-decreasing order of their weights.</li>
</ul>
</li>
<li><p><strong>Grow the Tree:</strong></p>
<ul>
<li>Repeat until the tree has (n-1) edges (where (n) is the number of vertices):<ul>
<li>Select the smallest edge that does not form a cycle with the edges already chosen.</li>
<li>Add the selected edge to the tree.</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>Termination:</strong></p>
<ul>
<li>When the tree has (n-1) edges, the algorithm terminates, and the result is a minimum spanning tree.</li>
</ul>
</li>
</ol>
<h3 id="pseudocode-1">Pseudocode:</h3>
<pre><code class="language-plaintext">function Kruskal(graph):
    Initialize an empty set MST to store the minimum spanning tree.
    Sort all edges in the graph in non-decreasing order of their weights.

    Create a disjoint-set data structure to keep track of connected components.

    for each vertex v:
        MakeSet(v)

    for each edge (u, v) in sorted order:
        if FindSet(u) ≠ FindSet(v):
            Add (u, v) to MST.
            Union(u, v)

    return MST
</code></pre>
<h3 id="example-2">Example:</h3>
<p>Consider the following graph:</p>
<pre><code>       2    3
   A---B----C
   |\      /|
   | \1   / |
   |  \  /  |
   |   \/   |
   |   /\   |
   |  /  4  |
   | /      |
   D--------E
       5
</code></pre>
<p>Applying Kruskal&#39;s algorithm:</p>
<ol>
<li>E-D (weight 1)</li>
<li>A-B (weight 2)</li>
<li>B-C (weight 3)</li>
</ol>
<p>Resulting Minimum Spanning Tree:</p>
<pre><code>   A---B
   |   |
   D---E
</code></pre>
<h3 id="real-life-example-2">Real-Life Example:</h3>
<p>In a road network, vertices could represent cities or intersections, and edges could represent the roads or highways connecting them with associated travel distances. Kruskal&#39;s algorithm can help in finding the minimum spanning tree, which represents the most cost-effective way to connect all cities or intersections with the minimum total road distance, ensuring efficient transportation planning.</p>
