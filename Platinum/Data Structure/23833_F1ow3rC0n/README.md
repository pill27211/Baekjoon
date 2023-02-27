# [Platinum IV] F1ow3rC0n - 23833

[문제 링크](https://www.acmicpc.net/problem/23833)

### 문제 요약

<p> $Q$일 동안 꽃잎을 나무에 붙이려고 한다. 각 날마다 취하는 행동이 주어질 때, $1$번 쿼리들에 대해 구매해야 하는 본드의 최소 개수를 출력해보자. </p>

### 제한

TL : 1sec, ML : 256 MB

$1 ≤ N, Q ≤ 100,000$

$1 ≤ K_i ≤ 100$

### 성능 요약

메모리: 2800 KB, 시간: 40 ms

### 분류

자료구조(data_structures), 세그먼트 트리(segment tree)

### comment

2번 쿼리를 보자. 또, 꽃잎을 붙이는 규칙을 떠올려보자.

그럼 $i$번째 나무에 핀 꽃의 종류 번호가 $K_i$로 바뀐다고 할 때, 다음의 변화를 주목해야 한다.

* $i - 1$번째 나무에 핀 꽃의 종류가 $i$번째 나무에 핀 꽃의 종류와 달랐는데, $K_i$로 바뀜으로써 같아졌다. (본드 수 - 1)
* $i - 1$번째 나무에 핀 꽃의 종류가 $i$번째 나무에 핀 꽃의 종류와 같았는데, $K_i$로 바뀜으로써 달라졌다. (본드 수 + 1)
* $i + 1$번째 나무에 핀 꽃의 종류가 $i$번째 나무에 핀 꽃의 종류와 달랐는데, $K_i$로 바뀜으로써 같아졌다. (본드 수 - 1)
* $i + 1$번째 나무에 핀 꽃의 종류가 $i$번째 나무에 핀 꽃의 종류와 같았는데, $K_i$로 바뀜으로써 달라졌다. (본드 수 + 1)

그렇다. 이것은 바로 본드 수에 대한 점단위 업데이트 쿼리와 합쿼리로 구성된 세그먼트 트리 문제로 해결할 수 있게 된다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

우선 입력 받으면서 최초의 꽃 상태를 세그먼트 트리 상에 모두 올려주자.

이땐, 문제 규칙에 따라 $i$번째 꽃의 종류와 $i - 1$번째 꽃의 종류를 비교하며 다르다면 + 1, 같다면 0의 상태로 올려주자.

2번 쿼리에 대해선 위에서의 변화를 주의하며 처리하면 된다.

1번 쿼리에서도 하나 놓치기 쉬운 점이 있는데, 매일마다 최초 꽃에 대한 본드는 반드시 구매해야 된다는 것이다.

처음 문제를 읽으면서 분명 생각했는데.. 의외로 구현 하면서 놓쳐서 틀렸었다.

디버깅에 쓴 케이스를 해당 문제 게시판에 게시해 뒀으니 참고하자.