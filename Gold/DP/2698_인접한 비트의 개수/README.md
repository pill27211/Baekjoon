
# [Gold IV] 인접한 비트의 개수 - 2698

[문제 링크](https://www.acmicpc.net/problem/2698)

### 문제 요약

<p> 수열 S의 크기 n과 k가 주어진다. 문제의 규칙에 따라 인접 비트의 개수를 구할 때, 인접한 비트의 개수가 k인 이진 수열 S의 개수를 구해보자. </p>

### 제한

TL : 1sec, ML : 128 MB

1 ≤ n, k ≤ 100

답은 항상 2,147,483,647보다 작거나 같다.

### 성능 요약

메모리: 2180 KB, 시간: 0 ms

### 분류

다이나믹 프로그래밍(dp)

### comment

dp[i][j][k] : 끝자리가 k로 끝나고 비트의 개수가 j인 길이 i 수열의 개수

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

우선 끝자리가 0으로 끝날땐 간단하게 점화식을 도출해낼 수 있다. 이전 길이의 인접 비트의 개수가 j인 수열의 수에서 0을 추가로 붙인들 그 결과는 같으므로 점화식은

dp[i][j][0] = dp[i - 1][j][0] + dp[i - 1][j][1];

그럼 끝자리가 1로 끝날땐 어떻게 점화식을 도출할까 ?

우선 1로 끝나기 때문에 이전 길이의 dp값을 참고할 때 영향이 있을 수도, 없을 수도 있다.

* 영향이 없을 경우

뒷자리가 1로 끝난다 한들 그 바로 앞자리가 0이면 어차피 1은 의미 없는 수가 된다.

따라서, 이전 길이의 인접 비트의 개수가 j면서 0으로 끝나는 수를 이번 경우의 포함 시킬 수 있다.(+ dp[i - 1][j][0])

* 영향이 있을 경우

뒷자리가 1로 끝나면서 그 앞자리가 1이면 인접 비트 수가 추가로 하나 증가하게 된다.

따라서, 이전 길이의 인접 비트의 개수가 j - 1이면서 1로 끝나는 수를 이번 경우의 포함 시킬 수 있다.(+ dp[i - 1][j - 1][1])

(현재 보고 있는 인접 비트의 개수로 맞춰야 하기 때문에 dp[i - 1][j][1]가 아닌 dp[i - 1][j - 1][1]가 되어야 한다)

최종적으로 끝자리가 1로 끝날땐 다음과같이 점화식이 도출된다.

dp[i][j][1] = dp[i - 1][j][0] + (j ? dp[i - 1][j - 1][1] : 0); (j가 0일 때 음수 인덱스에 접근하는 undefined behavior이 발생하므로 적절히 컨트롤 해주자)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

위 두 점화식을 모든 범위에 대해 시행해준 뒤 매 케이스마다 dp[i][j][0] + dp[i][j][1]의 값을 출력해주면 끝.
