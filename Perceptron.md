
* Perceptron

Input 값에 가중치 w를 주어 합산한 값에 bias를 더하여 Output으로 내보내고, Activate Function을 통해 1 혹은 -1(0) 값을 가진다. 


* sklearn.linear_model.Perceptron

학습반복수와 학습률을 설정하여, y값에 가장 fit한 가중치 값을 찾는 방법의 Perceptron.
이때 오차를 줄이기 위해 SGD(Stochastic Gradient Descent)을 사용한다.


※ 이렇게 나온 Perceptron은 Activate Function을 적용하지 않은 선형 모델이다.
하지만 설비예지보전에서의 종속변수는 고장,정상(1,0)으로만 표기되므로 
Perceptron으로 Fitting된 모델을 굳이 Activate Function을 사용할 필요가 없어보인다.


- 주요 parameter 

class_weight: 초기 가중치값을 설정한다.(Default=1)
eta0: 학습률, 값이 커지면 최적값에 빨리 도달할 수는 있지만, 정확하지 않을 것이다. 
n_iter: 학습반복수, 몇번의 학습률 조정이 이루어질 것인지 설정. 

- 주요 Methods

fir(X,Y): SGD를 사용할 독립변수와 종속변수를 설정
predict(X): Test 데이터의 예측값 산출



* Stochastic Gradient Descent
--> 실제 데이터 y와 모델의 예측값 y^에 대한 오차를 줄이기 위해, 가중치를 학습률에 의해 조정하면서 최적의 가중치 도출
Gradient Descent와는 다르게 train set 중 일부만 사용한다. 하지만 속도가 빠름

* activate function 
-> 이분적인 값을 가지게 하기 위한 Function (sigmoid, linear, Relu, tanh)

* Gradient(구배)
-> 공간에 대한 기울기, gradint의 방향이 함수값이 커지는 방향이다. 따라서 최대점을 찾는데 사용할 수 있다.





* 역사

Perceptron으로 XOR같은 비선형 문제를 풀 수 없다.
--> 다층퍼셉트론으로 비선형 문제 풀 수 있다.

그러나 
1970년 MLP(다층퍼셉트론)을 학습시킬 방법이 존재하지 않는다. - M.Minsky, 첫번째 암흑기(Dark Age)
1974년 MLP를 학습시키는 방법인 역전파(Back-Propagation)를 발표했으나 외면당했다. - P.Werbos
1986년 역전파 개념 다시 발견하고 제안 - G.Hinton 

그러나 
MLP는 은닉층의 갯수를 늘릴수록 성능이 좋아진다고 알려져 있는데, 은닉층이 많아지면서 중간 은닉층에서 가중치 계산이
불가능해지는(0으로 수렴), gradient vanishing 문제에 빠짐, 두번째 암흑기(Second Dark Age)

gradient vanishing 문제는 은닉층의 활성함수(Activation Function)을 시그모이드 함수에서 Rectifier 라는 ReLU 함수로 바꾸면서 해결
gradient vanishing의 원인은 sigmod함수를 사용했기 때문.

2006년 Hinton과 Bengio교수는 ReLU를 활용하고 초기입력값을 잘 선택하면 층수가 많아지는것을 발표했다. 
이렇게 층수가 많아진 신경망을 Deep Neural Network하고, DNN을 학습시키는 방법을 Deep Learning 이라고 한다.
은닉층은 ReLu함수를 사용하고 출력층은 시그모이드나 소프트맥스를 사용

* Back Propagation

종속변수 y에 어떤 영향을 주는지 알기 위해 독립변수의 기울기(미분)값을 이용한다.
y=w1x1+w2x2+b 일때 x1과 x2의 가중치는 기울기를 의미한다. 이때, 다층퍼셉트론(MLP)의 경우 계층이 많아진다.
이때 Forward Propagation의 경우 한번 거쳤던 노드를 또 거치게 되면서 계산과정이 복잡해지지만
Back Propagation은 위에서부터 내려오기 때문에 불필요한 중복이 계산이 없어진다.


ReLu = max(0,x) (분명히 자연로그 e가 들어가 있을것이라 생각했지만 아니었다.)










