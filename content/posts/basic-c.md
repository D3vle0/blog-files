---
title: "C언어 기초"
date: 2021-01-24T00:48:37+09:00
draft: false
---
## 기본 입출력

```c
#include <stdio.h>
int main() {
	printf("Hello, World!\n");
	
	return 0;
}
```
| 제어문자 | 의미 |
|--|--|
| `\n` | 개행 |
|`\t` | 수평 탭|
| `\'`| 작은 따옴표|
|`\"` |큰 따옴표 |

| 서식 지정자 | 의미 |
|--|--|
| `%d` | 부호 있는 10진 정수 |
|`%u` |부호 없는 10진 정수 |
|`%c` |단일 문자 |
| `%s`|문자열 |
|`%f` | 부호 있는 10진 실수|
```c
#include <stdio.h>
int main() {
	double a=3.1415926;
	printf("%5.3f", a);
}
```

5개의 칸에서 오른쪽으로 정렬, 소수점 4번째 자리에서 반올림

```c
#include <stdio.h>
int main() {
	int a;
	scanf("%d", &a);
	printf("%d", a);
}
```

입력 함수 `scanf()`

## if

```c
#include <stdio.h>
int main() {
	int a;
	scanf("%d", &a);
	if (a==1)
		printf("hello");
}

```
```c
#include <stdio.h>
int main() {
	int a;
	scanf("%d", &a);
	if (a==1)
		printf("hello");
	else (a==2)
		printf("world");
	else
		printf("c language is fun");
}
```

if ~ else if ~ else 형태로 사용 가능

```c
a==1?printf("hello"):printf("world");
```

삼항연산자는 `조건 ? 참일때 : 거짓일때;` 형태로 사용 가능
| 논리 연산자 | 의미 |
|--|--|
| `A && B` | A,B 모두 만족하면 참 |
|`A || B` | A,B 중 적어도 하나 만족하면 참| 
|`!A` | 참/거짓을 뒤집음|
## switch ~ case

```c
#include <stdio.h>
int main() {
    int score;
    scanf("%d", &score);
    switch (score/10) {
        case 10:
        case 9: printf("A"); break;
        case 8: printf("B"); break;
        case 7: printf("C"); break;
        case 6: printf("D"); break;
        default: printf("F"); break;
    }
}
```

**각각의 case 에 대해 break 를 걸어주지 않으면 다음 조건에 해당하는 명령이 실행된다.**

## while

```c
#include <stdio.h>
int main() {
    int a, i=2, cnt=0;
    scanf("%d", &a);
    while (i<a){
        if (a%i==0)
            cnt++;
        i++;
    }
    printf("%s", cnt?"composite":"prime");
}
```

`while (조건) { 반복할 명령 }` 형태로 사용 가능

## do~while

`do { 반복할 명령 } while (조건);` 형태로 사용 가능한데, while 과 다르게 반복문을 먼저 실행하고 조건에 따라 계속할 것인지 아닌지를 판단한다.

## for

```c
#include <stdio.h>
int main() {
    int a,b,sum=0;
    scanf("%d %d", &a, &b);
    for (int i=a;i<=b;i++)
        sum+=i;
    printf("%d", sum);
}
```

`for(시작값;반복 조건;증감식) { 참일 경우 실행 }` 형태로 사용 가능

```c
#include <stdio.h>
int main() {
    int a,b,sum=0;
    scanf("%d %d", &a, &b);
    for (int i=a;i<=b;i++){
        for (int j=1;j<=9;j++){
            printf("%d * %d = %d ", i,j,i*j);
        }
        printf("\n");
    }
}
```

중첩해서 사용 가능

-   break : 반복문을 빠져나감
-   continue : 이후 명령 실행하지 않고 다시 조건 판단

## 배열

같은 종류의 데이터 여러개를 처리하기 쉽게 나열한것

```c
int score{5}={85,93,98,78,100};
/*
score[0]=85
score[1]=93
score[2]=98
score[3]=78
score[4]=100
*/
```

```c
#include <stdio.h>
int main() {
    int score[3][2]={ 0 };
    for (int i=0;i<3;i++)
        for (int j=0;j<2;j++)
            scanf("%d", &score[i][j]);
    for (int i=0;i<3;i++){
        printf("학생 %d: ", i+1);
        for (int j=0;j<2;j++)
            printf("%d ", score[i][j]);
        printf("\n");
    }
}
```

2차원 배열은 컴파일 시 전부 1차원으로 변환해서 메모리에 들어간다.

## 포인터

포인터는 메모리의 주소를 가지고 있는 변수이다.

```c
int a=10;
int *p;
p=&a;
printf("%d", *p);
```

```c
#include <stdio.h>
int main() {
    int i=10;
    int *pi = &i;

    printf("i=%d, pi=%p\n", i, pi);
    (*pi)++;
    printf("i=%d, pi=%p\n", i, pi);

    printf("i=%d, pi=%p\n", i, pi);
    *pi++;
    printf("i=%d, pi=%p\n", i, pi);
}
```

`(*pi)++` 을 하면 pi 가 가리키는 곳인 i에 들어간 10이 1만큼 증가하고, `*pi++` 을 하면 주소가 i의 크기 (4bytes) 만큼 증가한다.
| 자료형 | 크기 |
|--|--|
| char | 1 byte |
| short | 2 bytes |
| int | 4 bytes |
| float | 4 bytes |
| double | 8 bytes|
```c
#include <stdio.h>
int main() {
    int a[]={1,2,3,4,5};
    printf("a=%u\n", a);
    printf("a+1=%u\n", a+1);
    printf("*a=%d\n", *a);
    printf("*(a+1) = %d\n", *(a+1));
}
```

```
a=3544564624 //a의 주소값
a+1=3544564628 // 주소값 + 4bytes
*a=1 //a가 가리키는 값
*(a+1) = 2 //a[1] 값
```

## 함수

-   코드가 중복되는 것을 막을 수 있음
-   여러번 재사용 가능
-   보다 체계적이고 유지보수 쉬움

```c
#include  <stdio.h>
int add (int x, int y) {
	return x+y;
}
int main() {
	printf("%d", add(2,4));
}
```

여기서 인수는 2와 4이고 매개변수는 x,y 이다.  
함수의 return 값에 따라 함수 이름 앞에 `int`, `double`, `char`, `long long int` 등을 지정할 수 있고, 반환값이 없으면 `void` 를 쓰면 된다.

```c
#include  <stdio.h>
int add (int x, int y);
int main() {
	printf("%d", add(2,4));
}
int add (int x, int y){
	return x+y;
}
```

함수 프로토타입을 사용하는 이유는 `main` 함수 뒤에 사용자 정의 함수를 쓰게 되면 컴파일러가 그 함수의 위치를 찾지 못하기 때문에 미리 정의해주는 것이다.

```c
#include <stdio.h>
int recursive(int n){
    if (n==1)
        return 1;
    else
        return recursive(n-1)*n;
}
int main() {
    int a;
    scanf("%d", &a);
    printf("%d", recursive(a));
}
```

함수에서 현재 n값에 1 감소시킨 값을 호출하는 방식으로 팩토리얼을 계산하는 프로그램이다.

## 난수

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
int main() {
	srand(time(NULL));
	printf("%d", rand()%10+1);
}
```

`rand()%n` : 0부터 n-1까지 난수 생성  
`rand()%n+1` : 1부터 n까지 난수 생성  
`srand(time(NULL));` : 1970.1.1 00:00:00 부터 지금까지의 시간 (초) 을 랜덤값 생성 시드로 사용
