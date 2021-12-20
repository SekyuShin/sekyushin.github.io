---

title: "BOJ_INPUTOUTPUT"  
excerpt: "입출력 문제"  
toc: true  
toc_sticky: true  
toc_label: ""  
categories:  
 - algorithm_solving  
tags:  
 - solving  
 - cpp  
 - algorithm
last_modified_at: 2021-12-19

---



입출력 문제 풀이들

# 1. 문제풀이 [Hello World] (2557)
Issue : <https://www.acmicpc.net/problem/2557>
## 1) 문제 조건
    - Hello World! 출력

# 2. 코드 (2557)
```c
#include<cstdio>

int main() {
    printf("Hello World!\n");
    return 0;
}
```
# 1. 문제풀이 [A+B 1,2] (1000, 2558)
Issue : <https://www.acmicpc.net/problem/1000>

Issue : <https://www.acmicpc.net/problem/2558>

## 1) 문제 조건
    - A+B
    - 0 < A, B < 10

# 2. 코드 (1000, 2558)
```c
#include<cstdio>

int main() {
    int A,B;
    scanf("%d %d",&A,&B);
    printf("%d\n",A+B);
    return 0;
}
```

# 1. 문제풀이 [A+B - 3] (10950)
Issue : <https://www.acmicpc.net/problem/10950>
## 1) 문제 조건
    - 반복 T
    - A+B
    - 0 < A, B < 10

# 2. 코드 (10950)
```c
#include<cstdio>

int main() {
    int A,B,T;
    scanf("%d", &T);
    for(int i=0;i<T;i++) {
        scanf("%d %d",&A,&B);
        printf("%d\n",A+B);
    }
    
    return 0;
}
```

# 1. 문제풀이 [A+B - 4] (10951)
Issue : <https://www.acmicpc.net/problem/10951>
## 1) 문제 조건
    - 무한반복
    - A+B
    - 0 < A, B < 10

# 2. 코드 (10951)
```c
#include<cstdio>

int main() {
	int A,B;
	for (;;) {
		if(scanf("%d %d", &A, &B) != EOF) printf("%d\n",A+B);
		else break;
	}
	return 0;
}
```
# 3. 리뷰(10951)

  - 문제중, 무한반복문이 나오는데 종료조건을 써주어야 출력초과가 안나온다.
    - scanf("%d %d", &A, &B) != EOF
    - File의 끝이 아니면이란 뜻으로 아마 텍스트를 한번에 넣어서 그 끝을 찾는 시스템인듯 보인다.


# 1. 문제풀이 [A+B - 5] (10952)
Issue : <https://www.acmicpc.net/problem/10952>
## 1) 문제 조건
    - 0 0 이 입력될 때 까지 무한 반복
    - A+B
    - 0 < A, B < 10

# 2. 코드 (10952)
```c
#include<cstdio>

int main() {
	int A,B;
	for (;;) {
		scanf("%d %d", &A, &B);
        if(A!=0 || B!=0) printf("%d\n",A+B);
		else break;
	}
	return 0;
}
```

# 1. 문제풀이 [A+B - 6] (10953)
Issue : <https://www.acmicpc.net/problem/10953>
## 1) 문제 조건
    - 반복횟수 T
    - A+B
    - 0 < A, B < 10
    - A,B입력시 ,로 구분

# 2. 코드 (10953)
```c
#include<cstdio>

int main() {
	int A,B,T;
    scanf("%d",&T);
	for (int i=0;i<T;i++) {
		scanf("%d,%d", &A, &B);
        printf("%d\n",A+B);
		
	}
	return 0;
}
```

# 1. 문제풀이 [A+B - 7] (11021)
Issue : <https://www.acmicpc.net/problem/11021>
## 1) 문제 조건
    - 반복횟수 T
    - A+B
    - 0 < A, B < 10
    - 출력형태 : "Case #x:"

# 2. 코드 (11021)
```c
#include<cstdio>

int main() {
	int A,B,T;
	scanf("%d",&T);
	for (int i=0;i<T;i++) {
		scanf("%d %d", &A, &B);
		printf("Case \#%d: %d\n",i+1,A+B);

	}
	return 0;
}
```

# 1. 문제풀이 [A+B - 8] (11022)
Issue : <https://www.acmicpc.net/problem/11022>
## 1) 문제 조건
    - 반복횟수 T
    - A+B
    - 0 < A, B < 10
    - 출력형태 : "Case #x: A + B = C"

# 2. 코드 (11022)
```c
#include<cstdio>

int main() {
	int A,B,T;
	scanf("%d",&T);
	for (int i=0;i<T;i++) {
		scanf("%d %d", &A, &B);
		printf("Case \#%d: %d + %d = %d\n",i+1,A,B,A+B);

	}
	return 0;
}
```

# 1. 문제풀이 [그대로 출력하기1, 2] (11718, 11719)
Issue : <https://www.acmicpc.net/problem/11718>

Issue : <https://www.acmicpc.net/problem/11719>
## 1) 문제 조건
    - 최대 100줄
    - 소문자, 대문자, 공백, 숫자
    - 최대 100글자
    - 공백 시작 x, 공백 끝 x (11718)
    - 공백 시작 0, 공백 끝 0 (11719)

# 2. 코드 (11718, 11719)
```c
#include<cstdio>

int main() {
	char str[101]; //조건 중, 최대 100글자 문자열 종료문자 포함하여 101
	char c;
	int i = 0;
	while((c=getchar())!=EOF) { //한 글자씩 입력을 받아 EOF가 아니라면 진행
		if (c != '\n') str[i++] = c; //i로 문자열의 위치를 지정하고 해당 문자 저장
		else {
			str[i] = '\0'; //다음줄일 경우, 종료문자를 문자열에 저장후
			printf("%s\n", str);
			i = 0; //i 초기화
		}
	}
	return 0;
}
```
# 3. 리뷰 (11718, 11719)

- 슬슬 제대로된 문제가 나오는 것 같다.
- 문제가 중복되므로 공통되게 풀었다.

# 1. 문제풀이 [숫자의 합] (11720)
Issue : <https://www.acmicpc.net/problem/11720>
## 1) 문제 조건
    - 총 N개의 숫자를 더하기
    - N을 입력받고 해당 수만큼 반복
    - N개의 숫자가 공백없이 쓰여있다.
# 2. 코드 (11720)
```c
#include<cstdio>

int main() {
	int N;
	char c;
	int result = 0;
	scanf("%d", &N);
	while (getchar() != '\n'); 
    //여기서 입력버퍼를 지워주지 않으면, c에 \n이 들어간다. 이 부분은 문자 입력시 무조건 주의해야하는 상황
    //fflush(stdin)은 gcc에서 돌아가지 않는다.
	for(int i=0;i<N;i++){
		c = getchar(); //문자를 한개 입력받고
		result += (c - '0'); //해당 문자의 숫자를 읽어준다.
	}
	printf("%d\n", result);
	return 0;
}
```

# 3. 리뷰 (11720)

    - 입력버퍼를 지워주지 않아 이상한 값이 계속 출력되었다. 문자를 입력받을때는
    늘 주의가 필요하다.


# 1. 문제풀이 [열 개씩 끊어 출력하기] (11721)
Issue : <https://www.acmicpc.net/problem/11721>
## 1) 문제 조건
    - 길이가 N인 단어중, 10개씩 끊어서 출력
    - 길이는 100을 넘지 않는다.
    - 길이가 0인 단어는 주어지지 않는다.
# 2. 코드 (11721)
```c
#include<cstdio>
int main() {
	char c;
	int i=0;
	while ((c=getchar())!='\n') {
		if(i++<10) printf("%c", c);
		else {
			i = 1;
			printf("\n%c",c);
		}
	}
	return 0;
}
```
# 3. 리뷰(11721)
    - 버퍼를 사용해서 저장해도 되겠지만, 그냥 출력하고 카운트를 따로 하는 방법을
    사용했다. 조건문에서 i++로 증감식을 넣었기에 초기화시에 0으로 해주었다.


# 1. 문제풀이 [N직기] (2741)
Issue : <https://www.acmicpc.net/problem/2741>
## 1) 문제 조건
    - 자연수 N을 입력하고 해당 자연수'까지' 한줄에 하나씩 출력
    - N은 100,000보다 작거나 같은수
# 2. 코드 (2741)
```c
#include<cstdio>
int main() {
	int N;
	scanf("%d", &N);
	for (int i = 0; i < N; i++) {
		printf("%d\n", i + 1);
	}
	return 0;
}
```

# 1. 문제풀이 [기찍N] (2742)
Issue : <https://www.acmicpc.net/problem/2742>
## 1) 문제 조건
    - 자연수 N을 입력하고 해당 자연수'부터' 한줄에 하나씩 출력
    - N은 100,000보다 작거나 같은수
# 2. 코드 (2742)
```c
#include<cstdio>
int main() {
	int N;
	scanf("%d", &N);
	for (int i = N; i > 0; i--) {
		printf("%d\n", i);
	}
	return 0;
}
```


# 1. 문제풀이 [구구단] (2739)
Issue : <https://www.acmicpc.net/problem/2739>
## 1) 문제 조건
    - N을 입력받고 해당하는 구구단 출력
    - N은 1보다 크거나 같고, 9보다 작거나 같다.
    - 출력 형태 : A * B = C
# 2. 코드 (2739)
```c
#include<cstdio>
int main() {
	int N;
	scanf("%d", &N);
	for (int i = 1; i < 10; i++) {
		printf("%d * %d = %d\n",N, i,N*i);
	}
	return 0;
}
```


# 1. 문제풀이 [2007년] (1924) 
Issue : <https://www.acmicpc.net/problem/1924>
## 1) 문제 조건
    - x월 y일의 요일 구하기
    - 요일에 따라 SUN, MON, TUE, WED, THU, FRI, SAT 중 출력
# 2. 코드 (1924)
```c
#include<cstdio>

int main() {
	int month, day;
	int month_num[] = {31,28,31,30,31,30,31,31,30,31,30,31};
	int tmp_sum = 0; 
    //1월 1일부터 시작하기에 -1부터 시작하나, 1월 1일의 요일이 MON이기에 1을 더한 값을 시작값으로 지정 (-1+1 = 0)
	const char *weeks[] = { "SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT" };
	scanf("%d %d", &month,&day);
	for (int i = 0; i < month-1; i++) {
		tmp_sum += month_num[i];
	}
	tmp_sum = (tmp_sum+day)%7;
	printf("%s\n", weeks[tmp_sum]);

	return 0;
}
```
# 3. 리뷰(1924)

    - 우선 해당 Month의 날짜 개수를 배열로 저장하고, 해당 날짜 전달까지의 날짜 개수를 구할 수 있도록하였다. 그리고 Day를 더해주어 총 날짜 개수를 구해주었다.
    - 그리고 해당 날짜 개수를 7로 나눈 나머지를 구해주어서 요일을 구하도록했다.
    이때, 요일은 weeks[]의 배열로 선언하였다.

    - 주의사항으로는 tmp_sum의 시작값이다. 날짜의 개수를 구해서 7로 나눈 나머지를 구하는 방법이라, 시작값이 중요하다. 그리고 해당 문제의 경우 weeks[1]인 MON부터 시작하고 1월 1일을 입력하면 날짜의 개수가 1부터 시작한다. 때문에 날짜의 개수가 0부터 시작할 수 있도록 -1을 해주고 MON이 해당하는 인덱스인 1을 더해주면 0부터 시작하는 시작값이 나온다.



# 1. 문제풀이 [합] (8393) 
Issue : <https://www.acmicpc.net/problem/8393>
## 1) 문제 조건
    - 입력값 N에 대해 1부터 N까지의 합구하기
    - N은 1보다 크거나 같고, 10,000보다 작거나 같다.
# 2. 코드 (8393)
```c
#include<cstdio>

int main() {
	int n;
	int sum = 0;
	scanf("%d", &n);
	for (int i = 1; i < n + 1; i++) {
		sum += i;
	}
	printf("%d\n", sum);
	return 0;
}
```
```c
#include<cstdio>

int main() {
	int n;
	int sum = 0;
	scanf("%d", &n);
	sum = (n*(n + 1)) / 2;
	printf("%d\n", sum);
	return 0;
}
```
# 3. 리뷰 (8393)
    - 두 가지로 풀어보았다. 완전탐색과 공식을 사용한 방법. 시간차이는 별로 나오지 않으나 n의 크기가 커진다면 공식이 훨씬 나을 것으로 예상한다.




# 1. 문제풀이 [최소,최대] (10818) 
Issue : <https://www.acmicpc.net/problem/10818>
## 1) 문제 조건
    - 정수의 개수 N  (1 ≤ N ≤ 1,000,000)
    - 정수 범위는 -1,000,000보다 크거나 같고, 1,000,000보다 작거나 같다
# 2. 코드 (10818)
```c
#include<cstdio>
int main() {
	int n;
	int max = -1000000; //조건 : 최솟값이 -1천만
	int min = 1000000; // 조건 : 최댓값이 1천만
	int tmp;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		scanf("%d", &tmp);
		if (tmp > max) max = tmp;
		if (tmp < min) min = tmp;
	}
	printf("%d %d\n", min, max);
	return 0;
}
```






# 1. 문제풀이 [별 찍기 - 1] (2438) 
Issue : <https://www.acmicpc.net/problem/2438>
## 1) 문제 조건
    - 줄의 개수 N (1 ≤ N ≤ 100)
    - 출력 형태는 N번째 줄까지 *을 출력하는데 왼쪽 정렬인 상태로 출력한다.
# 2. 코드 (2438)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < i+1; j++) { //j의 조건식이 중요하다.
			printf("*");
		}printf("\n");
	}
	return 0;
}
```




# 1. 문제풀이 [별 찍기 - 2] (2439) 
Issue : <https://www.acmicpc.net/problem/2439>
## 1) 문제 조건
    - 줄의 개수 N (1 ≤ N ≤ 100)
    - 출력 형태는 N번째 줄까지 *을 출력하는데 오른쪽 정렬인 상태로 출력한다.
# 2. 코드 (2439)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n; j++) {
			if(j>= n-i-1) printf("*"); //조건식이 중요
			else printf(" ");
		}printf("\n");
	}
	return 0;
}
```




# 1. 문제풀이 [별 찍기 - 3] (2440) 
Issue : <https://www.acmicpc.net/problem/2440>
## 1) 문제 조건
    - 줄의 개수 N (1 ≤ N ≤ 100)
    - 출력 형태는 N번째 줄까지 *을 출력하는데 왼쪽 정렬이고 역순으로 출력
# 2. 코드 (2440)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n-i; j++) {//j의 조건식이 중요하다.
			printf("*");
		}printf("\n");
	}
	return 0;
}
```




# 1. 문제풀이 [별 찍기 - 4] (2441) 
Issue : <https://www.acmicpc.net/problem/2441>
## 1) 문제 조건
    - 줄의 개수 N (1 ≤ N ≤ 100)
    - 출력 형태는 N번째 줄까지 *을 출력하는데 오른쪽 정렬이고 역순으로 출력
# 2. 코드 (2441)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n; j++) {
			if(j>= i) printf("*"); //조건식이 중요
			else printf(" ");
		}printf("\n");
	}
	return 0;
}
```




# 1. 문제풀이 [별 찍기 - 5] (2442) 
Issue : <https://www.acmicpc.net/problem/2442>
## 1) 문제 조건
    - 줄의 개수 N (1 ≤ N ≤ 100)
    - 출력 형태는 N번째 줄까지 *을 출력하는데 가운데 기준 대칭
    - N번째 줄에는 별 2×N-1개
# 2. 코드 (2442)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < 2*n-1; j++) { // 2×N-1의 별이 필요하기 때문에
			if(j<n-i-1) printf(" "); //n을 기준으로 i번째 만큼의 별이 필요하다.
			else if (j > n + i - 1) break; //이걸 안해주면 출력형식 이상이 뜬다.
			else printf("*");
		}printf("\n");
	}
	return 0;
}
```



# 1. 문제풀이 [별 찍기 - 8] (2445) 
Issue : <https://www.acmicpc.net/problem/2445>
## 1) 문제 조건
    - 줄의 개수 N (1 ≤ N ≤ 100)
    - 예제보고 같게 출력
```cpp
*        *
**      **
***    ***
****  ****
**********
****  ****
***    ***
**      **
*        *
```

    - 즉 가로(10) 세로 (9)
# 2. 코드 (2445)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < 2*n-1; i++) {
		for (int j = 0; j < 2*n; j++) {
			if (i < n) { //위 아래를 나누어야 하기에 조건문 추가
				if(j<i+1 || j>2*n-i-2) printf("*");
				else printf(" ");
			} else {
				if(j<2*n-i-1 || j>i) printf("*");
				else printf(" ");
			}
			
		}printf("\n");
	}
	return 0;
}
```

# 3. 리뷰 (2445)

    - 궁금해져서 다른 사람들은 어찌 풀까 봤더니 조건식을 한 개로 해놨다.
    printf((2 * i - 2 * j + 1)*(2 * i + 2 * j - 4 * n + 3)<0 ? "*" : " ");
    해석할까 하다가 굳이라는 생각이 들었다.
    나중에..


	

# 1. 문제풀이 [별 찍기 - 12] (2522) 
Issue : <https://www.acmicpc.net/problem/2522>
## 1) 문제 조건
    - N (1 ≤ N ≤ 100)
    - 예제보고 같게 출력
```cpp
  *
 **
***
 **
  *
```

    - 줄의 개수 : 2×N-1번째 줄까지
# 2. 코드 (2522)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < 2*n-1; i++) {
		for (int j = 0; j < n; j++) {	
			if ((i<n && j > n - i - 2) || ((i>n-1) && j>i-n)) printf("*");
			//i의 값이 n을 기준으로 조건을 달리해서 풀이 진행
			else printf(" ");
		}printf("\n");
	}
	return 0;
}
```



# 1. 문제풀이 [별 찍기 - 9] (2446) 
Issue : <https://www.acmicpc.net/problem/2522>
## 1) 문제 조건
    - N (1 ≤ N ≤ 100)
    - 예제보고 같게 출력
```cpp
*********
 *******
  *****
   ***
    *
   ***
  *****
 *******
*********
```

    - 줄의 개수 : 2×N-1번째 줄까지
# 2. 코드 (2446)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < 2*n-1; i++) {
		for (int j = 0; j < 2*n-1; j++) {	
			if ((i < n && (j > i - 1 && j < 2 * n - i - 1)) || ((i > n - 1) && (j > 2 * n - i - 3 && j < i + 1))) printf("*");
			else if (j > n-1) continue;
			else printf(" ");
		}printf("\n");
	}
	return 0;
}

```

# 3. 리뷰 (2446)

	- 뭔가 점점 규칙을 대충 찾고 숫자 몇개를 바꾸어 때려 맞추는 기분이 든다..




# 1. 문제풀이 [별 찍기 - 16] (10991) 
Issue : <https://www.acmicpc.net/problem/10991>
## 1) 문제 조건
    - N (1 ≤ N ≤ 100)
    - 예제보고 같게 출력
```cpp
   *
  * *
 * * *
* * * *
```

    - 줄의 개수 : N
# 2. 코드 (10991)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n+i; j++) {	
			if (j > n - i - 2  && ((n%2 == 1 && i%2 == j%2) || (n%2 == 0 && i%2 != j%2))) printf("*");
			else  printf(" ");
		}printf("\n");
	}
	return 0;
}

```



# 1. 문제풀이 [별 찍기 - 17] (10992) 
Issue : <https://www.acmicpc.net/problem/10992>
## 1) 문제 조건
    - N (1 ≤ N ≤ 100)
    - 예제보고 같게 출력
```cpp
   *
  * *
 *   *
*******
```

    - 줄의 개수 : N
# 2. 코드 (10992)
```c
#include<cstdio>
int main() {
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n+i; j++) {	
			if (j == n - i - 1 || j==n+i-1 || i==n-1) printf("*");
			else  printf(" ");
		}printf("\n");
	}
	return 0;
}

```

# 2. 리뷰 (10992)

	- 드디어 별 문제 끝..
	어렵지는 않았으나 규칙을 도추해 내는게 생각보다 성가신 작업이었다.