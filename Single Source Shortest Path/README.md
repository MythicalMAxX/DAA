<h2 id="single-source-shortest-path">Single Source Shortest Path</h2>
<p>Single Source Shortest Path (SSSP) algorithms find the shortest paths from a single source vertex to all other vertices in a weighted graph. One of the most well-known algorithms for this task is Dijkstra&#39;s algorithm, which works for graphs with non-negative edge weights. Another algorithm, Bellman-Ford algorithm, handles graphs with negative edge weights and detects negative weight cycles.</p>
<h3 id="dijkstras-algorithm">Dijkstra&#39;s Algorithm:</h3>
<p>Dijkstra&#39;s algorithm works by maintaining a set of vertices whose shortest distance from the source is known. It repeatedly selects the vertex with the smallest known distance, relaxes its neighbors, and adds them to the set of vertices with known distances. The process continues until all vertices are included.</p>
<p><strong>Pseudocode:</strong></p>
<pre><code class="language-plaintext">function Dijkstra(graph, source):
    Initialize distance array dist[] and set all distances to infinity.
    Set distance to source vertex as 0.
    Create a priority queue (min-heap) Q.

    while Q is not empty:
        u = extractMin(Q)
        for each neighbor v of u:
            if dist[u] + weight(u, v) &lt; dist[v]:
                dist[v] = dist[u] + weight(u, v)
                decreaseKey(Q, v, dist[v])

    return dist
</code></pre>
<h3 id="bellman-ford-algorithm">Bellman-Ford Algorithm:</h3>
<p>The Bellman-Ford algorithm is more versatile than Dijkstra&#39;s algorithm as it can handle graphs with negative edge weights. However, it&#39;s less efficient than Dijkstra&#39;s algorithm for non-negative graphs.</p>
<p><strong>Pseudocode:</strong></p>
<pre><code class="language-plaintext">function BellmanFord(graph, source):
    Initialize distance array dist[] and set all distances to infinity.
    Set distance to source vertex as 0.

    // Relax all edges repeatedly
    for i from 1 to |V| - 1:
        for each edge (u, v) in graph:
            if dist[u] + weight(u, v) &lt; dist[v]:
                dist[v] = dist[u] + weight(u, v)

    // Check for negative weight cycles
    for each edge (u, v) in graph:
        if dist[u] + weight(u, v) &lt; dist[v]:
            // Negative weight cycle detected

    return dist
</code></pre>
<h3 id="example">Example:</h3>
<p>Consider the following directed graph:</p>
<pre><code>A --2--&gt; B --1--&gt; C
 \           / |
  \         /  |
   \-3-&gt; D --5--&gt; E
</code></pre>
<ul>
<li><p><strong>Dijkstra&#39;s Algorithm from A:</strong></p>
<ul>
<li>Shortest distances: A (0), B (2), C (3), D (2), E (7)</li>
</ul>
</li>
<li><p><strong>Bellman-Ford Algorithm from A:</strong></p>
<ul>
<li>Shortest distances: A (0), B (2), C (3), D (2), E (7)</li>
</ul>
</li>
</ul>
<h3 id="real-life-example">Real-Life Example:</h3>
<p>In a transportation network, vertices could represent cities or intersections, and edges could represent roads or highways with associated travel times or distances. Single Source Shortest Path algorithms help in finding the quickest or shortest routes from a starting point to all other locations, facilitating efficient navigation and route planning in transportation systems.</p>
<h2 id="dijkstras-algorithm-1">Dijkstra&#39;s Algorithm</h2>
<p>Dijkstra&#39;s Algorithm is a widely used algorithm in graph theory for finding the shortest paths from a single source vertex to all other vertices in a weighted graph with non-negative edge weights. It works by iteratively selecting the vertex with the smallest known distance from the source and updating the distances to its neighbors.</p>
<p>Here are the steps of Dijkstra&#39;s Algorithm:</p>
<ol>
<li><p><strong>Initialization:</strong></p>
<ul>
<li>Initialize an array <code>dist</code> to store the shortest distances from the source vertex to each vertex in the graph. Set <code>dist[source]</code> to 0 and all other distances to infinity.</li>
<li>Create a priority queue (min-heap) to maintain the vertices with their current known distances. Add the source vertex with distance 0 to the queue.</li>
</ul>
</li>
<li><p><strong>Main Loop:</strong></p>
<ul>
<li>While the priority queue is not empty:<ul>
<li>Extract the vertex <code>u</code> with the minimum known distance from the priority queue.</li>
<li>For each neighbor <code>v</code> of <code>u</code>:<ul>
<li>If the distance to <code>u</code> plus the weight of the edge <code>(u, v)</code> is less than the current known distance to <code>v</code>, update <code>dist[v]</code> and enqueue <code>v</code> with the updated distance.</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>Result:</strong></p>
<ul>
<li>After the algorithm completes, the array <code>dist</code> contains the shortest distances from the source vertex to all other vertices in the graph.</li>
</ul>
</li>
</ol>
<h3 id="pseudocode">Pseudocode:</h3>
<pre><code class="language-plaintext">function Dijkstra(graph, source):
    Initialize distance array dist[] and set all distances to infinity.
    Set distance to source vertex as 0.
    Create a priority queue (min-heap) Q and enqueue source with distance 0.

    while Q is not empty:
        u = extractMin(Q)
        for each neighbor v of u:
            if dist[u] + weight(u, v) &lt; dist[v]:
                dist[v] = dist[u] + weight(u, v)
                decreaseKey(Q, v, dist[v])

    return dist
</code></pre>
<h3 id="example-1">Example:</h3>
<p>Consider the following directed graph:</p>
<pre><code>A --2--&gt; B --1--&gt; C
 \           / |
  \         /  |
   \-3-&gt; D --5--&gt; E
</code></pre>
<p>Applying Dijkstra&#39;s algorithm starting from vertex A:</p>
<ol>
<li>A (0), B (2), D (2)</li>
<li>B (2), D (2), C (3)</li>
<li>D (2), B (2), C (3), E (7)</li>
</ol>
<p>Resulting shortest distances from A to other vertices:</p>
<ul>
<li>A (0), B (2), C (3), D (2), E (7)</li>
</ul>
<h3 id="real-life-example-1">Real-Life Example:</h3>
<p>In a computer network, vertices could represent routers or network nodes, and edges could represent communication links with associated latencies or delays. Dijkstra&#39;s algorithm can help in finding the shortest paths from one router to all other routers, ensuring efficient data transmission and communication within the network.</p>
<h2 id="bellmans-ford-algorithm">Bellman&#39;s Ford Algorithm</h2>
<p>The Bellman-Ford algorithm is a versatile algorithm for finding the shortest paths from a single source vertex to all other vertices in a weighted graph. It can handle graphs with negative edge weights and can also detect negative weight cycles. The algorithm works by iteratively relaxing the edges, updating the estimated distances until no further improvement is possible or detecting a negative cycle.</p>
<p>Here are the steps of the Bellman-Ford algorithm:</p>
<ol>
<li><p><strong>Initialization:</strong></p>
<ul>
<li>Initialize an array <code>dist</code> to store the shortest distances from the source vertex to each vertex in the graph. Set <code>dist[source]</code> to 0 and all other distances to infinity.</li>
<li>Optionally, you can also initialize a predecessor array <code>prev</code> to track the predecessor of each vertex in the shortest paths.</li>
</ul>
</li>
<li><p><strong>Relax Edges:</strong></p>
<ul>
<li>Repeat the relaxation process for each edge <code>(u, v)</code> in the graph:<ul>
<li>If <code>dist[u] + weight(u, v) &lt; dist[v]</code>, update <code>dist[v]</code> to <code>dist[u] + weight(u, v)</code> and update <code>prev[v]</code> to <code>u</code>.</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>Check for Negative Cycles:</strong></p>
<ul>
<li>After relaxing all edges, check for the presence of negative weight cycles by iterating over all edges and checking if there are further improvements. If any improvement is possible, then a negative cycle exists.</li>
</ul>
</li>
<li><p><strong>Result:</strong></p>
<ul>
<li>The array <code>dist</code> contains the shortest distances from the source vertex to all other vertices in the graph. If there are no negative cycles, these distances are the shortest paths.</li>
</ul>
</li>
</ol>
<h3 id="pseudocode-1">Pseudocode:</h3>
<pre><code class="language-plaintext">function BellmanFord(graph, source):
    Initialize distance array dist[] and set all distances to infinity.
    Set distance to source vertex as 0.
    Optionally, initialize predecessor array prev[].

    for i from 1 to |V| - 1:
        for each edge (u, v) in graph:
            if dist[u] + weight(u, v) &lt; dist[v]:
                dist[v] = dist[u] + weight(u, v)
                prev[v] = u

    // Check for negative weight cycles
    for each edge (u, v) in graph:
        if dist[u] + weight(u, v) &lt; dist[v]:
            // Negative weight cycle detected

    return dist, prev
</code></pre>
<h3 id="example-2">Example:</h3>
<p>Consider the following directed graph:</p>
<pre><code>A --2--&gt; B --1--&gt; C
 \           / |
  \         /  |
   \-3-&gt; D --5--&gt; E
</code></pre>
<p>Applying Bellman-Ford algorithm starting from vertex A:</p>
<ol>
<li>A (0), B (2), D (2)</li>
<li>B (2), D (2), C (3)</li>
<li>D (2), B (2), C (3), E (7)</li>
</ol>
<p>Resulting shortest distances from A to other vertices:</p>
<ul>
<li>A (0), B (2), C (3), D (2), E (7)</li>
</ul>
<h3 id="real-life-example-2">Real-Life Example:</h3>
<p>Bellman-Ford can be used in network routing protocols to find the shortest paths in a network. In a telecommunication network, vertices could represent routers or network nodes, and edges could represent communication links with associated latencies or delays. The algorithm helps ensure efficient data transmission and communication within the network, even in the presence of negative edge weights or potential network failures.</p>
