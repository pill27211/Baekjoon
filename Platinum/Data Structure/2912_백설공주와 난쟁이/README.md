# [Platinum II] 백설공주와 난쟁이 - 2912

[문제 링크](https://www.acmicpc.net/problem/2912)

### 문제 요약

<p> 길이가 N인 수열과 Q개의 구간 단위 쿼리가 주어진다. 이때 각 쿼리에 대해 해당 쿼리의 구간 길이 / 2 보다 많이 등장하는 수가 있는지 판단해보자. </p>

### 제한

TL : 1sec, ML : 256 MB

3 ≤ N ≤ 300,000

1 ≤ Q, C ≤ 1,000,000,000

1 ≤ A ≤ B ≤ N

### 성능 요약

메모리: 3404 KB, 시간: 208 ms

### 분류

자료 구조(data structure), 세그먼트 트리(segtree), 오프라인 쿼리(offline query), mo's(mo's algorithm), 무작위화(randomization)

### comment

mo's 기본 예제급 문제다.

구간 단위 변화를 카운트 배열에 기록해주며 이 카운트 배열에서 현재 보는 구간의 길이(e - s + 1)보다 큰 값이 있는지 찾아주고.. 그러면 간단하게 해결된다.

이외에도 세그먼트 트리, 머지 소트 트리 등 다양한 방식의 풀이가 존재한다.

근데 갑자기 웬 무작위화??

생뚱맞는 태그가 있길래 생각을 좀 해봐도 무작위성이 문제에 대체 어떻게 적용 되는건지 감도 안잡혔다. 

톡방의 고인물분들에게 간략한 방식 설명을 들었는데 고일데로 고인 사람들의 영역이었다. (내가 경험해 본 유형이 아닌 것도 한 몫)

대체 이런 발상들은 어찌 하는거지 하하..
