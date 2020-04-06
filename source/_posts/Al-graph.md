---
date: '2020/4/1 15:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Graph
---

graph

<!-- more -->

### What is Graph?

  * Graph is a pair of sets(V,E), where V is the set of vertices and E is the set of edges, connecting the pairs of vertices.

### Some Terminologies

  * Vertex : Vertex is the node of the graph
  * Edges : Edges are the arcs that connect pairs of vertices
  * Unweighted Graph : A graph not having a weight associated with any edge
  * Weighted Graph : A graph having a weight associated with each edge
  * Undirected Graph : It is a graph that is a set of vertices connected by edges, where the edges don't have a direction associated with them.
  * Directed Graph : It is a graph that is a set of vertices connected by edges, where the edges have a direction associated with them.
  * Cyclic Graph : A cyclic graph is a graph having at least on loop.
  * Acyclic Graph : An Acyclic graph is a graph having no loop.
  * Tree : Tree is a special case of Directed Acyclic Graph(DAG).

### Types of Graph

<Br>


{% asset_img "graph.PNG" 500 500 "Types of Graph" %}


### How is Graph represented?

  1. **Adjacency Matrix** : In graph theory, an adjacency matrix is a square matrix used to represent a finite graph. The elements of the matrix indicate whether pairs of vertices are adjacent or not in the graph.

  {% asset_img "adjacencyMatrix.PNG" 400 400 "adjacency matrix" %}

  2. **Adjacency List** : In graph theory, an adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a vertex in the graph.

{% asset_img "adjacencyList.PNG" 400 400 "adjacency list" %}


##### When to use which representation?

  * If the graph is a 'Complete' or 'near to complete' Graph, then we should use **Adjacency Matrix**.
  * If the number of 'Edges' are few, then we should use **Adjacency List**.




출처 : "Data Structures & Algorithms" by DS GUY



