---
date: '2020/4/2 16:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Graph Traversal(BFS, DFS)
---

graph traversal

<!-- more -->

### What is Graph Traversal?

Graph traversal refers to the process of visiting each vertex in a graph.

### Types of Graph Traversal

  * Breadth First Search(BFS)
  * Depth First Search(DFS)

# Breadth First Search(BFS)

BFS is an algorithm for traversing Graph data structures. It starts at some arbitrary node of a graph and explores the neighbor nodes(which are at current level) first, before moving to the next level neighbors.

### Handling one Special Scenario of BFS

  * Disconnected Graph
    * Cannot traverse the graph with BFS. Because the vertecis are disconneted with each other.

### Time Complexity - BFS

  * Time Complexity - O(V+E)
  * Space Complexity - O(V+E)


<br>

# Depth First Search(DFS)

DFS is an algorithm for traversing Graph data structures. It starts selecting some arbitrary node and explores as far as possible along each edge before backtracking.



```
class Graph {
    constructor(){
        this.adjacencyList = {};
    }
    addVertex(vertex){
        if(!this.adjacencyList[vertex]) this.adjacencyList[vertex] = [];
    }

    addEdge(vertex1, vertex2){
        if(this.adjacencyList[vertex1]){
            this.adjacencyList[vertex1].push(vertex2);
        }
        if(this.adjacencyList[vertex2]){
            this.adjacencyList[vertex2].push(vertex1);
        }
    }

    removeEdge(v1, v2){
        if(this.adjacencyList[v1].includes(v2)){
            this.adjacencyList[v1] = this.adjacencyList[v1].filter( v => v !== v2);
        }
        if(this.adjacencyList[v2].includes(v1)){
            this.adjacencyList[v2] = this.adjacencyList[v2].filter( v => v !== v1);
        }
    }

    removeVertex(vertex){
        while(this.adjacencyList[vertex].length){
            const adjacentVertex = this.adjacencyList[vertex].pop();
            this.removeEdge(vertex, adjacentVertex);
        }
        delete this.adjacencyList[vertex];
    }


    depthFirstRecursive(start){
        const result = [];
        const visited = {};
        const adjacencyList = this.adjacencyList;

        (function dfs(vertex){
            if(!vertex) return null;
            visited[vertex] = true;
            result.push(vertex);
            adjacencyList[vertex].forEach(neighbor => {
                if(!visited[neighbor]){
                    return dfs(neighbor);
                }
            })
        })(start);

        return result;
    }

    depthFirstIterative(start){
        const stack = [start];
        const result = [];
        const visited = {};
        let currentVertex;

        visited[start] = true;
        while(stack.length){
            currentVertex = stack.pop();
            result.push(currentVertex);

            this.adjacencyList[currentVertex].forEach(neighbor => {
                if(!visited[neighbor]){
                    visited[neighbor] = true;
                    stack.push(neighbor);
                }
            })
        }
        return result;
    }

    breadthFirstIterative(start){
       const queue = [start];
       const result = [];
       const visited = {};
       let currentVertex
       
       visited[start] = true;
       
       while(queue.length){
            currentVertex = queue.shift();
            result.push(currentVertex);
            
            this.adjacencyList[currentVertex].forEach(neighbor=>{
                if(!visited[neighbor]){
                    visited[neighbor] = true;
                    queue.push(neighbor);
                }
            })
       }
       return result;
    }
}


let g = new Graph();

g.addVertex("A")
g.addVertex("B")
g.addVertex("C")
g.addVertex("D")
g.addVertex("E")
g.addVertex("F")


g.addEdge("A", "B")
g.addEdge("A", "C")
g.addEdge("B","D")
g.addEdge("C","E")
g.addEdge("D","E")
g.addEdge("D","F")
g.addEdge("E","F")
g.depthFirstRecursive("A")


//          A
//        /   \
//       B     C
//       |     |
//       D --- E
//        \   /
//          F
```


출처 : "Data Structures & Algorithms" by DS GUY



