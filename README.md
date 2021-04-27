# 중간고사 과제
## Strassen Alogorithm

## 이종웅


### Strassem Alogorithm 이란?

선형대수학에서 슈트라센 알고리즘은 독일의 수학자 폴커 슈트라센(Volker Strassen)이 1969년에 개발한 행렬 곱셈 알고리즘이다.
정의에 따라 n×n 크기의 두 행렬을 곱하면 O(n3)의 시간이 소요되지만 이 알고리즘은 대략 O(n2.807)의 시간이 소요된다.[\^myfootnote]

A와 B를 체 F에 대한 정사각행렬이라고 하자. 두 행렬의 곱 C는 다음과 같다.

{\displaystyle \mathbf {C} =\mathbf {A} \mathbf {B} \qquad \mathbf {A} ,\mathbf {B} ,\mathbf {C} \in F^{2^{n}\times 2^{n}}}{\displaystyle \mathbf {C} =\mathbf {A} \mathbf {B} \qquad \mathbf {A} ,\mathbf {B} ,\mathbf {C} \in F^{2^{n}\times 2^{n}}}
만약 A와 B가 2n × 2n 꼴의 크기가 아니라면 먼저 모자라는 행과 열을 0으로 채운다. 이 경우 행렬 곱셈이 끝난 뒤 행렬에서 필요한 부분만 다시 잘라 내야 한다.

이제 A, B, C를 같은 크기의 정사각행렬 네 개로 나눈다.

{\displaystyle \mathbf {A} ={\begin{bmatrix}\mathbf {A} _{1,1}&\mathbf {A} _{1,2}\\\mathbf {A} _{2,1}&\mathbf {A} _{2,2}\end{bmatrix}}{\mbox{ , }}\mathbf {B} ={\begin{bmatrix}\mathbf {B} _{1,1}&\mathbf {B} _{1,2}\\\mathbf {B} _{2,1}&\mathbf {B} _{2,2}\end{bmatrix}}{\mbox{ , }}\mathbf {C} ={\begin{bmatrix}\mathbf {C} _{1,1}&\mathbf {C} _{1,2}\\\mathbf {C} _{2,1}&\mathbf {C} _{2,2}\end{bmatrix}}}{\displaystyle \mathbf {A} ={\begin{bmatrix}\mathbf {A} _{1,1}&\mathbf {A} _{1,2}\\\mathbf {A} _{2,1}&\mathbf {A} _{2,2}\end{bmatrix}}{\mbox{ , }}\mathbf {B} ={\begin{bmatrix}\mathbf {B} _{1,1}&\mathbf {B} _{1,2}\\\mathbf {B} _{2,1}&\mathbf {B} _{2,2}\end{bmatrix}}{\mbox{ , }}\mathbf {C} ={\begin{bmatrix}\mathbf {C} _{1,1}&\mathbf {C} _{1,2}\\\mathbf {C} _{2,1}&\mathbf {C} _{2,2}\end{bmatrix}}}
이 때,

{\displaystyle \mathbf {A} _{i,j},\mathbf {B} _{i,j},\mathbf {C} _{i,j}\in F^{2^{n-1}\times 2^{n-1}}}{\displaystyle \mathbf {A} _{i,j},\mathbf {B} _{i,j},\mathbf {C} _{i,j}\in F^{2^{n-1}\times 2^{n-1}}}
따라서 다음이 성립한다.

{\displaystyle \mathbf {C} _{1,1}=\mathbf {A} _{1,1}\mathbf {B} _{1,1}+\mathbf {A} _{1,2}\mathbf {B} _{2,1}}{\displaystyle \mathbf {C} _{1,1}=\mathbf {A} _{1,1}\mathbf {B} _{1,1}+\mathbf {A} _{1,2}\mathbf {B} _{2,1}}
{\displaystyle \mathbf {C} _{1,2}=\mathbf {A} _{1,1}\mathbf {B} _{1,2}+\mathbf {A} _{1,2}\mathbf {B} _{2,2}}{\displaystyle \mathbf {C} _{1,2}=\mathbf {A} _{1,1}\mathbf {B} _{1,2}+\mathbf {A} _{1,2}\mathbf {B} _{2,2}}
{\displaystyle \mathbf {C} _{2,1}=\mathbf {A} _{2,1}\mathbf {B} _{1,1}+\mathbf {A} _{2,2}\mathbf {B} _{2,1}}{\displaystyle \mathbf {C} _{2,1}=\mathbf {A} _{2,1}\mathbf {B} _{1,1}+\mathbf {A} _{2,2}\mathbf {B} _{2,1}}
{\displaystyle \mathbf {C} _{2,2}=\mathbf {A} _{2,1}\mathbf {B} _{1,2}+\mathbf {A} _{2,2}\mathbf {B} _{2,2}}{\displaystyle \mathbf {C} _{2,2}=\mathbf {A} _{2,1}\mathbf {B} _{1,2}+\mathbf {A} _{2,2}\mathbf {B} _{2,2}}
이 과정에서는 필요한 연산의 수가 줄어 들지 않는다. 여전히 Ci,j 행렬을 계산하려면 여덟 번의 곱셈과 네 번의 덧셈이 필요하다.

이제 다음과 같은 행렬을 정의한다.

{\displaystyle \mathbf {M} _{1}:=(\mathbf {A} _{1,1}+\mathbf {A} _{2,2})(\mathbf {B} _{1,1}+\mathbf {B} _{2,2})}{\displaystyle \mathbf {M} _{1}:=(\mathbf {A} _{1,1}+\mathbf {A} _{2,2})(\mathbf {B} _{1,1}+\mathbf {B} _{2,2})}
{\displaystyle \mathbf {M} _{2}:=(\mathbf {A} _{2,1}+\mathbf {A} _{2,2})\mathbf {B} _{1,1}}{\displaystyle \mathbf {M} _{2}:=(\mathbf {A} _{2,1}+\mathbf {A} _{2,2})\mathbf {B} _{1,1}}
{\displaystyle \mathbf {M} _{3}:=\mathbf {A} _{1,1}(\mathbf {B} _{1,2}-\mathbf {B} _{2,2})}{\displaystyle \mathbf {M} _{3}:=\mathbf {A} _{1,1}(\mathbf {B} _{1,2}-\mathbf {B} _{2,2})}
{\displaystyle \mathbf {M} _{4}:=\mathbf {A} _{2,2}(\mathbf {B} _{2,1}-\mathbf {B} _{1,1})}{\displaystyle \mathbf {M} _{4}:=\mathbf {A} _{2,2}(\mathbf {B} _{2,1}-\mathbf {B} _{1,1})}
{\displaystyle \mathbf {M} _{5}:=(\mathbf {A} _{1,1}+\mathbf {A} _{1,2})\mathbf {B} _{2,2}}{\displaystyle \mathbf {M} _{5}:=(\mathbf {A} _{1,1}+\mathbf {A} _{1,2})\mathbf {B} _{2,2}}
{\displaystyle \mathbf {M} _{6}:=(\mathbf {A} _{2,1}-\mathbf {A} _{1,1})(\mathbf {B} _{1,1}+\mathbf {B} _{1,2})}{\displaystyle \mathbf {M} _{6}:=(\mathbf {A} _{2,1}-\mathbf {A} _{1,1})(\mathbf {B} _{1,1}+\mathbf {B} _{1,2})}
{\displaystyle \mathbf {M} _{7}:=(\mathbf {A} _{1,2}-\mathbf {A} _{2,2})(\mathbf {B} _{2,1}+\mathbf {B} _{2,2})}{\displaystyle \mathbf {M} _{7}:=(\mathbf {A} _{1,2}-\mathbf {A} _{2,2})(\mathbf {B} _{2,1}+\mathbf {B} _{2,2})}
이 Mk 행렬들은 Ci,j 행렬을 표현하는 데 쓰이는데, 이 행렬들을 계산하는 데는 일곱 번의 곱셈(각 변수마다 한 번씩)과 10번의 덧셈이 필요하다. 이제 Ci,j 행렬은 다음과 같이 표현할 수 있다.

{\displaystyle \mathbf {C} _{1,1}=\mathbf {M} _{1}+\mathbf {M} _{4}-\mathbf {M} _{5}+\mathbf {M} _{7}}{\displaystyle \mathbf {C} _{1,1}=\mathbf {M} _{1}+\mathbf {M} _{4}-\mathbf {M} _{5}+\mathbf {M} _{7}}
{\displaystyle \mathbf {C} _{1,2}=\mathbf {M} _{3}+\mathbf {M} _{5}}{\displaystyle \mathbf {C} _{1,2}=\mathbf {M} _{3}+\mathbf {M} _{5}}
{\displaystyle \mathbf {C} _{2,1}=\mathbf {M} _{2}+\mathbf {M} _{4}}{\displaystyle \mathbf {C} _{2,1}=\mathbf {M} _{2}+\mathbf {M} _{4}}
{\displaystyle \mathbf {C} _{2,2}=\mathbf {M} _{1}-\mathbf {M} _{2}+\mathbf {M} _{3}+\mathbf {M} _{6}}{\displaystyle \mathbf {C} _{2,2}=\mathbf {M} _{1}-\mathbf {M} _{2}+\mathbf {M} _{3}+\mathbf {M} _{6}}
이 과정에서는 곱셈이 사용되지 않기 때문에, 전체 곱셈을 일곱 번의 곱셈과 18번의 덧셈으로 처리할 수 있다. 큰 행렬에 대해서는 행렬의 곱셈이 덧셈보다 더 많은 시간을 필요로 하기 때문에 덧셈을 더 하는 대신 곱셈을 덜 하는 것이 전체적으로 더 효율적이다.

이 과정을 재귀적으로 반복할 경우 총 {\displaystyle 7\cdot n^{\log _{2}7}-6\cdot n^{2}}{\displaystyle 7\cdot n^{\log _{2}7}-6\cdot n^{2}}번의 연산이 필요하다. {\displaystyle \log _{2}7=2.807\cdots }{\displaystyle \log _{2}7=2.807\cdots }이므로 전체 수행 시간은 약 O(n2.807)이다. 실제로는 n이 작을 경우 정의에 따라 행렬 곱셈을 하는 경우가 빠를 수도 있기 때문에, 보통 작은 n에 대해서는 일반적인 방법으로 곱셈을 하도록 구현한다.

슈트라센 알고리즘은 속도에 비해 수치 안정성이 떨어지는 것으로 알려져 있다. 두 행렬 A와 B를 곱한 결과를 C라 할 때, 실제 오차인 {\displaystyle \lVert C-AB\rVert }{\displaystyle \lVert C-AB\rVert }는 {\displaystyle 27n^{2}u\lVert A\rVert \lVert B\rVert +O(u^{2})}{\displaystyle 27n^{2}u\lVert A\rVert \lVert B\rVert +O(u^{2})}보다 작음이 알려져 있다. 이는 일반적인 행렬 곱셈보다 더 큰 오차이다.[1]
