
# [Diamond V] 배열의 특징 - 14180

[문제 링크](https://www.acmicpc.net/problem/14180)

### 문제 요약

<p> 배열의 특징이 $C = ΣAi·i (1 ≤ i ≤ n)$로 정의된다. 배열에서 수 하나를 아무 위치로 이동시킬 수 있을 때, 가능한 $C$의 최댓값을 구해보자. </p>

### 제한

TL : 2sec, ML : 512 MB

$2 ≤ N ≤ 200,000$

$|Ai| ≤ 1,000,000$

### 성능 요약

메모리: 9832 KB, 시간: 48 ms

### 분류

다이나믹 프로그래밍(dp), 누적 합(prefix sum), 볼록 껍질을 이용한 최적화(convex hull optimization)

### comment

$i$번째 있는 수가 $1 ≤ i ≤ N$ 번째 인덱스로 이동할 수 있다고 한다.

단순히 모든 i에 대해 $1 ≤ i ≤ N$을 차례로 돌아 보는 건 당연히 $O(N^2)$에 식 통일도 안되고 최적화 할 껀덕지도 없어 보인다.

$i$를 기점으로 배열을 나눠 왼 쪽, 오른 쪽 인덱스로 이동한다고 생각해보자.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 왼 쪽으로 이동 한다고 할 때.

이동 시 변화를 파악하기 위해 간단한 예를 하나 들겠다.

배열 $a_n$ = { $a_1, a_2, a_3, a_4, a_5$ }가 있을 때

$a_5$가 $a_2$의 위치로 이동 한다고 해보자. 그럼 다음의 변화가 일어남을 관찰할 수 있다.

* $a_2, a_3, a_4$의 인덱스가 하나씩 늘어남에 따라 기존 배열의 특징( $S$ )에 $a_2, a_3, a_4$가 하나씩 더해진다.
* $a_5$가 $a_2$의 위치로 이동함에 따라 인덱스가 그 차이(3)만큼 감소한다. 따라서, 기존 배열의 특징에 $a_5$가 3번 빼진다.

이때 배열의 길이가 최대 $2 * 1e5$이므로 첫번째 변화의 변화량을 일일히 계산할 순 없는 노릇이다. 누적 합( $P[]$ )을 바로 도입하자.

결국 이를 일반화 하면, $1 ≤ j ≤ i$의 범위에서 $i$가 $j$의 위치로 이동할 때

$S + P[i - 1] - P[j - 1] - (i - j) * a_i$

로 정리할 수 있다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 오른 쪽으로 이동 한다고 할 때.

똑같이 위의 예시에서, 반대로 $a_2$가 $a_5$의 위치로 이동 한다고 해보자. 그럼 다음의 변화가 일어남을 관찰할 수 있다.

* $a_3, a_4, a_5$의 인덱스가 하나씩 감소함에 따라 기존 배열의 특징( $S$ )에 $a_3, a_4, a_5$가 하나씩 빼진다.
* $a_2$가 $a_5$의 위치로 이동함에 따라 인덱스가 그 차이(3)만큼 증가한다. 따라서, 기존 배열의 특징에 $a_2$가 3번 더해진다.

이역시 일반화를 하면, $i ≤ j ≤ n$의 범위에서 $i$가 $j$의 위치로 이동할 때

$S - (P[j] - P[i]) + (j - i) * a_i = S + P[i] - P[j] + (j - i) * a_i$

로 정리할 수 있다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

드디어 익숙한 형태의 식으로 정리되었다.

각각 상수를 제외하고 직선의 방정식으로 표현하면 $a_i$를 $x$라 할 때

$1 ≤ j ≤ i$ -> $f_1(x) = j * x - P[j - 1] + P[i - 1]$

$i ≤ j ≤ n$ -> $f_2(x) = j * x - P[j] + P[i]$

가 되겠다.

최종적으로 교점 및 함숫값에 대해 이분 탐색을 적용해 $O(N log N)$으로 문제를 해결할 수 있다.

#### 오른 쪽을 보기 위해 $i == n$부터 내려올 때 함수 기울기 관리에 주의하자.
