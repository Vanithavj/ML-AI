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
bfs(visited,graph,'1')<br><br><br><br>
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
<b>OUTPUT:</b><br><br><br>

![image](https://user-images.githubusercontent.com/97940332/207026465-d03c3220-cfa0-4907-b516-d362464b365b.png)
