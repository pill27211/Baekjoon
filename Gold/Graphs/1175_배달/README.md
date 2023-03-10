# [Gold I] 배달 - 1175

[문제 링크](https://www.acmicpc.net/problem/1175)

### 문제 요약

<p> $N * M$ 크기의 맵에서 반드시 두 곳을 방문해야 한다. 또, 상하좌우 이동함에 있어서 직전에 이동한 방향으론 이동하지 못한다. 이때 목표 지점들을 모두 방문하는 최소 시간을 구해보자. </p>

### 제한

TL : 2sec, ML : 128 MB

$1 ≤ N, M ≤ 50$

### 성능 요약

메모리: 2068 KB, 시간: 0 ms

### 분류

그래프 이론(graphs), 그래프 탐색(graph_traversal), 너비 우선 탐색(bfs)

### comment

현재 상태를 판단함에 있어서 좌표 이외에 직전에 어느 방향으로 이동해 왔는지, 배달을 어느정도 진행 했는지가 필요하다.

이에 따라 4차원으로 방문 처리를 진행하면 간단하게 해결할 수 있다.

$V[i][j][p][q]$ : 배달 진행 상태가 $q$인 채 점 $(i, j)$ 에서 $p$방향으로 이동한 적이 있는가 ?

+ $C$인 두 곳의 차별점을 두기 위해 각각 $a$, $b$로 변경 시킨 채 풀이 하였다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
