Functions Continued
==

## Recursive Functions

---

```text
어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다.
"재귀함수가 뭔가요?"
"잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을 통달한
선인이 있었어. 마을 사람들은 모두 그 선인에게 수많은 질문을 했고, 
모두 지혜롭게 대답해 주었지. 그의 답은 대부분 옳았다고 하네.
그런데 어느날, 그 선인에게 한 선비가 찾아와서 물었어.
"재귀함수가 뭔가요?"
"잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을...
```
---

# 재귀함수란?

## 자기 자신을 다시 호출해서 작업을 수행하는 함수

---
# 팩토리얼을 예시로 보여주자면
```python 
def fact(n):
    if ( n == 1):
        return 1
    return fact(n-1)*n
```
>재귀함수로 팩토리얼을 구현해보면 이렇다

```text
T(N) = N * T(N-1)
T(1) = 1
```
>점화식으로 표현하면 이렇다

---

### 자 그럼 아래의 식을 재귀함수로 구현해볼까요
$$\sum_{i=0}^n i$$

```python
def sum(n):
    #여기 코드를 넣으세요
```
---

# 다음은 피보나치
```python
def fib(n):
    if ( n == 0 or n == 1):
        return n
    return fib(n-1) + fib(n-2)
```
>재귀는 2번 재참조 가능
```text
T(N) = T(N-1) + T(N-2)
T(1) = 1 
T(0) = 0
```
>점화식으로 표현하면 이렇다

---
## 피보나치 함수의 호출과정을 트리로 표현해보자

----

<div style="width:85%;height:auto;">

![](https://cdn.namuwikiusercontent.com/storage/1dd1d55c8c067af61042e73810af1bf2a2b760270dbb0d377724854a340f9d5445148e15644b8b5a488543fe144946de4d44c3a035e5751de8f8005c5158c437461690f684826edc7e3d0db95d384583?e=1513384884&k=SnxxR2MTtq8QmVHLjBIYkQ)
</div>
<span style="font-size:140%">

>잠시만요, 여러번 불리는 숫자가 있네요?
</span>
---
#### 위의 그림에서 f(2) 같은 경우는 2번 호출된다. 
#### f(1)는 3번 f(0)는 2번 계산되어 4번 중복계산 된다.
#### 숫자가 커질 수록 중복 호출되는 횟수도 증가해 효율성이 떨어진다.

<span style="font-size:180%">

**좋은 방법은 없을까?**
</span>

---
# 메모이제이션!!
### 한번 호출한 값은 메모리에 저장하면 되지 않을까?


---
```python
def fib(n):
    if ( n == 0 or n == 1):
        return n
    return fib(n-1) + fib(n-2)
```
> 이 코드를 고쳐보자
```python
memo = {}
def memFib(n):
    if n < 2:
        memo[n] = n
    elif n not in memo:
        memo[n] = memFib(n-1) + memFib(n-2)
    return memo[n]
```
---

# 한번 퀵소트를 짜볼까요??

<div style="width:50%;height:auto;">

![](https://s3.amazonaws.com/likeitlearnit/images/QuickSortLarge.png)
</div>

---

# 퀵소트란?

#### 어떤 리스트 안에서 임의의 피벗을 추출한 후 그 피벗을 기준으로 왼쪽으로는 작은 숫자를 두고 오른쪽으로는 큰 숫자를 오게끔 하는 정렬법
<https://www.youtube.com/watch?v=XE4VP_8Y0BU>

---
```python
def QuickSort(List):
     if len(List)  < 2:
         return List
     Pivot = List[0]
     return QuickSort([x for x in List[1:] if x <  Pivot]) 
          + Pivot
          + QuickSort([x for x in List[1:] if x >= Pivot])
```

---

```text
콜라츠의 추측, 3n+1 문제, 우박수 문제라고 불리는 이 문제는 

다음과 같다.

1, 어떤 자연수 n이 입력되면,

2. n이 홀수이면 3n+1을 하고,

3. n이 짝수이면 n/2를 한다.

4. 이 n이 1이 될때까지 2 3과정을 반복한다.

예를 들어 5는 5 → 16 → 8 → 4 → 2 → 1 이 된다.

이 처럼 어떤 자연수 n이 입력되면 위 알고리즘에 의해 1이 되는 

과정을 모두 출력하시오.

```

---

```python
def HNum (n):
    print (n)
    if n == 1:
        return None
    if n%2 ==1:
        HNum(3n+1)
    else
        HNum(n/2)
```

---


```

방금 전의 문제를 역순으로 출력해 보세요

```
---

```python
def HNum (n):
    
    if n == 1:
        print(n)
        return None
    elif n%2 ==1:
        HNum(3n+1)
    else
        HNum(n/2)
    print(n)
```
---

<http://codeup.kr/JudgeOnline/problem.php?id=3709>
<http://codeup.kr/JudgeOnline/problem.php?id=3716>


---

1번은 사실 피보나치

2번은 점화식으로 풉시다

T(n) = T(n-1) + T(n-2) + 3*T(n-3)

---



```text

nCr을 계산하는 프로그램을 만들어봅시다

*참고: nCr = n-1Cr + n-1Cr-1
```


---
<small>

```text
혹시 심심하시면 풀어보세요

어떤 수열이 있을 때 연속된 구간의 최대합을 출력하려고 한다.

예를 들어

2 -6 4 5 -2 6 2 -1이라는 수열이 있다면 

연속된 구간의 최대 부분합은 15이다. (4 + 5 + -2 + 6 + 2)

임의의 수열에 관해서 최대 부분합을 출력하는 프로그램을 짜보세요! ^~^

```
</small>

---

## Lambda function

---

#### 1회용 함수가 필요하다면? 
# 람다!

---
```python
def sum (a,b):
    return a + b
sum(10,23)
```
> 이것과 같은 기능을 하는 1회용 함수를 만들어보자
```python
(lambda x,y: x+y)(10,23)
```
> 짜잔!
---
# 제곱수로 리스트를 만들어볼까요?
```python
a = []*10
for i in range(10):
    a[i] = i*i
```
```python
a = [lambda x: x*x for x in range(10)]
```
---
# Functions Concluded
