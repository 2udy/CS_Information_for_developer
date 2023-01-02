# Dijkstra

가중치 그래프에서 최단 거리를 구하는 알고리즘

![그래프: 최단 경로 알고리즘 Shortest Path Problem 다익스트라 Dijkstra 소스코드(우선순위 큐, heapq를  이요한 구현) + 시간복잡도 : 네이버 블로그](https://mblogthumb-phinf.pstatic.net/MjAxOTAyMjBfMjc5/MDAxNTUwNjY2NjMxMTE5.Uf6ncZY2gfLm3_Dauq6BxCFVQ87UTG0wT-ELDsZwnkMg.splET7_j-hsZKvcFM5xlYinBpKPwwL1_h_YQjECI6fwg.GIF.weplayicecream/2bP4pJr4wVimqCWjYimXJe2cnCgnGNrSY8SknnG67Xj.gif?type=w800)

### 과정

1. 출발노드 설정
2. 출발 노드를 기준으로 각 노드의 최소비용 저장
3. 방문하지 않은 노드 중에서 가장 비용이 적은 노드 선택
4. 해당 노드를 거쳐 특정 노드로 가는 경우를 고려하여 최소 비용 갱신
5. 3~4 번 반복



### 구현

```python

def dijkstra(s, V):  # 시작정점 s, 마지막 정점 V
    U = [0] * (V + 1)
    U[s] = 1
    for v in range(V + 1):
        D[v] = adj[s][v]
# while len(U) != V: 
	for _ in range(V): # V= 정점 개수 -1과 같으므로 남은 점점 개수와 같음
		minV = INF
		w=0
		for i in range(V + 1):
    	if U[i] == 0 and minV > D[i]:
      	minV = D[i]
				w=i 
    U[w]=1 # 선택된 집합에 포함
	
  for v in range(V+1): # 정점 v가 
  	if 0 < adj[w][v] < INF: # w에 인접이면, 시작정점에서 w를 거쳐 v로 가능 비용과
    	D[v] = min(D[v], D[w] + adj[w][v]) # 시작정점에서 v로 가는 기존 비용을 비교 후 선택
      
INF = 10000

V, E = map(int, input().split())

adj = [[INF] * (V + 1) for _ in range(V + 1)]
for i in range(V + 1):
    adj[i][i] = 0
    
for _ in range(E):
    u, v, w = map(int, input().split())
    adj[u][v] = w  #

D = [0] * (V + 1)

dijkstra(0, V)

print(D)
```

