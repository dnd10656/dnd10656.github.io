# 중간고사 과제
## Strassen Alogorithm

## 이종웅


### Strassem Alogorithm 이란?

선형대수학에서 슈트라센 알고리즘은 독일의 수학자 폴커 슈트라센(Volker Strassen)이 1969년에 개발한 행렬 곱셈 알고리즘이다.
정의에 따라 n×n 크기의 두 행렬을 곱하면 O(n3)의 시간이 소요되지만 이 알고리즘은 대략 O(n2.807)의 시간이 소요된다.[\^myfootnote]


![C=AB](https://wikimedia.org/api/rest_v1/media/math/render/svg/f4c680ec4a32379114e0326ba69b179881b69e8e)  

![ABC](https://wikimedia.org/api/rest_v1/media/math/render/svg/e2948b2c6caf12770b217310b956b23abdc80380)  

![C11](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d91fa79d27697a5c6551698c1a83a3d5837c57b)  
![C12](https://wikimedia.org/api/rest_v1/media/math/render/svg/a08bea24eec9422cda82e6e04af1d96fc6822038)  
![C21](https://wikimedia.org/api/rest_v1/media/math/render/svg/7adffe97db091ce8ba231352b3721bbe261985ca)  
![C22](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b40ed74cf54465d8e54d09b8492e50689928313)  

![M1](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)  
![M2](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)  
![M3](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)  
![M4](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)  
![M5](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)  
![M6](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)  
![M7](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)  

![c11](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)  
![c12](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)  
![c21](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)  
![c22](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)  
