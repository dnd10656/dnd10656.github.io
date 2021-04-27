# 중간고사 과제
## Strassen Alogorithm
---
## 이종웅

---
### Strassen Alogorithm

**아래 A, B 행렬과 두 행의 곱의 결과 C가 있다고 했을 때 (A, B는 정사각행렬)
![a=](https://wikimedia.org/api/rest_v1/media/math/render/svg/41c6337190684aff7b69f124226d6e62d79ebca5)  

**행렬의 곱은 다음과 같으며, 총 8번의 곱셈과 4번의 덧셈으로 연산한다.  
![C11](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d91fa79d27697a5c6551698c1a83a3d5837c57b)  
![C12](https://wikimedia.org/api/rest_v1/media/math/render/svg/a08bea24eec9422cda82e6e04af1d96fc6822038)  
![C21](https://wikimedia.org/api/rest_v1/media/math/render/svg/7adffe97db091ce8ba231352b3721bbe261985ca)  
![C22](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b40ed74cf54465d8e54d09b8492e50689928313)  

**Strassen에서 행렬의 곱셈을 더하기 연산으로 풀어 각 원소를 구할 수 있는 M이라는 연산 행렬로 표현한다.  
이러한 M행렬은 7번의 곱셈과 10번의 덧셈 연산으로 나타낼 수 있으며 아래와 같이 표현한다.  
![M1](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)  
![M2](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)  
![M3](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)  
![M4](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)  
![M5](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)  
![M6](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)  
![M7](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)  
  
**최종 C행렬은 M행렬의 덧셈 연산으로 이루어져 있으며 전체 곱셈을 일곱 번의 곱셈과 18번의 덧셈으로 처리할 수 있다.  
큰 행렬에 대해서는 행렬의 곱셈이 덧셈보다 더 많은 시간을 필요로 하기 때문에 덧셈을 더 하는 대신 곱셈을 덜 하는 것이  
전체적으로 효율적이다.  

![c11](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)  
![c12](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)  
![c21](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)  
![c22](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)  
---
### Strassem Alogorithm java code

```java
import java.util.Scanner;
```
** A, B 행렬을 사용자가 입력하기 위해서 import를 통해 java.util 패키지에 포함되어 있는 Scanner을 호출했습니다.  

```java
public class Strassen {
public void strassen (int n, int[][] A, int[][] B, int[][] C){
        int i,j;
        int M1[][] = new int[n / 2][n / 2];
        int M2[][] = new int[n / 2][n / 2];
        int M3[][] = new int[n / 2][n / 2];
        int M4[][] = new int[n / 2][n / 2];
        int M5[][] = new int[n / 2][n / 2];
        int M6[][] = new int[n / 2][n / 2];
        int M7[][] = new int[n / 2][n / 2];
        int TempA[][] = new int[n / 2][n / 2];
        int TempB[][] = new int[n / 2][n / 2];
        if (n <= 2) {                        // 2 × 2 행렬이 되면 결과 행렬에 계산하여 넣는다.
            C[0][0] = A[0][0] * B[0][0] + A[0][1] * B[1][0];
            C[0][1] = A[0][0] * B[0][1] + A[0][1] * B[1][1];
            C[1][0] = A[1][0] * B[0][0] + A[1][1] * B[1][0];
            C[1][1] = A[1][0] * B[0][1] + A[1][1] * B[1][1];
        } else {            // M1을 계산한후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i][j] + A[i + n / 2][j + n / 2];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i][j] + B[i + n / 2][j + n / 2];
            strassen(n / 2, TempA, TempB, M1);     // M2 계산 후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i + n / 2][j] + A[i + n / 2][j + n / 2];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i][j];
            strassen(n / 2, TempA, TempB, M2);
            // M3 계산후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i][j];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i][j + n / 2] - B[i + n / 2][j + n / 2];
            strassen(n / 2, TempA, TempB, M3);
            // M4 계산후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i + n / 2][j + n / 2];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i + n / 2][j] - B[i][j];
            strassen(n / 2, TempA, TempB, M4);
            // M5 계산후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i][j] + A[i][j + n / 2];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i + n / 2][j + n / 2];
            strassen(n / 2, TempA, TempB, M5);
            // M6 계산 후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i + n / 2][j] - A[i][j];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i][j] + B[i][j + n / 2];
            strassen(n / 2, TempA, TempB, M6);
            // M7 계산 후 strassen 메소드를 호출
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempA[i][j] = A[i][j + n / 2] - A[i + n / 2][j + n / 2];
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    TempB[i][j] = B[i + n / 2][j] + B[i + n / 2][j + n / 2];
            strassen(n / 2, TempA, TempB, M7);
            //C11 계산
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    C[i][j] = M1[i][j] + M4[i][j] - M5[i][j] + M7[i][j];
            //C12 계산
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    C[i][j + n / 2] = M3[i][j] + M5[i][j];
            // C21 계산
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    C[i + n / 2][j] = M2[i][j] + M4[i][j];
            // C22 계산
            for (i = 0; i < n / 2; i++)
                for (j = 0; j < n / 2; j++)
                    C[i + n / 2][j + n / 2] = M1[i][j] + M3[i][j] - M2[i][j] + M6[i][j];
        }
    }
 ```  
**Strassen 행렬 계산법에 따라 차례대로 계산하였습니다.

```java
    public static void Strassen_init (int n, int[][] A, int[][] B, int[][] C) {
        for(int i=0 ; i<n ; i++){
            for(int j=0 ; j<n ; j++){
                A[i][j] = (int)(Math.random() * 10+1);       // 행렬 A에 값을 할당
                B[i][j] = (int)(Math.random() * 10+1);       // 행렬 B에 값을 할당
                C[i][j] = 0;					                            // 행렬 C에 값을 할당
            }
        }
    }  
  ```  
    
**행렬 초기화 구문입니다. 원래대로라면 이와같이 A와 B를 Math.random() 함수로 랜덤하게 지정하고 싶었습니다.  

```java
 public static void main(String args[]) {
        long start = System.currentTimeMillis();
        Scanner scanner = new Scanner(System.in);
        Strassen s = new Strassen();
        int n = 2;
        int[][] A = new int[n][n];
        int[][] B = new int[n][n];
        int[][] C = s.strassen(A,B);

        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                A[i][j] = scanner.nextInt();
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                B[i][j] = scanner.nextInt();
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
               System.out.print(C[i][j]+" ");
                       System.out.println();

                long end = System.currentTimeMillis();

                System.out.println("수행시간 : "+ (end-start)+ "ms");
           }
        }
    }
}
```  
**성능분석을 위해 long start = System.currentTimeMillis(); long end = System.currentTimeMillis(); System.out.println("수행시간 : "+ (end-start)+ "ms"); 을 사용하였습니다.



**원래 목적은 A, B를 랜덤함수로 호출하여 출력하는 것이었는데 코드 오류가 너무 발생하여 Scanner을 이용하여 A, B를 출력하게 되었습니다.
여전히 코드 오류가 있어 오류가 발생하지만, 정말 많이 노력했습니다...
