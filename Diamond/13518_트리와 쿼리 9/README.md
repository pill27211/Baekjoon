
# [Diamond IV] 트리와 쿼리 9 - 13518

[문제 링크](https://www.acmicpc.net/problem/13518)

### 문제 요약

<p> N개의 정점으로 이루어진 트리가 주어진다. Q개의 쿼리에 대해, 각 쿼리에 대한 답을 출력해보자. </p>

### 제한

TL : 2sec, ML : 512 MB

2 ≤ N, Q ≤ 100,000

1 ≤ W ≤ 1,000,000

### 성능 요약

메모리: 27736 KB, 시간: 512 ms

### 분류

트리(trees), 최소 공통 조상(lca), 오일러 경로 테크닉(euler_tour_technique), 오프라인 쿼리(offline_queries), mo's(mo)

### comment

* u v: u에서 v로 가는 경로에 존재하는 서로 다른 정점의 가중치의 개수를 출력한다.

그래 쿼리는 참 단순해 보이는 데.. 과정은 그리 단순하지 않다.

트리를 그려놓고 쿼리에 대한 관찰을 해보자.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

예제를 예시로 들고, 트리를 그려보자.

![image](https://user-images.githubusercontent.com/120912574/214846329-e31e5610-17e2-42ba-a91e-14f1480a5c0e.png)

그럼 대략 위와 같은 모양으로 그려볼 수 있는데, 이때 1부터 ett를 돌려보며 기록 순서를 작성해보면 다음과같이 써볼 수 있다.

1_in[1] -> 2_in[2] -> 3_out[2] -> 4_in[3] -> 5_in[5] -> 6_out[5] -> 7_in[6] -> 8_out[6] -> 9_in[7] -> 10_out[7] -> 11_out[3] -> 12_in[4] -> 13_in[8] -> 14_out[8] -> 15_out[4] -> 16_out[1]

여기서 중요한 관찰을 해볼 수 있는데, 임의의 쿼리에 대한 정점 쌍(p, q)을 생각해보자.

p - q의 경로는 크게 두가지로 나뉜다. (p == LCA(p, q)) || (q == LCA(p, q)) 를 만족하거나, 아니거나.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

전자일 때.

예제에선 전자와같은 쿼리가 없으므로 임의의 쿼리를 생각해보자. Q_1 : {1, 5} 라 하고 이를 위에 써둔 기록에 올려보자.

1_in[1] -> 2_in[2] -> 3_out[2] -> 4_in[3] -> 5_in[5] 가 되며 유일한 경로에 포함되지 않는 정점(2)들은 in[], out[] 에 의해 상쇄되고 결국 경로 상의 정점들만 남게 된다.

똑같이 Q_2 : {4, 8} 에 적용해보면 

12_in[4] -> 13_in[8] 가 되며 경로 상의 정점들만 남게 된다.

즉, ett로 메겨지는 번호에 의해 구간을 짤라낼 수 있으며 (p == LCA(p, q)) || (q == LCA(p, q)) 를 만족하는 모든 쿼리에 대해 (in[p] ~ in[q])의 구간 쿼리로 환원시킬 수 있게 된다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

후자일 때.

위의 트리 예제에서 Q_1 : {2, 5}이며 이를 위에 써둔 기록에 올려보자.

3_out[2] -> 4_in[3] -> 5_in[5] 가 되며 경로 상에 LCA(2, 5)를 제외한 모든 정점들이 등장한다.

똑같이 Q_2 : {7, 8} 에 적용해보면

10_out[7] -> 11_out[3] -> 12_in[4] -> 13_in[8] 가 되며 LCA(7, 8)를 제외한 경로 상에 모든 정점들이 등장한다.
 
즉, ett로 메겨지는 번호에 의해 구간을 짤라낼 수 있으며 !((p == LCA(p, q)) || (q == LCA(p, q))) 를 만족하는 모든 쿼리에 대해

(out[p] ~ in[q]) 의 구간 쿼리로 환원시킬 수 있다. 그리고 추가로 여기에 포함되지 않은 LCA(p, q)를 포함해주는 것이다.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

이때, 위에서의 u, v는 in[u] < in[v] 일 수 있도록 일반성을 유지하도록 하자. 또한 환원된 구간 쿼리는 'ett로 메겨지는 번호'에 대해 수행해야 하는 것이다.

그럼 이제 업데이트가 없는 구간 쿼리 문제가 되었으므로 mo's로 빠르게 처리해줄 수 있다.

각 쿼리를 이루는 정점 쌍에 대해 LCA를 구하여 위에서 나눈 기준에 따라 알맞게 처리하면 된다.

문제의 쿼리를 수행하기 위해 정점의 수를 카운트할 배열, 가중치를 카운트할 배열 각각을 만들어주고 구간의 변화에 맞게 쿼리에 대한 답을 뽑아내주자.

이 문제를 풀 정도면 오프라인 처리를 어렵지 않게 해낼 수 있을테니 간단히만 설명해 보겠다.

* 어떤 정점이 구간에 포함될 때

-> 포함되는 순간 해당 정점이 유일하면서(= 카운트가 1) 가중치 또한 유일하다면 t++. 또는 해당 정점이 유일하지 않게 되면서(= 카운트가 2) 유일한 가중치가 사라졌다면 t--.

* 어떤 정점이 구간에서 빠질 때

-> 빠지는 순간 해당 정점이 유일하게 되면서(= 카운트가 1) 가중치 또한 유일하게 됐다면 t++. 또는 유일했던 해당 정점이 빠지면서(= 카운트가 0) 유일했던 가중치도 사라졌다면 t--.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

LCA와 mo's가 엮인 재밌는 문제였다. (처음 마주하는 유형)

이렇게 쓰고 보니 참 간단해 보이는데.. 

![image](https://user-images.githubusercontent.com/120912574/214867097-692c3261-f54a-4115-817a-b4e0abcd0704.png)

AC로의 길은 꽤 험난했던 걸로...

