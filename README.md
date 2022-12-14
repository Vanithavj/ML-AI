# ML-AI

<b>#1.BFS</b><br>
graph={<br>
    '1':['2','10'],<br>
    '2':['3','8'],<br>
    '3':['4'],<br>
    '4':['5','6','7'],<br>
    '5':[],<br>
    '6':[],<br>
    '7':[],<br>
    '8':['9'],<br>
    '9':[],<br>
    '10':[]<br>
    }<br>
visited=[]<br>
queue=[]<br>
def bfs(visited,graph,node):<br>
    visited.append(node)<br>
    queue.append(node)<br>
    while queue:<br>
        m=queue.pop(0)<br>
        print(m,end=" ")<br>
        for neighbour in graph[m]:<br>
            if neighbour not in visited:<br>
                visited.append(neighbour)<br>
                queue.append(neighbour)<br>
print("Following is the Breadth-First Search:")<br>
bfs(visited,graph,'1')<br>
<b>OUTPUT:</b><br>

![image](https://user-images.githubusercontent.com/97940332/207026350-272364f6-19bb-49c6-813e-d4d450dad8b6.png)
----------------------------------------------------------------------------------------------------------------------------------------------------------
<b>#2.DFS</b><br>
graph={<br>
    '5':['3','7'],<br>
    '3':['2','4'],<br>
    '7':['6'],<br>
    '6':[],<br>
    '2':['1'],<br>
    '1':[],<br>
    '4':['8'],<br>
    '8':[]<br>
}<br>
visited=set() #Set to keep track of visited nodes of graph<br>
def dfs(visited,graph,node):<br>
    if node not in visited:<br>
        print(node)<br>
        visited.add(node)<br>
        for neighbour in graph[node]:<br>
            dfs(visited,graph,neighbour)<br>
print("Following is the Depth-First Search:")<br>
dfs(visited,graph,'5')<br>
<b>OUTPUT:</b><br>

![image](https://user-images.githubusercontent.com/97940332/207026465-d03c3220-cfa0-4907-b516-d362464b365b.png)
------------------------------------------------------------------------------------------------------------------------------------------------------------------

<b>#3.Water jug problem</b><br>

from collections import defaultdict
jug1,jug2,aim=4,3,2
visited=defaultdict(lambda:False)
def waterjugSolver(amt1,amt2):
    if(amt1==aim and amt2 ==0)or(amt2==aim and amt1==0):
        print(amt1,amt2)
        return True
    if visited[(amt1,amt2)]==False:
        print(amt1,amt2)
        visited[(amt1,amt2)]=True
        return(waterjugSolver(0,amt2)or
              waterjugSolver(amt1,0)or
               waterjugSolver(jug1,amt2)or
               waterjugSolver(amt1,jug2)or
               waterjugSolver(amt1+min(amt2,(jug1-amt1)),
                             amt2-min(amt2,(jug1-amt1)))or
               waterjugSolver(amt1-min(amt1,(jug2-amt2)),
                             amt2=min(amt1,(jug2-amt2))))
    else:
        return False
print("Steps:")
waterjugSolver(0,0)
<b>OUTPUT:</b><br>
![image](https://user-images.githubusercontent.com/97940332/207577086-cfb62c46-4913-44cf-a612-02e08f3eabb1.png)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>#4.Tower Of Hanoi</b><br>
def TowerOfHanoi(n,source,destination,auxiliary):
    if n==1:
        print("Move disk 1 from source",source,"to deastination",destination)
        return
    TowerOfHanoi(n-1,source,auxiliary,destination)
    print("Move disk",n,"from source",source,"to destination",destination)
    TowerOfHanoi(n-1,auxiliary,destination,source)
    
n=3
TowerOfHanoi(n,'A','B','C')
<b>OUTPUT</b><br>
![image](https://user-images.githubusercontent.com/97940332/207577811-0acec237-13a7-45b7-b418-230fba5907aa.png)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>5.Besy First Search</b><br>
from queue import PriorityQueue
import matplotlib.pyplot as plt
import networkx as nx

def best_first_search(source,target,n):
    visited=[0]*n
    visited[source]=True
    pq=PriorityQueue()
    pq.put((0,source))
    while pq.empty()==False:
        u=pq.get()[1]
        print(u,end=" ")
        if u==target:
            break
        for v,c in graph[u]:
            if visited[v]==False:
                visited[v]=True
                pq.put((c,v))
            #print()
def addedge(x,y,cost):
    graph[x].append((y,cost))
    graph[y].append((x,cost))
v=int(input("Enter the number of nodes:"))
graph=[[]for i in range(v)]
e=int(input("Enter the number of edges:"))
print("Enter the edges along with their weights: ")
for i in range(e):
    x,y,z=list(map(int,input().split()))
    addedge(x,y,z)
source=int(input("Enter the source Node:"))
target=int(input("Enter the target/destination Node:"))
print("Path:",end="")
best_first_search(source,target,v)
<b>OUTPUT</b><br>
![image](https://user-images.githubusercontent.com/97940332/207578184-c0824c28-de9c-4fc7-9464-f2d6d5f9874a.png)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
           



