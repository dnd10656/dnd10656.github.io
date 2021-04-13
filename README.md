# greed2

## 팀원: 강현규, 류연수, 이종웅

---

# 코드설명  

import java.util.Scanner;

Scanner를 사용하기 위해서 java.util. 패키지에서 불러온다.

---

```javascript
public class FractionalKnapSack
{
    public static void main(String args[])
    {
        Scanner sc = new Scanner(System.in);
        int i, w, j=0, m, n;
        float v=0,max;
        int array[][]=new int[20][20];
        System.out.print("물건들의 개수를 입력:");
        n=sc.nextInt();
        System.out.print("물건들의 무게를 입력:");
        for(i=0;i<n;i++)
            array[0][i]=sc.nextInt();
        System.out.print("물건들의 가치를 입력:");
        for(i=0;i<n;i++)
            array[1][i]=sc.nextInt();
        System.out.print("배낭에 담을 수 있는 최대 무게를 입력:");
        w=sc.nextInt();
        ```
        
        
        ```javascript
        m=w;
        while(m>=0)
        {
            max=0;
            for(i=0;i<n;i++) {
                if(((float)array[1][i])/((float)array[0][i])>max) {
                    max=((float)array[1][i])/((float)array[0][i]);
                    j=i; } }
            if(array[0][j]>m) {
                System.out.println("배낭에 넣을 "+  (j+1) + " 번 물건의 무게는 " +m);
                v+=m*max;
                m=-1; }
            else {
                System.out.println("배낭에 넣을 "+ (j+1) + " 번 물건의 무게는 " + array[0][j]);
                m-=array[0][j];
                v+=(float)array[1][j];
                array[1][j]=0; } }
        System.out.println("배낭에 넣은 물건들의 총 가치는: " + v);
        sc.close();
    }
}
```
