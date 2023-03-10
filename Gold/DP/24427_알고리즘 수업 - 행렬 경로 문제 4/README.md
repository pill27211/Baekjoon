
# [Gold IV] 알고리즘 수업 - 행렬 경로 문제 4 - 24427

[문제 링크](https://www.acmicpc.net/problem/24427)

### 문제 요약

<p> 2차원 행렬 상에서 (1, 1) -> (n, n)으로 이동하려 한다. 특정 지점들이 주어질 때, 이 지점을 '적어도 하나' 거치는 최댓값을 구해보자. </p>

### 제한

TL : 1sec, ML : 512 MB

5 ≤ n ≤ 1,000

1 ≤ n_i ≤ 100,000

1 ≤ P ≤ n^2 - 2

### 성능 요약

메모리: 10828 KB, 시간: 244 ms

### 분류

다이나믹 프로그래밍(dp)

### comment

dp[i][j] : (i, j)까지 이동하며 얻을 수 있는 가장 큰 점수.

우선 아무 조건 없이 (1, 1)에서 (n, n)으로 향하는 경로 상 최댓값을 계산해보며 dp 테이블을 채워보자.

이때 dp테이블의 임의의 위치 dp[i][j]는 '특정 지점' | '그냥 지점'으로 나뉜다.

여기서 우린 **적어도 하나**의 특정 지점을 거치는 경우에 대한 최댓값을 구해야 하므로 dp 테이블에서 '그냥 지점'에 해당하는 위치를 모두 0으로 만들자. (고려할 필요가 없는 위치이므로)

그럼 특정 위치의 ← 또는 ↑ 에 0이 아닌 값이 남아 있다면 다음의 점화식을 적용할 수 있다.

dp[i][j] = max({ dp[i][j], dp[i - 1][j] + a[i][j], dp[i][j - 1] + a[i][j] });

최종 dp[n][n]에 기록된 값을 출력해주면 끝.
