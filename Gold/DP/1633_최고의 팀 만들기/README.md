
# [Gold IV] 최고의 팀 만들기 - 1633

[문제 링크](https://www.acmicpc.net/problem/1633)

### 문제 요약

<p> 각 플레이어들의 능력치가 주어진다. (15, 15) 쌍으로 팀을 만들 때 만들 수 있는 팀 중 가장 큰 능력치를 갖는 팀의 능력치를 구해보자. </p>

### 제한

TL : 1sec, ML : 128 MB

30 ≤ n ≤ 1,000

1 ≤ n_i, n_j ≤ 100

### 성능 요약

메모리: 3028 KB, 시간: 4 ms

### 분류

다이나믹 프로그래밍(dp)

### comment

dp[i][j][k] : i번 선수를 두고 고민할 차례에서 현재까지 뽑은 흑, 백 선수가 각각 j, k명일 때 이후로 구할 수 있는 가장 큰 능력치의 팀.

입력 방식이 조금 특이하다. EOF처리를 잘 해주자.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

3개의 파라미터를 든 채 탑다운 DP를 진행해보자. (n, p, q) == (현재 보는 선수 번호, 현재까지 뽑은 흑 선수, 현재까지 뽑은 백 선수)

기저 조건은 문제에도 주어졌듯이 흑, 백 선수가 각각 15명일 때로 세팅해주자.

선수들의 흑, 백 능력치를 각각 a[n], b[n]라고 할 때 임의의 선수 n에 대해 3가지 경우를 염두해 볼 수 있다.

* n을 흑 선수로 선택할 경우 -> a[n] + f(n + 1, p + 1, q)
* n을 백 선수로 선택할 경우 -> b[n] + f(n + 1, p, q + 1)
* n을 선택하지 않는 경우 -> f(n + 1, p, q)

이때 첫번째 경우와 두번째 경우는 p와 q가 각각 15 미만일 때만 고려할 수 있는 경우다. 따라서 조건문으로 잡아주며 15 미만일 때만 수행되게 하자.

세번째 경우는 언제든 고려해볼 수 있으므로 항상 고려해주도록 한다.

최종적으로 도출되는 최댓값을 출력 해주면 끝.
