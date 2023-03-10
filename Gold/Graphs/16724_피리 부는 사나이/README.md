
# [Gold III] 피리 부는 사나이 - 16724

[문제 링크](https://www.acmicpc.net/problem/16724)

### 문제 요약

<p> 2차원 상에서 사이클의 개수를 세내어 보자.  </p>

### 제한

TL : 1sec, ML : 256 MB

1 ≤ N, M ≤ 1,000

지도 밖으로 나가는 방향의 입력은 주어지지 않는다.

### 성능 요약

메모리: 6916 KB, 시간: 44 ms

### 분류

그래프 이론(graphs), 그래프 탐색(graph_traversal), 깊이 우선 탐색(dfs)

### comment

문제를 좀만 읽어보면, 사이클의 개수를 세내라는 것을 알 수 있다.

(1, 1)부터 dfs를 통해 차례로 방문 처리를 해가며 사이클일 때만 r++을 해주자.

i번째 dfs에서 방문하는 정점들에 방문 처리로 i를 저장해두면 사이클을 쉽게 판별할 수 있다.

dfs도중 i가 적혀있는 정점에 방문했다면 사이클이라는 뜻이니까.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

결과적으로 단순 그래프 탐색 문제인데 이게 왜 Gold 3 씩이나 하는지 잘 모르겠다.

분리 집합 태그가 있긴 하다만 솔직히 분리 집합만의 개념 || 최적화를 아예 생각하지 않아도 충분히 풀리는 문제인데..
