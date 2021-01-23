---
title: "Basic Python"
date: 2021-01-24T01:17:01+09:00
draft: false
---

## PYTHON으로 무엇을 할 수 있을까?

-   시스템 유틸리티 제작
-   GUI 프로그래밍
-   C/C++와의 결합
-   웹 프로그래밍
-   수치 연산 프로그래밍
-   데이터베이스 프로그래밍
-   데이터 분석, 사물 인터넷

## 문자열 자료형

### 문자열 연산

```py
>>> a='hello'
>>> b='world'
>>> a+b
'helloworld'
```

```py
>>> a='test123'
>>> b=3
>>> a*b
'test123test123test123'
```

```py
>>> a='hello'
>>> a[0]='b'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

슬라이싱을 활용하여 문자열을 조합하거나 replace 함수를 쓰자.

### 문자열 포맷팅

```py
>>> print("%s is fun %d" %("python", 1423))
python is fun 1423
```

```py
>>> name='Devleo'
>>> num=1423
>>> "I am {0} {1} !!".format(num,name)
'I am 1423 Devleo !!'
```

```py
>>> "I am {num} {name} !!".format(num=1423, name='Devleo')
'I am 1423 Devleo !!'
```

```py
>>> pi=3.141592653589793238462643383279502884197169399375
>>> "{0:10.5f}".format(pi)
'   3.14159'
```

10칸의 공간에서 우측정렬, 소수점 6번째 자리에서 반올림

```py
print("{0:=^20}".format("hello"))

=======hello========
```

20칸의 공간에서 hello 를 ‘=’ 으로 둘러싸고 가운데 정렬
|정렬| 기능 |
|--|--|
| < | 왼쪽 정렬 |
|> |오른쪽 정렬 |
|^ | 가운데 정렬|

## 리스트

```py
>>> a=[1, 2, ['a','b', ['life', 'is']]]
>>> a[-1][2][1]
'is'
```

중첩해서 사용 가능

```py
>>> a=[1,2,'hello','python']
>>> len(a)
4
```

리스트 원소의 개수 : `len()`

```py
>>> a=[0,1,2,3]
>>> a[3]+"python"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

`a[3]` 을 `str`로 형변환 한다

```py
>>> str(a[3])+"python"
'3python'
```

### 리스트 관련 중요 함수
| 함수 | 기능 |
|--|--|
| append() | 리스트 요소 추가 |
|sort() |리스트 정렬 |
|reverse() |리스트 뒤집기 |
|index() |위치 반환 (존재하지 않는 값은 `ValueError`) |
|pop() | 리스트 요소 (n번째) 빼기|
```py
>>> a=[47,258,12,79,238,35]
>>> print(a.sort())
None
```

리스트 a를 오름차순으로 정렬해주는 것은 맞지만, **출력할 반환값이 없음** (`reverse()` 도 동일)

## 튜플

-   **리스트와 달리 값의 생성, 삭제, 수정 불가**
-   중첩해서 사용 가능
-   인덱싱, 슬라이싱 가능
-   더하기 곱하기 가능

```py
>>> a=(1,2,3)
>>> a
(1, 2, 3)
```

```py
>>> a
(2, 3, 4)
>>> a[1]=3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

## 딕셔너리

-   대응관계를 나타낼 수 있는 자료형
-   key를 통해 value를 얻음

```py
a={"name":"Devleo","birth":"040324", "school":[1423,"WP"]}
```

`value`에 리스트 사용 가능, `key`는 불가

```py
>>> a["name"]="SangHyuk"
>>> a
{'school': [1423, 'WP'], 'name': 'SangHyuk', 'birth': '040324'}
```

추가, 수정 가능

```py
>>> del(a["birth"])
>>> a
{'school': [1423, 'WP'], 'name': 'SangHyuk'}
```

삭제 가능

### 딕셔너리 관련 중요 함수
| 함수 | 기능 |
|--|--|
| keys() | key값 반환 `['school', 'name']`|
|values() |value값 반환 `[[1423, 'WP'], 'SangHyuk']` |
|items() |key, value 쌍을 튜플로 반환 `[('school', [1423, 'WP']), ('name', 'SangHyuk')]` |
| get()|key에 대응하는 value 반환 `SangHyuk'` |

## 집합 자료형

-   집합에 관련된 것을 쉽게 처리
-   중복 허용하지 않음
-   순서가 없음
-   **인덱싱으로 값을 얻을 수 없음**

```py
>>> s1=set([1,2,3,4,5])
>>> s1
set([1, 2, 3, 4, 5])
>>> s1[0]
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
TypeError: 'set' object does not support indexing
```
| 집합자료형 연산 | 연산자 |
|--|--|
| 교집합 | `&` |
| 합집합| `|`|
| 차집합| `-`|
```py
>>> s2=set([3,4,5,6])
>>> s1-s2
set([1, 2])
```
| 집합자료형 관련 함수 | 기능 |
|--|--|
| add() | 1개의 값 추가 |
|update() |여러개의 값 추가 |
|remove() |특정값 제거 |

```py
>>> s1.remove(3)
>>> s1
set([1, 2, 4, 5])
```

```py
>>> s1.update([-1,-5,7])
>>> s1
set([1, 2, 4, 5, 7, -5, -1])
```

## 불 자료형

참과 거짓을 나타내는 자료형 (True or False)

## if문

```py
>>> a=31337
>>> if a%2:
...     print('odd')
... else:
...     print('even')
...
odd
```

제어문에서 콜론을 사용하여 들여쓰기

```py
>>> if a%2 and len(str(a)) == 2:
...     print('hello')
... else:
...     print('world')
...
hello
```

`and`, `or`, `not`사용 가능

```py
>>> dimi=['EB', 'DC', 'HD']
>>> if 'WP' in dimi:
...     pass
... else:
...     print('no dimi...')
...
no dimi...
```

`x in 튜플, 리스트, 문자열`  
`x not in 튜플, 리스트, 문자열` 사용 가능  
`pass`는 조건문에서 아무일도 하지 않게 설정

```py
>>> a=2
>>> if a==1:
...     print('I')
... elif a==2:
...     print('love')
... else:
...     print('python!')
...
love
```

`if ~ elif ~ ... ~ else` 형태로 다양한 조건 판단 가능

```py
>>> score=93
>>> print('success') if score >= 90 else print('fail')
success
```

조건부 표현식 \- 가독성, 활용성 좋음

## while

```py
time=0
while time <  7:
	print("%d a.m. sleeping..."  %time)
	time+=1
print('wake up!!')
```

```
0 a.m. sleeping...
1 a.m. sleeping...
2 a.m. sleeping...
3 a.m. sleeping...
4 a.m. sleeping...
5 a.m. sleeping...
6 a.m. sleeping...
wake up!!
```

```py
money = 2000
drink = ("energy drink", "soda", "coke", "toreta")
cost = [1000, 700, 800, 1200]
while 1:  # while True: 와 동일
    i = 0
    while i < len(drink):
        print("%d. %s (%d)" % (i+1, drink[i], cost[i]))
        i += 1
    print("money = %d" %money)
    choice = int(input())
    if choice > 0 and choice <= len(drink):
        if money >= cost[choice-1]:
            print("You bought %s!" % drink[choice-1])
            money-=cost[choice-1]
        else:
            print("you have not enough money")
            break        
    else:
        print("there is no number %d..." %choice)
print("bye bye")
```

break : 특정 조건에서 반복문 탈출  
continue : 반복문 처음으로 이동

## for

```
for 변수 in 리스트, 튜플, 문자열:
	반복할 내용
```

리스트나 튜플, 문자열의 요소에 차례로 변수에 대입된다.

```py
a=[4,7,-3,6]
sum=0
for i in a:
	sum+=i
print (sum)
```

```py
for i in range(2,5):
    for j in range(1,5):
        print(i*j, end=" ")
```

range(2,5) 는 2부터 4까지를 의미한다.

### 리스트 내포

```py
a=[1,-4,-2,6,3]
res=[i*4 for i in a if i > 0]
print(res)

[4, 24, 12]
```

a 원소 중 0보다 큰 수들에 4를 곱한 값을 저장

## 함수

```py
def add(*arr):
    sum=0
    for i in arr:
        sum+=i
    return sum
print(add(1,2,3,4,5))
```

매개변수에 `*`을 붙이면 **여러개의 입력값**을 받는다.

```py
def find(**dic):
	print(dic.get('name'))
find(name='devleo', age=17)
```

매개변수에 `**`를 붙이면 **딕셔너리**로 변환된다.

```py
a = 1
def test():
	global a
	a+=1
test()
print(a)
```

전역변수 a를 함수 안에서 쓰려면 `global 변수`

### 함수 사용시 주의할 점

-   **함수 안에서 만든 변수는 함수 안에서만 사용 가능**
-   매개변수는 함수 밖의 변수 이름과는 상관 없음

### lambda

함수를 한줄로 간결하게 만들 때 사용

```py
mul=lambda  a,b: a*b
print(mul(4,-2))
```

## 파일 입출력
|파일 열기 모드 | |기능 |
| |읽기 모드 |
 | 기능 |
|--|--|
| rr | 읽기 모드 |
|w 쓰기 모드| |
|w | 쓰기 모드|
| a| 추가 모드|
```py
f=open('test.txt', 'w')
for i in range(1,11):
	f.write('%d번째 줄\n'%i)
f.close()
```
test.txt에 데이터 저장
```py
f=open('test.txt', 'r')
while  1:
	line=f.readline()
	if not line:
		break
	print(line)
f.close()
```

test.txt 한줄씩 읽고 출력

```py
f=open('test.txt', 'r')
line=f.readlines()
for i in line:
    print(i)
f.close()
```

test.txt 내용을 한줄씩 리스트로 저장

**쓰기모드로 파일을 열면 원래 있던 데이터가 모두 사라진다.** 값을 추가하려면 추가모드로 열면 된다.

```py
with open("./test.txt",'w') as f:
	f.write("Hello World!")
```
close() 가 필요없다.