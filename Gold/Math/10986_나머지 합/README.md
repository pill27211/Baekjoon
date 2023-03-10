
# [Gold III] 나머지 합 - 10986

[문제 링크](https://www.acmicpc.net/problem/10986)

### 문제 요약

<p> N개의 수가 주어진다. 이때, 연속 부분 합이 M으로 나누어 떨어지는 구간의 개수를 구해보자. </p>

### 제한

TL : 1sec, ML : 256 MB

1 ≤ N ≤ 1,000,000

2 ≤ M ≤ 1,000

1 ≤ N_i ≤ 1,000,000,000

### 성능 요약

메모리: 9840 KB, 시간: 136 ms

### 분류

수학(math), 누적 합(prefix_sum)

### comment

우선 수들의 범위와 시간 제한을 보면, 대충 O(N)정도의 풀이를 의도함을 알 수 있다.

(a[j] - a[i]) % M = 0 는 모듈러 연산의 성질에 의해 (a[j] % M) - (a[i] % M) = 0 과 같음에 따라 a[j] % M = a[i] % M 을 만족하는 (i, j)쌍의 수를 찾는 문제로 바뀐다.

연속 부분 합을 다뤄야 하므로 누적 합 배열을 생각해보자.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

누적 합을 담아가며 단순히 합만이 아닌 mod M의 값으로 저장해주자.

이때 M의 범위가 힌트라면 힌트일 수 있는데 M의 최댓값인 1000개 만큼의 카운트 배열을 만들어주자.

i번째까지의 누적 합 배열을

a[i] = (a[i] + a[i - 1]) % M

라고 했을 때 이 값을 그대로 카운트에 포함 시켜주자.

c[a[i]]++

최종적으로 각 카운트 배열에 담긴 숫자의 뜻은 해당 인덱스를 나머지값으로 하는 누적 합 개수이며

임의의 카운트 인덱스 C[i] = k 에서 두 쌍을 뽑는 조합의 경우가 kC2 = (c[i] * (c[i] - 1)) / 2 가 된다.

추가로 i == j인 쌍에 대해 M으로 나누어 떨어지는 경우도 포함해 주어야 하므로 총 결과에 c[0]값을 더해주어야 한다.
