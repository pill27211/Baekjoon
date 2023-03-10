
# [Gold II] 피보나치 수 6 - 11444

[문제 링크](https://www.acmicpc.net/problem/11444)

### 문제 요약

<p> n번째 피보나치 수를 1,000,000으로 나눈 나머지 값을 구해보자. </p>

### 제한

TL : 1sec, ML : 256 MB

1 ≤ n ≤ 1,000,000,000,000,000,000

### 성능 요약

메모리: 2024 KB, 시간: 0 ms

### 분류

수학(math), 분할 정복을 이용한 거듭제곱(exponentiation_by_squaring)

### comment

이 문제 역시 [여기](https://github.com/pill27211/Baekjoon/tree/main/Gold/Math/2749_%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98%20%EC%88%98%203)서 다룬 내용과 같다.

딱 하나 차이점이 존재하는데, 모듈러가 1e6에서 1e9 + 7로 바뀌었다.

피사노 주기를 써먹기가 사실상 불가능 해 귀찮은 행렬 제곱을 이용해야 하나 싶지만,, 사실 다른 굉장히 강력한 방법이 존재한다.

바로 도가뉴 항등식(d'Ocagne's identity)이라는 것인데, [여기](https://ko.wikipedia.org/wiki/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98_%EC%88%98)를 포함해
인터넷에 많은 자료들이 있으니 증명 및 유도 과정을 참고하자.

당연히 범위만큼 정적 배열을 생성할 수는 없으므로, 이럴 때 안성맞춤인 map자료구조를 애용하자.

식을 적절히 정리해 코드로 작성해주면 끝.
