
# [Platinum IV] 터보소트 - 3006

[문제 링크](https://www.acmicpc.net/problem/3006)

### 문제 요약

<p> 문제에서 정의된 터보소트의 규칙을 따를 때, 주어지는 각 단계에서의 스왑 횟수를 구해보자. </p>

### 제한

TL : 1sec, ML : 128 MB

$1 ≤ N ≤ 100,000$

### 성능 요약

메모리: 2800 KB, 시간: 24 ms

### 분류

자료구조(data_structures), 세그먼트 트리(segtree)

### comment

어떤 수가 등장하는 인덱스와 함께 문제의 규칙을 따라가보면 어렵지 않게 일반화를 시킬 수 있다. (홀수 / 짝수)

* 우선 1 ~ N의 모든 수를 세그먼트 트리 상에 올린다.
* $1 ≤ i ≤ N$ 에 대해 i가 등장한 인덱스를 c[i]라 하자.
* i가 홀수일 때는 결국 세그먼트 트리 상에 c[i]보다 작은 수들만큼 스왑이 발생한다.
* i가 짝수일 때는 결국 세그먼트 트리 상에 c[i]보다 큰 수들만큼 스왑이 발생한다.

이때, i에 대한 정렬이 끝났다면 i는 최 좌측 / 최 우측 으로 빠졌다고 볼 수 있으므로 세그먼트 트리 상에서 수를 내린다.

또한 이 최 좌측 / 최 우측 으로 빠진 수들은 봐야하는 구간에서도 제외 되어야 하므로 양 끝에서 점점 좁혀오는 포인터 변수 $p, q$를 두어 양 끝 범위를 관리하자.
