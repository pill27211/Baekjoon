# [Platinum V] 거의 최단 경로 - 5719

[문제 링크](https://www.acmicpc.net/problem/5719)

### 문제 요약

<p>여러 개의 테스트 케이스에서 그래프와 시작점, 도착점이 주어진다. 이때, 최단경로가 아닌 '거의 최단경로'를 찾아보자.</p>

### 제한

TL : 1sec, ML : 256 MB

2 ≤ N ≤ 500 { 정점의 번호는 0, 1, 2, ... n - 1 }

1 ≤ M ≤ 10000

유향 그래프이며 입력으로 주어지는 임의의 정점 U에서 V를 잇는 간선은 유일하다.

### 성능 요약

메모리: 3296 KB, 시간: 124 ms

### 분류

그래프 이론(graphs), 그래프 탐색(graph_traversal), 다익스트라(dijkstra), 너비 우선 탐색(bfs)


### comment

예전에 처음 보고 생각이 안나서 즐겨찾기 해두고 꽤 묵혀뒀다가 풀게 된 문제인데, 결과적으로 이 문제는 다익스트라 2번, 역추적 1번(bfs 활용)으로 해결할 수 있다.

우선 처음 다익스트라를 수행하며 각 정점으로의 최단거리 갱신이 일어날 때마다 해당 간선을 따로 모아둔다.(인접 행렬이던, 간선 배열의 형태이던.. 등등)

이후 도착점으로부터 첫 다익스트라에서 표시해둔 간선들을 이용해 최단거리를 만드는 간선들을 모두 제거한다.(bfs역추적)

다시 시작점으로부터 다익스트라를 수행하며 '거의 최단 경로'를 찾는다.(도착점으로 갈 수 있다면 출력, 아니면 -1)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

++ 최초 간선들을 모아둘 때 거리 갱신이 일어날때만 처리해서 틀렸다.(-> 당연히 거리가 같을 때도 처리해주어야 함)

++ 역추적 과정을 대충 짰더니 비효율적이게 작동하여 메모리 초과를 여러번 얻어맞았다.(-> 적절한 방문 처리를 해주며 진행해야 함)
