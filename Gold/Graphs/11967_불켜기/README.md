
# [Gold II] 불켜기 - 11967

[문제 링크](https://www.acmicpc.net/problem/11967)

### 문제 요약

<p> N * N의 맵이 있다. 임의의 방에서 다른 방의 불을 켤 수 있는 M개의 스위치 정보가 주어질 때, 불을 켤 수 있는 방의 수를 구해보자. </p>

### 제한

TL : 2sec, ML : 512 MB

2 ≤ N ≤ 100

1 ≤ M ≤ 20,000

### 성능 요약

메모리: 2872 KB, 시간: 272 ms

### 분류

그래프 이론(graphs), 그래프 탐색(graph_traversal), 너비 우선 탐색(bfs)

### comment

기본적인 상하좌우 bfs탐색에서 다음이 고려된다.

* 불이 켜진 곳에만 이동할 수 있다.
* 현재 지점에 다른 지점의 불을 켤 수 있는 스위치가 있을 수 있다.
* 최초 지점 (1, 1)에는 불이 켜져 있으며, 이 곳에서 이동이 시작된다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

처음 드는 생각은 방문 처리를 어떻게 하냐인데.. 정말 단순하게 생각하면 된다.

최초 bfs를 수행하면서 불이 꺼져있는 방에 불을 켠 행동이 있었다면 현재 bfs를 마친 후 (1, 1)에서 bfs를 다시 돌려보자.

물론 이전 시행 자체에서 불을 켜며 그곳을 방문 했을 수도 있지만 그렇지 않을 경우도 있을테니 말이다.

또, 현재 bfs에서 불을 켠 행동이 있었다면 (1, 1)에서 bfs를 다시 돌려보자.

이렇게 bfs를 i, i + 1, i + 2, ... 번 돌리면 결국 더이상 불을 켠 행동이 없는 순간이 온다. 이때 로직을 끝내버리면 된다.

말그대로 머릴 비운 정말정말 나이브한 방식이다.

그러나 이렇게 해도, 범위가 작아 충분히 통과해 버린다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

이게 왜 골2?
