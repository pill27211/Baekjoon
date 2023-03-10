
# [Gold IV] 여행 - 2157

[문제 링크](https://www.acmicpc.net/problem/2157)

### 문제 요약

<p> M개 이하의 도시만을 거치며 1번 도시에서 N번 도시로 갈 때, 먹게 되는 기내식 점수의 최댓값을 구해보자. </p>

### 제한

TL : 2sec, ML : 128 MB

1 ≤ N ≤ 300

2 ≤ M ≤ N

1 ≤ K ≤ 100,000

1 ≤ c ≤ 10,000

### 성능 요약

메모리: 2728 KB, 시간: 108 ms

### 분류

다이나믹 프로그래밍(dp), 그래프 이론(graphs)

### comment

dp[i][j] : i번 도시에서 j개의 도시를 거쳐 N번 도시로 갈 때의 최댓값.

N의 범위가 작아 인접 행렬로 표현해도 충분하다. 중복 간선이 들어올 수 있으니 이에 대해 c가 가장 큰 간선으로 세팅해주자.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

우선 M개 이하의 도시만을 거쳐야 하므로 1번 도시에서 1개 도시를 거쳤을 때, 2개 도시를 거쳤을 때, 3, ... M개 도시를 거쳤을 때를 고려해보며 최댓값을 찾아주었다.

예제를 예시로 생각해보자.

만약 1에서 3으로 3개의 도시를 거쳐가는 경우를 계산한다고 해보자. (출발점과 도착점 포함)

탑다운 dp함수에서 파라미터로 두 개의 값을 받는다고 했을 때(현재 도시, 거쳐야 하는 도시 수)

출발점을 포함해야 하므로 최초 호출은 f(1, 2)가 되어야 한다.

이후 1에서 2로 이동할 때 호출은 f(2, 1)가 되어야 한다. (이동 시마다 거쳐야 하는 도시 수가 하나씩 감소하므로)

그렇다면 최종 탈출 조건(기저 조건)은 어떻게 구성되어야 할까 ?

일단 현재 도시 == N 이어야 한다. (여행 경로는 반드시 1번 도시에서 시작해서 N번 도시에서 끝나야 하므로)

추가로, 우린 dp테이블을 위와 같이 정의하였으므로 반드시 j개의 도시를 거쳐야만 한다.

따라서 기저 조건은 현재 보는 도시가 N임과 동시에 거쳐야 하는 도시 수가 0이 되어야 한다. (이외의 경우엔 정답에 영향이 없을 정도로 작은 값을 리턴)

이를 그대로 코드에 옮겨주고 dp[1][1, 2, ... , M]에 대한 최댓값을 찾아주면 끝.
