#ML-AI

#1.BFS
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
 OUTPUT:<br>
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
visited=set()<br>
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
from collections import defaultdict<br>
jug1,jug2,aim=4,3,2<br>
visited=defaultdict(lambda:False)<br>
def waterjugSolver(amt1,amt2):<br>
    if(amt1==aim and amt2 ==0)or(amt2==aim and amt1==0):<br>
        print(amt1,amt2)<br>
        return True<br>
    if visited[(amt1,amt2)]==False:<br>
        print(amt1,amt2)<br>
        visited[(amt1,amt2)]=True<br>
        return(waterjugSolver(0,amt2)or<br>
              waterjugSolver(amt1,0)or<br>
               waterjugSolver(jug1,amt2)or<br>
               waterjugSolver(amt1,jug2)or<br>
               waterjugSolver(amt1+min(amt2,(jug1-amt1)),<br>
                             amt2-min(amt2,(jug1-amt1)))or<br>
               waterjugSolver(amt1-min(amt1,(jug2-amt2)),<br>
                             amt2=min(amt1,(jug2-amt2))))<br>
    else:<br>
        return False<br>
print("Steps:")<br>
waterjugSolver(0,0)<br>
<b>OUTPUT:</b><br>
![image](https://user-images.githubusercontent.com/97940332/207577086-cfb62c46-4913-44cf-a612-02e08f3eabb1.png)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>#4.Tower Of Hanoi</b><br>
def TowerOfHanoi(n,source,destination,auxiliary):<br>
    if n==1:<br>
        print("Move disk 1 from source",source,"to deastination",destination)<br>
        return<br>
    TowerOfHanoi(n-1,source,auxiliary,destination)<br>
    print("Move disk",n,"from source",source,"to destination",destination)<br>
    TowerOfHanoi(n-1,auxiliary,destination,source)<br>
n=3<br>
TowerOfHanoi(n,'A','B','C')<br>
<b>OUTPUT</b><br>
![image](https://user-images.githubusercontent.com/97940332/207577811-0acec237-13a7-45b7-b418-230fba5907aa.png)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>5.Best First Search</b><br>
from queue import PriorityQueue<br>
import matplotlib.pyplot as plt<br>
import networkx as nx<br>
def best_first_search(source,target,n):<br>
    visited=[0] * n<br>
    visited[source]=True<br>
    pq=PriorityQueue()<br>
    pq.put((0,source))<br>
    while pq.empty()==False:<br>
        u=pq.get()[1]<br>
        print(u,end=" ")<br>
        if u==target:<br>
            break<br>
        for v,c in graph[u]:<br>
            if visited[v]==False:<br>
                visited[v]=True<br>
                pq.put((c,v))<br>
            #print()<br>
def addedge(x,y,cost):<br>
    graph[x].append((y,cost))<br>
    graph[y].append((x,cost))<br>
v=int(input("Enter the number of nodes:"))<br>
graph=[[]for i in range(v)]<br>
e=int(input("Enter the number of edges:"))<br>
print("Enter the edges along with their weights: ")<br>
for i in range(e):<br>
    x,y,z=list(map(int,input().split()))<br>
    addedge(x,y,z)<br>
source=int(input("Enter the source Node:"))<br>
target=int(input("Enter the target/destination Node:"))<br>
print("Path:",end="")<br>
best_first_search(source,target,v)<br>
<b>OUTPUT</b><br>
![image](https://user-images.githubusercontent.com/97940332/207578184-c0824c28-de9c-4fc7-9464-f2d6d5f9874a.png)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
 #6.TIC TAC TOE
 #Tic-Tac-Toe Program using<br>
#random number in Python<br>

#importing all necessary libraries<br>
import numpy as np<br>
import random<br>
from time import sleep<br>

#Creates an empty board<br>


def create_board():<br>
	return(np.array([[0, 0, 0],<br>
					[0, 0, 0],<br>
					[0, 0, 0]]))<br>

#Check for empty places on board<br>


def possibilities(board):<br>
	l = []<br>

	for i in range(len(board)):<br>
		for j in range(len(board)):<br>

			if board[i][j] == 0:<br>
				l.append((i, j))<br>
	return(l)<br>

#Select a random place for the player<br>


def random_place(board, player):<br>
	selection = possibilities(board)<br>
	current_loc = random.choice(selection)<br>
	board[current_loc] = player<br>
	return(board)<br>

#Checks whether the player has three<br>
#of their marks in a horizontal row<br>


def row_win(board, player):<br>
	for x in range(len(board)):<br>
		win = True<br>

		for y in range(len(board)):<br>
			if board[x, y] != player:<br>
				win = False<br>
				continue<br>
<br>
		if win == True:<br>
			return(win)<br>
	return(win)<br>

#Checks whether the player has three<br>
#of their marks in a vertical row<br>


def col_win(board, player):<br>
	for x in range(len(board)):<br>
		win = True<br>

		for y in range(len(board)):<br>
			if board[y][x] != player:<br>
				win = False<br>
				continue<br>
<br>
		if win == True:<br>
			return(win)<br>
	return(win)<br>

#Checks whether the player has three<br>
#of their marks in a diagonal row<br>


def diag_win(board, player):<br>
	win = True<br>
	y = 0<br>
	for x in range(len(board)):<br>
		if board[x, x] != player:<br>
			win = False<br>
	if win:<br>
		return win<br>
	win = True<br>
	if win:<br>
		for x in range(len(board)):<br>
			y = len(board) - 1 - x<br>
			if board[x, y] != player:<br>
				win = False<br>
	return win<br>

#Evaluates whether there is<br>
#a winner or a tie<br>


def evaluate(board):<br>
	winner = 0<br>

	for player in [1, 2]:<br>
		if (row_win(board, player) or<br>
				col_win(board, player) or<br>
				diag_win(board, player)):<br>

			winner = player<br>

	if np.all(board != 0) and winner == 0:<br>
		winner = -1<br>
	return winner<br>

#<br>Main function to start the game<br>


def play_game():<br>
	board, winner, counter = create_board(), 0, 1<br>
	print(board)<br>
	sleep(2)<br>
<br>
	while winner == 0:<br>
		for player in [1, 2]:<br>
			board = random_place(board, player)<br>
			print("Board after " + str(counter) + " move")<br>
			print(board)<br>
			sleep(2)<br>
			counter += 1<br>
			winner = evaluate(board)<br>
			if winner != 0:<br>
				break<br>
	return(winner)<br>


#Driver Code<br>
print("Winner is: " + str(play_game()))<br>
<br><br>
OUTPUT:
![image](https://user-images.githubusercontent.com/97940332/208875975-8696aa19-9149-4ca0-a7b7-fb21b1f0f1d6.png)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------



