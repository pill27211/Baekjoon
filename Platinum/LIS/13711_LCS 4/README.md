# [Platinum V] LCS 4 - 13711

[문제 링크](https://www.acmicpc.net/problem/13711)

### 문제 요약

<p>두 수열이 주어지면, 두 수열의 LCS 길이를 찾아보자.</p>

### 제한

TL : 2sec, ML : 512 MB

1 ≤ N ≤ 100,000

두 수열 A, B에는 1부터 N까지의 정수가 각각 한 번씩 등장한다.

### 성능 요약

메모리: 3192 KB, 시간: 24 ms

### 분류

가장 긴 증가하는 부분 수열(o(nlogn)), 이분 탐색(binary_search)


### comment

문제의 조건을 곰곰이 생각해 보면, 이 문제는 lcs의 탈을 쓴 lis 문제임을 바로 알아차릴 수 있다.

N ≤ 100,000이므로 dp가 아닌 이분 탐색 등을 활용해 lis를 구해주자.