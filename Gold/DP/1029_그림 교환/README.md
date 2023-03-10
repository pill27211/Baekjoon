
# [Gold I] 그림 교환 - 1029

[문제 링크](https://www.acmicpc.net/problem/1029)

### 문제 요약

<p> 문제의 거래 조건을 따를 때, 그림을 소유할 수 있는 사람 수의 최댓값을 찾아보자. </p>

### 제한

TL : 2sec, ML : 128 MB

2 ≤ N ≤ 15

0 ≤ w ≤ 9

### 성능 요약

메모리: 21220 KB, 시간: 20 ms

### 분류

다이나믹 프로그래밍(dp), 비트마스킹(bitmask), 비트필드를 이용한 다이나믹 프로그래밍(dp_bitfield)

### comment

문제의 거래 조건을 보면 구매 가격이 항상 단조 증가 해야 한다.

즉, 마지막으로 구매된 가격에 따라 메모이제이션이 달라져야 하므로 기본 비트dp에 3차원 dp를 생각해볼 수 있다.

dp[i][j][k] : 마지막으로 구매된 그림의 가격이 j원이고, i번 예술가가 k번 예술가에게 그림을 팔았을 경우의 최댓값.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

4개의 파라미터(p : 현재 예술가, q : 지금까지 구매된 정보, o : 마지막으로 구매된 그림의 가격, c : 지금까지 그림을 소유했던 사람의 수)를 들고 탑다운 dp를 진행해보자.

p에서 뻗어지는 0 ~ n에 대해 호출될 조건은 당연히 p_i가 o보다 같거나 커야 하며, q의 비트 상태에 (1 << i)가 포함되어 있지 않아야 한다.

그렇게 뻗어지다 모든 예술가들이 q에 포함되거나 o보다 큰 그림의 가격이 없는 호출이 온다면, 이때의 c를 반환해주면 된다.

처음엔 함수 윗부분에 기저 조건을 잡아줬지만 생각해보니 굳이 필요치않음을 깨닫고 최종 리턴식에서 합쳐 주었다.
