<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:  HARISH PRANAV     </h3>
<h3>Register Number:  212225040117      </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>

``````
// A* Search Algorithm
1.  Initialize the open list
2.  Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3.  while the open list is not empty
    a) find the node with the least f on 
       the open list, call it "q"

    b) pop q off the open list
  
    c) generate q's 8 successors and set their 
       parents to q
   
    d) for each successor
        i) if successor is the goal, stop search
        
        ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
          successor.f = successor.g + successor.h

        iii) if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor

        iV) if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)
  
    e) push q on the closed list
    end (while loop)

``````
## Program
```python

import heapq

def astar(graph, h, start, goal):
    open_list = [(h[start], 0, start, [start])]
    closed = set()

    while open_list:
        f, g, node, path = heapq.heappop(open_list)

        if node == goal:
            return path

        if node in closed:
            continue

        closed.add(node)

        for neighbour, cost in graph[node]:
            if neighbour not in closed:
                new_g = g + cost
                new_f = new_g + h[neighbour]

                heapq.heappush(open_list,
                               (new_f, new_g, neighbour,
                                path + [neighbour]))

    return None


n, e = map(int, input().split())

graph = {}

for _ in range(e):
    u, v, w = input().split()
    w = int(w)

    graph.setdefault(u, []).append((v, w))
    graph.setdefault(v, []).append((u, w))

h = {}

for _ in range(n):
    node, value = input().split()
    h[node] = int(value)

start = list(h.keys())[0]
goal = list(h.keys())[-1]

path = astar(graph, h, start, goal)

if path:
    print("Path found:", path)
else:
    print("Path not found")

```

<hr>
<h2>Sample Graph I</h2>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b1377c3f-011a-4c0f-a843-516842ae056a)

<hr>
<h2>Sample Input</h2>
<hr>
10 14 <br>
A B 6 <br>
A F 3 <br>
B D 2 <br>
B C 3 <br>
C D 1 <br>
C E 5 <br>
D E 8 <br>
E I 5 <br>
E J 5 <br>
F G 1 <br>
G I 3 <br>
I J 3 <br>
F H 7 <br>
I H 2 <br>
A 10 <br>
B 8 <br>
C 5 <br>
D 7 <br>
E 3 <br>
F 6 <br>
G 5 <br>
H 3 <br>
I 1 <br>
J 0 <br>
<hr>
<h2>Sample Output</h2>
<hr>
Path found: ['A', 'F', 'G', 'I', 'J']


<hr>
<h2>Sample Graph II</h2>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/acbb09cb-ed39-48e5-a59b-2f8d61b978a3)


<hr>
<h2>Sample Input</h2>
<hr>
6 6 <br>
A B 2 <br>
B C 1 <br>
A E 3 <br>
B G 9 <br>
E D 6 <br>
D G 1 <br>
A 11 <br>
B 6 <br>
C 99 <br>
E 7 <br>
D 1 <br>
G 0 <br>
<hr>
<h2>Sample Output</h2>
<hr>
Path found: ['A', 'E', 'D', 'G']
<img width="990" height="805" alt="image" src="https://github.com/user-attachments/assets/bd7a1a94-d8fc-433e-a61a-b932fc38b84f" />
<img width="767" height="698" alt="image" src="https://github.com/user-attachments/assets/ae5a5488-ce65-46a7-bf65-e543cdcd6288" />

# Result:
Thus  Implemented  Search algorithm for a Graph using Python 3

