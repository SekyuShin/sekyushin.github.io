---

title: "01_복잡도 분석"  
excerpt: "시간 복잡도 공간 복잡도"  
toc: true  
toc_sticky: true  
toc_label: ""  
categories:  
 - algorithm_study  
tags:  
 - study
 - cpp
 - algorithm

last_modified_at: 2019-12-14
---

## 복잡도

- - -
  
복잡도의 종류는 크게 시간복잡도와 공간복잡도가 있다.  
복잡도는 빅오 표기법을 사용하는데, 이는 알고리즘이 최악일때의 경우를 판단하기 때문에 평균과 가까운 성능으로 예측하기 쉽기 때문이다. 


### 시간복잡도  

시간복잡도는 프로그램의 수행시간을 분석하는 것이고 반복문에 크게 영향을 받는다. 즉, 알고리즘의 성능을 설명하는 것이다.
빅오 표기법에서 시간복잡도는 입력된 N의 크기에 따라 실행되는 조작의 수를 나타낸다.  
예를 들면 입력의 크기가 n일 때 주어진 프로그램의 수행시간이 `5n^4-7n^3 ...` 을 가진다면, 최고차항의 계수와 그보다 낮은 차수의 항을 제외시켜 O(n^4)와 같이 표기한다.  
즉, 시간복잡도에서 중요하게 보는 것은 가장 큰 영향을 미치는 n의 단위이다.  

![big_o](https://user-images.githubusercontent.com/42687768/70862731-5d04e480-1f83-11ea-829d-8823fc536a23.jpg)

```t
1             O(1)   --> 상수
2n + 20       O(n)   --> n이 가장 큰영향을 미친다.
3n^2          O(n^2) --> n^2이 가장 큰영향을 미친다.

```

시간 복잡도의 문제해결 단계를 나열하면 아래와 같다.

```t
O(1) – 상수 시간 : 문제를 해결하는데 오직 한 단계만 처리함.
O(log n) – 로그 시간 : 문제를 해결하는데 필요한 단계들이 연산마다 특정 요인에 의해 줄어듬.
O(n) – 직선적 시간 : 문제를 해결하기 위한 단계의 수와 입력값 n이 1:1 관계를 가짐.
O(n log n) : 문제를 해결하기 위한 단계의 수가 N*(log2N) 번만큼의 수행시간을 가진다. (선형로그형)
O(n^2) – 2차 시간 : 문제를 해결하기 위한 단계의 수는 입력값 n의 제곱.
O(C^n) – 지수 시간 : 문제를 해결하기 위한 단계의 수는 주어진 상수값 C 의 n 제곱.
```

예제를 보면

```cpp
// 1. O(log(n))
while(n)
	n/=2;

// 2. O(sqrt(n))
for(int i=0;i*i<=n;i++);

// 3. O(n)
for(int i=0;i<n;i++);

// 4. O(nlog(n))
for(int i=0;i<n;i++)
	for(int j=i;j;j/=2);

// 5. O(nsqrt(n))
for(int i=0;i<n;i++)
	for(int j=0;j*j<=i;j++);

// 6. O(n^2)
for(int i=0;i<n;i++)
	for(int j=0;j<n;j++);

// 7. O(n^3)
for(int i=0;i<n;i++)
	for(int j=0;j<n;j++)
		for(int k=0;k<n;k++);

// 8. O(2^n)
int function(int n){
	if(n==0||n==1)
		return 1;
	return function(n-1)+function(n-2);
}

// 9. O(n!)
// n개의 데이터를 나열하는 방법의 수
void function(int x, vector<int> pick, vector<bool> picked){
	if(x==n){
		for(int i=0;i<pick.size();i++)
			printf("%d\n", pick[i]);
		return;
	}
	for(int i=0;i<n;i++){
		if(picked[i])
			continue;
		pick.push_back(i);
		picked[i]=true;
		function(x+1, pick, picked);
		pick.pop_back();
		picked[i]=false;
	}
	return;
}

```

![complexity_ex](https://user-images.githubusercontent.com/42687768/70862746-7443d200-1f83-11ea-88d2-25ee426298ee.JPG)

위 표는 실행시간이 빠른 순으로 입력 N값에 따른 서로 다른 알고리즘의 시간복잡도이고, 위 코드는 예제 들이다. 이를 정리하면,
`O(1) < O(logn) < O(n) < O(nlogn) < O(n^2) < O(n^3) < O(2^n) < O(n!) ...`  
위의 순서대로 점점 느려진다.  
PS에서 보통 1억을 1초로 잡고 계산한다.  
예를 들면, n이 1000이라면 6번 이하로는 가능한 알고리즘이다.  
알고리즘 문제를 풀 때, 주어진 입력값에 의해서 n의 값을 어림짐작하면 예상 시간을 알 수 있다.  
아주 많은 상황은 식의 계수는 별 쓸모가 없고 적어도 차수를 줄여야 효율이 좋다고 판단한다.

### 공간복잡도

공간복잡도는 프로그램의 메모리 사용량을 분석하는 것이다.  
간단하게 사용한 배열의 크기 *(해당 자료형의 크기) 로 계산한다.  
보통 기타 지역변수나 헤더파일, 함수 등을 생각해서 5~10MB 정도는 여유로 빼고 생각한다. 그러나 공간복잡도 보다 우선순위에서 밀린다. 이유는 메모리는 넉넉해 져가는 반면, 컴퓨터의 연산속도는 메모리 공간만큼 증가하지 않았기 때문이다.
