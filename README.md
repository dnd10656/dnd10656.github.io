# 중간고사 과제
## Strassen Alogorithm

## 이종웅


### Strassen Alogorithm

아래 A, B 행렬과 두 행의 곱의 결과 C가 있다고 했을 때 (A, B는 정사각행렬이다.)
![a=](https://wikimedia.org/api/rest_v1/media/math/render/svg/41c6337190684aff7b69f124226d6e62d79ebca5)  

행렬의 곱은 다음과 같으며, 총 8번의 곱셈과 4번의 덧셈으로 연산된다.  
![C11](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d91fa79d27697a5c6551698c1a83a3d5837c57b)  
![C12](https://wikimedia.org/api/rest_v1/media/math/render/svg/a08bea24eec9422cda82e6e04af1d96fc6822038)  
![C21](https://wikimedia.org/api/rest_v1/media/math/render/svg/7adffe97db091ce8ba231352b3721bbe261985ca)  
![C22](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b40ed74cf54465d8e54d09b8492e50689928313)  

Strassen에서 행렬의 곱셈을 더하기 연산으로 풀어 각 원소를 구할 수 있는 M이라는 연산 행렬로 표현한다.  
이러한 M행렬은 7번의 곱셈과 10번의 덧셈 연산으로 나타낼 수 있으며 아래와 같이 표현한다.  
![M1](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)  
![M2](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)  
![M3](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)  
![M4](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)  
![M5](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)  
![M6](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)  
![M7](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)  
 
최종 C행렬은 M행렬의 덧셈 연산으로 이루어져 있으며 전체 곱셈을 일곱 번의 곱셈과 18번의 덧셈으로 처리할 수 있다.  
큰 행렬에 대해서는 행렬의 곱셈이 덧셈보다 더 많은 시간을 필요로 하기 때문에 덧셈을 더 하는 대신 곱셈을 덜 하는 것이  
전체적으로 효율적이다.
![c11](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)  
![c12](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)  
![c21](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)  
![c22](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)  

참고자료 출처: https://ko.wikipedia.org/wiki/%EC%8A%88%ED%8A%B8%EB%9D%BC%EC%84%BC_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98
