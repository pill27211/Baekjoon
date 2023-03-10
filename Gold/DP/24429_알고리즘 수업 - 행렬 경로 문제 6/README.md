
# [Gold IV] 알고리즘 수업 - 행렬 경로 문제 6 - 24429

[문제 링크](https://www.acmicpc.net/problem/24429)

### 문제 요약

<p> 2차원 행렬 상에서 (1, 1) -> (n, n)으로 이동하려 한다. 특정 지점이 주어질 때, '모든 특정 지점을 거치는' 최댓값을 구해보자. </p>

### 제한

TL : 1sec, ML : 512 MB

5 ≤ n ≤ 1,000

1 ≤ n_i ≤ 100,000

1 ≤ P ≤ n^2 - 2

### 성능 요약

메모리: 22268 KB, 시간: 260 ms

### 분류

다이나믹 프로그래밍(dp), 정렬(sorting)

### comment

이 시리즈의 [3번째 문제](https://github.com/pill27211/Baekjoon/tree/main/Gold/DP/24426_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%20%EC%88%98%EC%97%85%20-%20%ED%96%89%EB%A0%AC%20%EA%B2%BD%EB%A1%9C%20%EB%AC%B8%EC%A0%9C%203)
에서 특정 지점을 반드시 거치는 최댓값을 구하는 과정을 정리 했었다.

이 문제에서도 그대로 적용 된다.

똑같은 방식을 이 문제에 적용한다면 (1, 1)부터 가까운 순으로 정렬된 특정 지점들을 p1, p2, ...pk라 할 때

(1, 1) -> p1 -> p2, ... -> pk -> (n, n) 와 같다.

이런식으로 이동하면서 도착점에 도달할 수 없는지는 어떻게 판단할까?

이는 간단하게 확인할 수 있다.

매 이동시마다 이동을 마친 후 dp[p_i][q_i]의 값이 특정 됐는지 확인해 보면 된다.

임의의 지점에서 다음 지점으로 ↓, → 의 이동만으론 논리상 갈 수 없다면 해당 dp값이 여전히 0으로 남아 있을 테니.
