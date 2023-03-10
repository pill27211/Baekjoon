
# [Gold IV] 가장 큰 정사각형 - 1915

[문제 링크](https://www.acmicpc.net/problem/1915)

### 문제 요약

<p> 이진수로만 이루어진 2차원 배열이 주어진다. 이때, 1로만 이루어지는 가장 큰 정사각형의 크기를 구해보자. </p>

### 제한

TL : 2sec, ML : 128 MB

1 ≤ n, m ≤ 1,000

### 성능 요약

메모리: 5936 KB, 시간: 80 ms

### 분류

다이나믹 프로그래밍(dp)

### comment

dp[i][j] : i행 j열을 포함한 정사각형의 가장 큰 변의 길이.(단, i행 j열은 1)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

(아래 내용은 a[i][j]가 1일때에 한해 수행되는 로직이다)

a[i][j]를 포함한 좌상단 정사각형의 가장 큰 변의 길이를 구하려면 어떤 것들을 고려해야 할까 ?

당연히 처음 드는 생각은 일단 a[i][j]를 기준으로 최소 위(a[i - 1][j]), 왼쪽(a[i][j - 1])이 1이어야 한다. (로직은 { 1, 1 } 부터 우, 그리고 하 로 진행되므로)

그리고 좌상 대각선(a[i - 1][j - 1])을 고려해 주어야 하는데 이는 a[i][j] 기준 좌상단으로 뻗어 나가는 정사각형의 내부가 구성될 수 있는지를 봐야 하기 때문이다.

아래의 점화식을 보자.

dp[i][j] = min(dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]) + 1

여기서 만약 dp[i - 1][j]와 dp[i][j - 1] 중 하나라도 0이라면 a[i][j]를 포함한 좌상단 정사각형은 절대 만들어질 수 없다. 즉, dp[i][j] = 1 (자기 자신만의 길이)

또한 dp[i - 1][j - 1]이 0이라면 a[i][j]를 포함한 좌상단 정사각형의 테두리는 구성될 가능성이 있다고 해도 그 내부엔 1이 아닌 곳이 있다는 것이므로 결국 dp[i][j] = 1 (자기 자신만의 길이)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

어차피 a[i][j] 기준 왼 쪽과 위 쪽은 이미 입력 받은 수 이므로 위 로직을 입력을 받으면서 동시에 진행해 주었다.
