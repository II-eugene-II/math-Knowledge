## 피보나치 수열

---

피보나치 수열의 기본 정의는 다음과 같습니다.

$$F_0 = 0, F_1 = 1$$

$$ F_{n+2} = F_{n+1} + F_n $$

초항 두개를 $F_1 = 1, F_2 = 1$ 로도 하지만, 두 정의는 완전히 동일합니다.

---

피보나치 수의 일반항이 $$F_n = \frac{1}{\sqrt5} \times \frac{(1+\sqrt5)^n-(1-\sqrt5)^n}{2^n}$$ 임이 잘 알려져 있지만 증명은 우선 생략하기로 합니다.

---

행렬의 거듭제곱으로도 피보나치수를 표현할 수 있습니다.

$$ \left[
\begin{matrix}
    F_{n+1} & F_{n} \\
    F_{n} & F_{n-1} \\
\end{matrix}
\right] = \left[
\begin{matrix}
    1 & 1 \\
    1 & 0 \\
\end{matrix}
\right]^n $$

---

## 기타 여러가지 특징들

---

오직 피보나치 수만 연구하는 그런 특별한 학술지도 있습니다. https://www.fq.math.ca/

무려 1963년부터 나온 나름 꽤나 전통있는 학술지이며, 63년편부터 16년호까지 무료로 볼 수 있습니다. https://www.fq.math.ca/list-of-issues.html

또한, 워낙 특수하면서도 심플한 점화식을 가지고 있기에 여러가지 수많은 성질들을 가지고 있다.

---

1번 -

$F_{n+1} F_{n-1} - {F_n}^2 = (-1)^n$

(카시니 항등식)

<details markdown="1">
<summary>증명 접기/펼치기</summary>

<!--summary 아래 빈칸 공백 두고 내용을 적는공간-->

증명법 1. 수학적 귀납법

$n = k$일때 성립한다고 하면 $F_{k+1}F_{k-1}-{F_k}^2=(-1)^k$이다.



증명법 2. 행렬식

$$ F_{n+1} F_{n-1} - F_{n}^{2} = \det \left[
\begin{matrix}
    F_{n+1} & F_{n} \\
    F_{n} & F_{n-1} \\
\end{matrix}
\right] = \det \left[
\begin{matrix}
    1 & 1 \\
    1 & 0 \\
\end{matrix}
\right]^n = (-1)^{n} $$

</details>

---

2번 -

${F_n}^2 - F_{n+r}F_{n-r} = (-1)^{n-r}{F_n}^2$

(1번의 일반화)

---

3번 -

$F_{m+n} = F_{m-1} F_{n} + F_{m} F_{n+1}$

(위 행렬곱으로 증명 가능)

---

4번 -

$\sum\limits_{k=0}^n F_{k} = F_{n+2}-1$

---

5번 -

$\sum\limits_{k=0}^n (-1)^{k+1} F_{k} = (-1)^{n+1} F_{n-1}+1$

---

6번 -

$\sum\limits_{k=0}^n {F_{k}}^2 = F_{n} F_{n+1}$

---

7번 -

$\sum\limits_{k=0}^n {F_{k}}^3 = \frac{F_{3n+2} + (-1)^{n+1}6F_{n-1} + 5}{10}$

이 항등식은 잘 생각해보면 모든 자연수 $n$에 대하여 $F_{3n+2} + (-1)^{n+1}6F_{n-1} + 5$이 10의 배수임을 나타내기도 한다. (좌변이 자연수 이므로)

---

8번 -

$\sum\limits_{k=1}^n F_{2k-1} = F_{2n}$

$k=1$ 인데에 유의하자.

---

9번 -

$\sum\limits_{k=0}^n F_{2k} = F_{2n+1} - 1$

---

10번 -

$\sum\limits_{k=0}^n F_{3k} = \frac{F_{3n+2} - 1}{2}$

7번과 마찬가지로 모든 자연수 $n$에 대하여 $F_{3n+2}$의 값이 홀수임을 알 수 있다. (좌변이 자연수이므로)

---

11번 -

자연수 $k$에 대하여

"$k$는 피보나치 수이다." 와 "$5k^2 + 4$ 혹은 $5k^2 - 4$가 제곱수이다."

는 동치이다. (!)

정말 놀랍게도 그냥 일방적으로 "$k$는 피보나치 수"이면 "$5k^2 + 4$ 혹은 $5k^2 - 4$가 제곱수"가 되는 것도 아니고, 아예 완전히 같은 말이다.

[출처1](https://en.wikipedia.org/wiki/Fibonacci_number#Identification)
[출처2](https://m.blog.naver.com/kyh941031/221919420503)

---

12번 -

$F_{2n+k} = F_k {F_{n+1}}^2 + 2 F_{k-1} F_{n+1} F_{n} + F_{k-2} {F_{n}}^2$

---

13번 -

$F_{3n} = 2{F_{n}}^3 + 3F_n F_{n+1} F_{n-1} = 5{F_{n}}^3 + 3 (-1)^n F_{n}$

---

14번 -

$F_{3n+1} = {F_{n+1}}^3 + 3 F_{n+1}{F_{n}}^2 - {F_{n}}^3$

---

15번 -

$F_{3n+2} = F_{n+1}^3 + 3 F_{n+1}^2F_n + F_n^3$

---

16번 -

$F_{4n} = 4F_nF_{n+1}(F_{n+1}^2 + 2F_n^2) - 3F_n^2(F_n^2 + 2F_{n+1}^2)$

---

17번 -

$\sum\limits_{n=0}^\infty \frac{F_n}{10^{n}} = \frac{10}{89}$

---

18번 -

$\sum\limits_{n=0}^\infty \frac{F_n}{x^{n}} = \frac{x}{x^{2}-x-1}$

(17번의 일반화)

---

19번 -

$\sum\limits_{k=0}^\infty \frac{1}{1+F_{2k+1}} = \frac{\sqrt{5}}{2}$

---

20번 -

$\sum\limits_{k=1}^\infty \frac{(-1)^{k+1}}{\sum\limits_{j=1}^k {F_{j}}^2} = \frac{\sqrt{ 5}-1}{2}$

---

21번 -

$\sum\limits_{k=n}^{n+9} F_{k} = 11 F_{n+6}$

-> 연속된 10개의 항은 11의 배수이다.

---

22번 -


$\sum\limits_{n=0}^\infty {{F_n}^2}{k^{n}} = \frac{x(1-x)}{1-2x-2x^{2}+x^3}$

---

23번 -

$F_{k+2} p^{k+1} + F_{k+1} p^{k+2} \equiv 1 \pmod{p^2+p-1}$

<details markdown="1">
<summary>증명 접기/펼치기</summary>

<!--summary 아래 빈칸 공백 두고 내용을 적는공간-->


$$ F_{k+2} p^{k+1} + F_{k+1} p^{k+2} = \left( F_{k+1} + F_{k} \right)  p^{k+1} + \left( F_{k} + F_{k-1} \right) p^{k+2} = p \left( F_{k+1} p^{k} + F_{k} p^{k+1} \right) + p^2 \left( F_{k} p^{k+1} + F_{k-1} p^{k} \right) $$

$$ p \left( F_{k+1} p^{k} + F_{k} p^{k+1} \right) + p^2 \left( F_{k} p^{k+1} + F_{k-1} p^{k} \right) \equiv p^2 + p \equiv 1 \pmod{p^2+p-1} $$

</details>
