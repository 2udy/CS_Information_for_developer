# LCA

(Lowest Common Ancestor) 최소공통조상 즉 두 정점이 최초로 만나는 부모 정점을 찾는 것



### 구현

1. 두 노드의 깊이를 더 낮은 노드의 깊이를 기준으로 맞춘다
2. 부모가 같아질 때 까지 두 노드를 동시에 거슬러 올라간다



### 시간복잡도

- 매 쿼리마다 부모 방향으로 거슬로 올라가기 위해 최악의 경우 *O*(*N*)의 시간 복잡도가 요구됩니다. (한쪽에 치우쳐서 일렬로 된 노드인 경우)
- 따라서 모든 쿼리(M)를 처리할 때의 시간 복잡도는 *O*(*N**M*)입니다.



### 개선된 LCA 알고리즘

- 2의 제곱 형태로 거슬러 올라가도록 하면 *O*(*l**o**g**N*)의 시간 복잡도를 보장할 수 있습니다.



### 구현

```python
import sys
input = sys.stdin.readline # 시간 초과를 피하기 위한 빠른 입력 함수
sys.setrecursionlimit(int(1e5)) # 런타임 오류를 피하기 위한 재귀 깊이 제한 설정
LOG = 21 # 2^20 = 1,000,000

n = int(input())
parent = [[0] * LOG for _ in range(n + 1)] # 부모 노드 정보
d = [0] * (n + 1) # 각 노드까지의 깊이
c = [0] * (n + 1) # 각 노드의 깊이가 계산되었는지 여부
graph = [[] for _ in range(n + 1)] # 그래프(graph) 정보

for _ in range(n - 1):
    a, b = map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)

# 루트 노드부터 시작하여 깊이(depth)를 구하는 함수
def dfs(x, depth):
    c[x] = True
    d[x] = depth
    for y in graph[x]:
        if c[y]: # 이미 깊이를 구했다면 넘기기
            continue
        parent[y][0] = x
        dfs(y, depth + 1)

# 전체 부모 관계를 설정하는 함수
def set_parent():
    dfs(1, 0) # 루트 노드는 1번 노드
    for i in range(1, LOG):
        for j in range(1, n + 1):
            parent[j][i] = parent[parent[j][i - 1]][i - 1]

# A와 B의 최소 공통 조상을 찾는 함수
def lca(a, b):
    # b가 더 깊도록 설정
    if d[a] > d[b]:
        a, b = b, a
    # 먼저 깊이(depth)가 동일하도록
    for i in range(LOG - 1, -1, -1):
        if d[b] - d[a] >= (1 << i):
            b = parent[b][i]
    # 부모가 같아지도록
    if a == b:
        return a;
    for i in range(LOG - 1, -1, -1):
        # 조상을 향해 거슬러 올라가기
        if parent[a][i] != parent[b][i]:
            a = parent[a][i]
            b = parent[b][i]
    # 이후에 부모가 찾고자 하는 조상
    return parent[a][0]

set_parent()

m = int(input())

for i in range(m):
    a, b = map(int, input().split())
    print(lca(a, b))
```

