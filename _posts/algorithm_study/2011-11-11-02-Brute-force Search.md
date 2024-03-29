---

title: "02_완전 탐색(Brute-force Search)"  
excerpt: "완전탐색, 브루트포스(Brute-force)"  
toc: true  
toc_sticky: true  
toc_label: ""  
categories:  
 - algorithm_study  
tags:  
 - study
 - cpp
 - algorithm

last_modified_at: 2021-12-05
---

## 완전 탐색(Brute-force Search)

- - -

### 완전 탐색이란

모든 문제를 푸는 데 있어서 가장 쉽고 간단한 방법이다.  
간단히 말하자면 가능한 경우를 일일이 다 탐색하는 방법이다.  
절대 틀릴 일은 없는 강력한 방식이지만, 시간은 당연히 최대로 들어간다.

### 해석
하나씩 전부 확인하는 문제들. 
단, 시간 계산을 잘 해야한다.

### 완전 탐색 예제

```cpp
#include<cstdio>
#include<algorithm>

using namespace std;

int main(){
    int N, arr[1000];
    scanf("%d", &N);
    for(int i=0; i<N; i++)
        scanf("%d", arr+i);
    int result = 0;
    for(int i=0; i<N; i++)
        for(int j=0; j<N; j++)
            if(i!=j) result = max(result, arr[i]+arr[j]);
    printf("%d\n", result);
}

```

간단한 예시로 이런 코드가 있다. 이 코드의 내용은 `N개의 수를 입력 받은 후, 서로 다른 2개를 더해서 나올 수 있는 합 중 가장 큰 값을 구하는 코드`이다.  
여기서 2중 반복문을 사용하면서 모든 경우의 수를 시도하고 있으며, 시간 복잡도는 O(n^2) 이 된다.  

***다만, 문제는 N의 값이 작다면 빠르게 가능하지만, N의 값이 100,000을 넘어가게 되면 빠른 시간내에 푸는것은 불가능 하게 된다.***

이런 문제로 인해 알고리즘 상에서 완전 탐색은 권하지 않는다.  
실제로 위와 같은 문제는 내림 차순 정렬 후, 0번째 인덱스 값과 1번째 인덱스 값을 합하면 결과가 나오기 때문에 위와 같은 풀이로 풀 필요는 없다.  

```cpp
#include <cstdio>
#include <algorithm>
using namespace std;

int main(){
    int N, arr[1000];
    scanf("%d", &N);
    for(int i=0; i<N; i++)
        scanf("%d", arr+i);
    sort(arr, arr+N);
    printf("%d\n", arr[N-1]+arr[N-2]);
}

```

STL의 sort함수를 사용해서 N개 값을 정렬하면, O(NlogN)의 시간 복잡도를 가지게 된다.  

***완전 탐색은 구현도 간단하고 단순하지만, 추천하지 않는 방식이다.***

### 추천 문제

- [2309번: 일곱 난쟁이]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-2309)  
- [2231번: 분해합]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-2231)  
- [3085번: 사탕 게임]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-3085)  
- [10448번: 유레카 이론]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-10448)  
- [2503번: 숫자 야구]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-2503)  
- [1018번: 체스판 다시 칠하기]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-1018)  
- [1182번: 부분집합의 합 (★)]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-1182)  
