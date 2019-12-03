---
title:  "test"
excerpt: "이것은 테스트 중입니다."

toc: true
toc_sticky: true
toc_label: "페이지 보유주라"

categories:
  - Blog
tags:
  - Blog

last_modified_at: 2019-12-03T17:05:00-05:00
---

GitHub Blog 서비스인 github.io 블로그 시작하기로 했다.
GitHub Blog 서비스의 이름은 Pages이다.

Pages가 다른 블로그 플랫폼 보다 편한 것 같아서 마음에 든다.
다른 사람들도 같이 많이 사용했으면 좋겠다는 생각이 든다.

YFM에서 정의한 제목을 이중 괄호 구문으로 본문에 추가할 수 있다.
이 글의 제목은 {{ page.title }}이고
마지막으로 수정된 시간은 {{ page.last_modified_at }}이다

# 기본적인 마크다운 사용법  
## 기본적인 텍스트 표기 방식
```  
기본적인 텍스트 표기 방식이다.
마크다운은 줄바꿈을 인식하지 않는다.

줄바꿈을 하기 위해서는 라인 끝에 스페이스를 2번  
표기해야 한다.

여러가지 강조 표시가 존재한다. 첫번째로 *single asterisks*,
두번째로 _single underscores_, 세번째로 **double asterisks**,
네번째로 __double underscores__, 다섯번째로 ~~cancelline~~가 있다. 

```
기본적인 텍스트 표기 방식이다.
마크다운은 줄바꿈을 인식하지 않는다.

줄바꿈을 하기 위해서는 라인 끝에 스페이스를 2번  
표기해야 한다.

여러가지 강조 표시가 존재한다. 첫번째로 *single asterisks*,
두번째로 _single underscores_, 세번째로 **double asterisks**,
네번째로 __double underscores__, 다섯번째로 ~~cancelline~~가 있다.


## 글머리 달기
``` 
# 의 갯수가 많을수록 글씨가 작아짐
###### 차이를 비교

```
# 의 갯수가 많을수록 글씨가 작아짐
###### 차이를 비교


## 인용
```
> 인용문 사용시
>> 중복사용시 단계별 깊이를 지원
>>> 쉽죠잉
```
> 인용문 사용시
>> 중복사용시 단계별 깊이를 지원
>>> 쉽죠잉


## 정렬 목록
```  
1. 봄
2. 여름
3. 가을
4. 겨울
```
1. 봄
2. 여름
3. 가을
4. 겨울


## 비정렬 목록 
*,+,- 를 사용하며  
```
- 이렇게
  - 띄어쓰기 두번만
    - 하면 되는듯
```
- 이렇게
  - 띄어쓰기 두번만
    - 하면 되는듯

## 코드인용 ``` or ~~~
~~~
```c
int main() {
    printf("Hello");
}  
```
~~~

```c
int main() {
printf("Hello");
}
```

## 수평선
```
 * * *
 ***
 *****
 - - -
 ------------
```
- - -

##링크
```
- 링크 표시법 : [Title](link)
[Google 페이지 링크](https://google.com)

```
[Google 페이지 링크](https://google.com)

*  주소 직접 표시법  

```
<https://google.com>
```
<https://google.com>

##이미지 삽입
```
![](https://devinlife.com/assets/images/bio-photo-keyboard-small.jpg)
```
![](https://devinlife.com/assets/images/bio-photo-keyboard-small.jpg)

```
![](https://devinlife.com/assets/images/bio-photo-keyboard-small.jpg){: .align-center}
```
![](https://devinlife.com/assets/images/bio-photo-keyboard-small.jpg){: .align-center}

```
![키보드 사진](https://devinlife.com/assets/images/bio-photo-keyboard-small.jpg "내 키보드 사진"){: .align-center}
```
![키보드 사진](https://devinlife.com/assets/images/bio-photo-keyboard-small.jpg "내 키보드 사진"){: .align-center}

## 표 만들기
*  표 내용 중앙 정렬
```
| 항목  | 가  격 | 개 수 |
|:-----:|:------:|:------|
| 라 면 | 800 원 | 10 개 |
| 과 자 | 900 원 | 20 개 |
```

| 항목  | 가  격 | 개 수 |
|:--------------:|:----------------:|:-----------------|
| 라 면 | 800 원 | 10 개 |
| 과 자 | 900 원 | 20 개 |

*  표 내용 좌측 정렬-중앙 정렬-우측 정렬
```
| 항목 | 가격 | 개수 |  
|:------|:------:|------:|  
| 라면 | 800원 | 10개 |  
| 과자 | 900원 | 20개 |  
```

| 항목 | 가격 | 개수 |
|:---------------|:----------------:|------------------:|
| 라면 | 800원 | 10개 |
| 과자 | 900원 | 20개 |

마무리~ \n을 잘 사용해야 결과값이 잘 나온다.

