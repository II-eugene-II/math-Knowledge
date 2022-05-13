# 원주율 값의 근사

e의 경우에는 <img src="https://latex.codecogs.com/svg.image?e^x" title="https://latex.codecogs.com/svg.image?e^x" />의 테일러급수 식에 정수값(1)을 넣어서 비교적 쉽게 근사할 수 있었으나, 파이는 이야기가 다르다.

<img src="https://latex.codecogs.com/svg.image?e^x" title="https://latex.codecogs.com/svg.image?e^x" />의 테일러급수 식으로 원주율을 구하려면, <img src="https://latex.codecogs.com/svg.image?\pi" title="https://latex.codecogs.com/svg.image?\pi" />값도 모르는데 <img src="https://latex.codecogs.com/svg.image?\ln&space;\pi" title="https://latex.codecogs.com/svg.image?\ln \pi" />의 값을 알아야만 하는 당혹스러운 일이 생긴다.

원주율값과 관련된 함수는 당연히 삼각함수이다. 그러나 원래의 삼각함수는 원주율값을 넣어야 정수값이 나오는 형식이기 때문에, 정수값을 넣어 원주율 값을 알고 싶으면 삼각함수의 역함수. 즉 역삼각함수를 이용해야한다.

탄젠트 함수의 역함수인 아크탄젠트 함수의 경우, 테일러급수를 이용하여

<img src="https://latex.codecogs.com/svg.image?\arctan&space;x&space;=&space;\sum^{\infty}_{n=0}&space;\frac{(-1)^n}{2n&plus;1}&space;x^{2n&plus;1}" title="https://latex.codecogs.com/svg.image?\arctan x = \sum^{\infty}_{n=0} \frac{(-1)^n}{2n+1} x^{2n+1}" />

이므로, <img src="https://latex.codecogs.com/svg.image?x=1" title="https://latex.codecogs.com/svg.image?x=1" /> 대입시 <img src="https://latex.codecogs.com/svg.image?\frac{\pi}{4}" title="https://latex.codecogs.com/svg.image?\frac{\pi}{4}" /> 가 나옴을 알 수 있다.

<img src="https://latex.codecogs.com/svg.image?\arcsin&space;x&space;=&space;\sum^{\infty}_{n=0}&space;\frac{(2n)!}{4^n&space;(n!)^2&space;(2n&plus;1)}&space;x^{2n&plus;1}" title="https://latex.codecogs.com/svg.image?\arcsin x = \sum^{\infty}_{n=0} \frac{(2n)!}{4^n (n!)^2 (2n+1)} x^{2n+1}" />

---

그러나 순수하게 이 공식만을 이용하면 수렴 속도가 굉장히 느리다. 따라서 역탄젠트 함수의 공식을 응용한 "마친 공식"을 따라 계산한다.
