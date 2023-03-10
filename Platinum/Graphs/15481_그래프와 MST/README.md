# [Platinum IV] 그래프와 MST - 15481

[문제 링크](https://www.acmicpc.net/problem/15481)

### 문제 요약

<p> 그래프가 주어진다. 이때 이 그래프를 이루는 모든 간선들에 대해 해당 간선을 포함하는 최소 스패닝 트리의 가중치 합을 추가되는 간선순으로 모두 출력해보자. </p>

### 제한

TL : 2sec, ML : 512 MB

2 ≤ N ≤ 200,000

N - 1 ≤ M ≤ 200,000

1 ≤ {임의의 두 정점을 연결하는 간선의 가중치} ≤ 1,000,000,000

임의의 두 정점을 잇는 간선은 유일하다.

### 성능 요약

메모리: 54780 KB, 시간: 332 ms

### 분류

그래프 이론(graphs), 트리(trees), 최소 스패닝 트리(minimum spanning tree), 최소 공통 조상(lowest common ancestor)

### comment

당연히 매번 mst를 만드려는 생각은 버려야 한다.

최소 스패닝 트리가 있는데, 어떤 임의의 간선을 반드시 포함해야 한다고 한다. 또 이러한 사항을 최대 200,000번만큼 처리해야 한다. 어떻게 해야 할까 ?

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

최소 스패닝 트리 G가 있고, 임의의 정점 u와 v를 가중치 w로 잇는 간선 e가 있다고 했을 때 이 간선을 반드시 포함하는 mst 가중치의 합을 생각해보자.

1. 간선 e가 이미 G에 포함되어 있다면 ? 현재 mst 가중치의 합이 곧 답이다.

2. 간선 e가 G에 포함되어 있지 않다면.

: G에 입장에서 생각해보자. u와 v를 잇는 간선 e가 추가되려 하는데 이에 따라 u와 v 근방의 사이클이 형성된다. 따라서 현재 G에서 u와 v를 잇는 어떠한 간선 하나를 제거해야 트리가 유지된다.
 
어떤 간선을 제거해야 '최소 스패닝 트리'라고 할 수 있을까 ? 당연히 u와 v 사이에 존재하는 '가중치가 가장 큰 간선'을 제거해야 한다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

lca와 희소 배열을 활용해 보자.

우선 가장 먼저 보편적인 mst를 찾기 위해 최초 mst를 구축해본다. (기존의 mst 가중치 합 s 저장)이때, mst도 하나의 트리임에 따라 lca를 적용할 수 있게 된다.

따라서 기존의 간선들 이외에, 최초 mst 구축에 포함되는 모든 간선들로 형성되는 트리에 대해 lca, 희소 배열 전처리를 진행한다.

전처리를 함에 있어서 각 정점마다 2^0, 2^1, ... 2^18번째 부모를 저장함과 동시에 '해당 시점의 가장 큰 가중치'도 같이 저장한다.

(방법이 잘 떠오르지 않는다면 [이 문제](https://www.acmicpc.net/problem/3176)를 먼저 풀어보고 오자.)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

이제 모든 간선들을 순서대로 순회하며 차례로 답을 출력해주기만 하면 된다.

문제의 요구사항 "각각의 간선마다 그 간선을 포함하는 최소 스패닝 트리의 가중치 합"은 다음의 처리로 바뀌게 된다.

"i번째 간선이 임의의 정점 u와 v를 가중치 w로 잇는다고 할 때, u와 v를 잇는 mst상의 가장 큰 가중치 m을 빼주고 w를 더한 값"

-> r = s - m + w
