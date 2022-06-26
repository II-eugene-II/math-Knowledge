## 리만 가설 검증

---

[밀러라빈 소수 판별법](https://github.com/II-eugene-II/Prime-Produce/blob/main/Miller_Rabin_Primality_Test.md)

밀러라빈 소수판정법에서는 **리만 가설이 맞다는 가정 하에** 2(ln(N))^2 보다 작은 모든 소수들을 가지고 소수라고 판정이 되면 소수이다.

이 말은 곧 2(ln(N))^2 보다 작은 모든 소수들을 가지고 소수라고 판정이 되었는데, 사실은 소수가 아니었다면 **리만 가설이 틀렸다는 뜻**이다.

---

먼저 2(ln(N))^2 보다 작은 모든 소수 리스트를 만든다.

```
import math

def prime_Sieve(n):
    sieve = [True] * n                       # 태초에 모든 칸은 True(소수)로 판단
    
    m = int(n ** 0.5)                        # 소수가 아니라면 N의 약수가 2와 sqrt(N) 사이에 있다.
    #for i in range(4, n, 2):
    #    sieve[i] = False                    # 2가 아닌 2의 배수를 전부 False(합성수)로 판단...하지도 않고 아예 무시한다.
    for i in range(9, n, 6):
        sieve[i] = False                     # 3이 아닌 3의 배수를 전부 False(합성수)로 판단
    
    for i in range(3, m + 1, 2):             # i는 3부터 홀수만 따짐
        if sieve[i] == True:                 # i가 소수 일때는
            for j in range(5 * i, n, 6 * i): # i가 아닌 i의 배수들을 전부 False(합성수)로 판단
                sieve[j] = False
            for j in range(7 * i, n, 6 * i):
                sieve[j] = False             # 2, 3의 배수를 이미 제거했으므로 5i, 7i, 11i, 13i, ...만 제거

    # 소수 목록 산출
    return [2] + [i for i in range(3, n, 2) if sieve[i] == True]

def miller_rabin_test(n,a,r,d):
    # n은 odd integer
    # b는 base
    # n-1 = 2^r * d
    x = pow(a, d, n)  # a0= a^d mod n
    if x == 1 or x == n-1:
        return 1
    else: # a0가 +-1이 아니라면
        for i in range(r):
            if x==n-1:
                return 1
            x= pow(x,2,n)
        return 0

def is_prime(n):
    r=0
    if n<2 or not n&1:
        return 0 # 짝수이거나 1은 소수가 아니다.
    if n==2:
        return 1 # 2는 소수이다.
    d = (n-1)
    while d%2==0:
        r+=1
        d>>=1
    powlnN = math.ceil(2 * ((math.log(N)) ** 2))
    mini_primeList = prime_Sieve(powlnN)
    for a in mini_primeList:
        test = miller_rabin_test(n, a, r, d)
        if test==0:
            return 0
    return 1

N = input()
N = int(N)

if is_prime(N):
  print("높은 확률로 소수") # N이 3317044064679887385961981 보다 작으면 확실한 소수
else:
  print("확실한 합성수") # 소수라고 출력했으나 사실은 합성수인 경우는 있어도, 합성수라고 출력했으나 사실 소수인 경우는 없음
```

N이 3317044064679887385961981보다 작은 경우는 검증 되었으니, 이 이상에 대해 테스트해본다.

또, 일반 for문을 활용한 Naive한 소수 판별 함수를 만든다.

밀러 판정법에서 소수라 했는데 Naive한 판정법에서 소수가 아니라고 하는 순간 **리만 가설이 틀렸다는 뜻**이 된다. (Naive한 판정법은 틀릴 수 없다.)

---

밀러 판정법에서 소수라 출력하고, Naive한 판정법에서 소수라 출력하면 그냥 하던 일 계속 하고,

밀러 판정법에서 소수라 출력하고, Naive한 판정법에서 합성수라고 출력하면 알림을 울리게 한디.

밀러 판정법에서 합성수라고 출력하면 확실한 것이므로 Naive한 판정을 굳이 하지 않는다. (시간이 오래걸리므로...)

---

```
import math

# 에라토스테네스의 체

def prime_Sieve(n):
    sieve = [True] * n                       # 태초에 모든 칸은 True(소수)로 판단
    
    m = int(n ** 0.5)                        # 소수가 아니라면 N의 약수가 2와 sqrt(N) 사이에 있다.
    #for i in range(4, n, 2):
    #    sieve[i] = False                    # 2가 아닌 2의 배수를 전부 False(합성수)로 판단...하지도 않고 아예 무시한다.
    for i in range(9, n, 6):
        sieve[i] = False                     # 3이 아닌 3의 배수를 전부 False(합성수)로 판단
    
    for i in range(3, m + 1, 2):             # i는 3부터 홀수만 따짐
        if sieve[i] == True:                 # i가 소수 일때는
            for j in range(5 * i, n, 6 * i): # i가 아닌 i의 배수들을 전부 False(합성수)로 판단
                sieve[j] = False
            for j in range(7 * i, n, 6 * i):
                sieve[j] = False             # 2, 3의 배수를 이미 제거했으므로 5i, 7i, 11i, 13i, ...만 제거

    # 소수 목록 산출
    return [2] + [i for i in range(3, n, 2) if sieve[i] == True]

# 밀러 라빈 테스트

def miller_rabin_test(n,a,r,d):
    # n은 odd integer
    # b는 base
    # n-1 = 2^r * d
    x = pow(a, d, n)  # a0= a^d mod n
    if x == 1 or x == n-1:
        return 1
    else: # a0가 +-1이 아니라면
        for i in range(r):
            if x==n-1:
                return 1
            x= pow(x,2,n)
        return 0
        
# 밀러 라빈 테스트를 이용한 소수 판정

def is_prime(n):
    r=0
    if n<2 or not n&1:
        return 0 # 짝수이거나 1은 소수가 아니다.
    if n==2:
        return 1 # 2는 소수이다.
    d = (n-1)
    while d%2==0:
        r+=1
        d>>=1
    powlnN = math.ceil(2 * ((math.log(N)) ** 2))
    mini_primeList = prime_Sieve(powlnN)
    for a in mini_primeList:
        test = miller_rabin_test(n, a, r, d)
        if test==0:
            return 0 # 소수 아님
    return 1 # 소수
    
# Naive한 판정법

def is_NaivePrime(N):
    sqrtN = math.ceil(math.sqrt(N))
    for i in range(3, sqrtN, 2): #처음부터 짝수는 입력하지 않는 것으로 한다.
        if(N % i == 0):
            return 0 # 소수 아님
    return 1;

N = 3317044064679887385961981

while(1):
    if is_prime(N):
        if is_NaivePrime(N):
            print("리만가설 아직 맞음", N)
        else:
            print("리만가설 틀림", N)
    else:
        print("확실한 합성수", N) # 소수라고 출력했으나 사실은 합성수인 경우는 있어도, 합성수라고 출력했으나 사실 소수인 경우는 없음
    N += 2
```

처음엔 이렇게 코드를 짰으나, 3317044064679887385962123 이 소수인지 아닌지 Naive 한 소수 판정법이 너무 느려서 조금 더 최적화 하기로 한다.
