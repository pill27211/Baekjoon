
# [Diamond V] 특공대 - 4008

[문제 링크](https://www.acmicpc.net/problem/4008)

### 문제 요약

<p> 문제에 정의된 전투력 측정 방식을 따를 때, $n$명의 병사들에 대해 얻을 수 있는 최대 조정 전투력을 구해보자. </p>

### 제한

TL : 1sec, ML : 64 MB

$1 ≤ n ≤ 1,000,000$

$-5 ≤ a ≤ -1$

$|b|, |c| ≤ 10,000,000$

$1 ≤ n_i ≤ 100$


### 성능 요약

메모리: 41084 KB, 시간: 132 ms

### 분류

다이나믹 프로그래밍(dp), 볼록 껍질을 이용한 최적화(convex hull optimization)

### comment

이 문제역시 CHT 대표 문제로 불린다.

물론 CHT 태그를 타고 보게 된 문젠데 처음 본 내 반응은 "이게 왜 CHT?" 였다.

바로 문제로 들어가보자.

우선 연속 부분 수열로 이루어지는 경우를 고려해야 하므로

길이 $n$의 수열을 입력 받음과 동시에 누적 합 수열로 바꿔주자. ( $A[]$ )

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### $dp[i]$ : $1$ ~ $i$의 병사들로 구성할 수 있는 최대 조정 전투력.

나이브한 풀이를 생각해보자.

문제에 정의된 함수 $g(x) = a * x^2 + b * x + c$ 라 하고 초기값 $dp[i] = g(A[i])$ 일 때

$1 ≤ j < i$ 에서 $dp[i] = max(dp[i], dp[j] + g(A[i] - A[j]))$ 로 정리할 수 있다.

모든 $i$에 대한 $j$를 돌아보면 $O(N^2)$으로 문제를 해결할 수 있다.

우항을 전개하여 좀 더 세부적으로 식을 들여다보자.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

$dp[j] + g(A[i] - A[j])$

$= dp[j] + a * (A[i]-A[j])^2 + b * (A[i]-A[j]) + c$

$= dp[j] + a * A[i]^2 - 2 * a * A[i] * A[j] + a * A[j]^2 + b * A[i] - b * A[j] + c$

위에서 정의한 $j, i$의 범위 관계에 따라 $A[i] = x$로 두고 $Δj$의 영향을 보기 위해 $j$가 포함된 항들을 앞으로 빼자.

$f(x) = -2 * a * A[j] * x + a * A[j]^2 - b * A[j] + dp[j] + a * A[i]^2 + b * A[i] + c$

$Δj$와 무관한 상수항을 제외하면

$f(x) = -2 * a * A[j] * x + a * A[j]^2- b * A[j] + dp[j]$

따라서 기울기 $-2 * a * A[j]$, $y$절편 $a * A[j]^2- b * A[j] + dp[j]$ 을 갖는 직선의 방정식의 꼴로 정리할 수 있다. ( $f(x) = ax + b$ )

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

결국 이 문제는 $1 ≤ i ≤ n$ 인 $i$에 대해 $max(f(i))$를 찾는 것이 된다.

하지만 위에서 말했듯 $i$마다 $1 ≤ j < i$인 모든 $j$에 대해 돌아볼 순 없는 노릇이다.

다음을 보자.

* $A[]$는 '누적 합' 배열이다.
* $n_i$는 $1 ≤ n_i ≤ 100$를 만족한다.
* 즉, $A[]$는 단조 증가한다.
* $f(x)$의 기울기 $-2 * a * A[j]$ 에서 $A[]$가 단조 증가 하고 $-2 * a(-5 ≤ a ≤ -1)$ 가 양수 이므로 $f(x)$의 기울기 역시 단조 증가한다.

따라서 기울기에 이분 탐색을 적용해 $O(N logN)$으로 문제를 해결할 수 있다.
