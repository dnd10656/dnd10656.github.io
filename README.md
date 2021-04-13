# greed2
  
  
#### 팀원: 강현규, 류연수, 이종웅
---
  
  
### 코드설명  

```import java.util.Arrays;
import java.util.Comparator;
```
> 배열을 다루기 위해 `util.java.` 패키지에서 `Arrays` 클래스를 불러온다.  
> Arrays.sort() 메소드의 기준으로 삽입해줄 정렬 기준을 가진 `Comparator` 클래스도 불러온다.
---

```Java
public class Leejongwoong {
    public static double woong(int[] w, int[] v, int c) {
        temval[] V = new temval[w.length];
        for (int i = 0; i < w.length; i++) {
            V[i] = new temval(w[i], v[i], i); }
        Arrays.sort(V, new Comparator<temval>() {
            public int compare(temval o1, temval o2) {
                return o2.a.compareTo(o1.a); }});
        double tv = 0;
```
>`temval`의 최대값을 구하고 `a`의 무게와 가치를 비교하여 내림차순으로 정렬한다.  
---

```Java
        for (temval i : V) {
            int wt = (int) i.w;
            int vl = (int) i.v;
            if (c - wt >= 0) {
                c = c - wt;
                tv += vl;
            } else {
                double f = ((double) c / (double) wt);
                tv += (vl * f);
                c = (int) (c - (wt * f));
                break; }
        }
        return tv;
    }
```
>` int[] w = { 10, 20, 30, 40 }; int[] v = { 20, 50, 100, 120 };`에서의 최대 가치 `w 40, v 120`을 먼저 배낭에 넣은 뒤 10만큼의 남은 무게를 물건들의 무게와 가치를 비교하여 무게가 초과된다면 무게와 가치를 비례해 줄여 `c`의 값인 50에 맞춰 배낭에 넣어준다.  
>`c(배낭 안에 들어갈 수 있는 최대 무게)`의 값에서 `wt(물건들의 무게)`뺀 값이 0보다 크거나 같으면(0이라면) `c = c - wt;`이며,
`tv`의 값은 `w`의 `v(물건들의 가치)`이다.
> `c - wt`의 값이 0보다 작다면(물건들의 무게가 배낭에 넣을 수 있는 무게를 초과한다면) 초과하는 물건들 중에서
> `c - wt`가 0가 되도록 가치가 높은 물건의 물건의 무게와 가치를 비례하여 줄여 `tv`에 저장해준 뒤 리턴해준다.
---

```Java
   static class temval {
        Double a;
        double w, v, i2;

        public temval(int w, int v, int i2) {
            this.w = w;
            this.v = v;
            this.i2 = i2;
            a = new Double((double) v / (double) w);

        }
    }
    public static void main(String[] args) {
        int[] w = {10, 40, 20, 30};
        int[] v = {60, 40, 100, 120};
        int c = 50;
```
>`temval`의 함수 `a = new Double((double)v / (double)w);`를 통해 `w(무게)`와 `v(가치)`를 비교하여  `public class Leejongwoong Comparator`정렬에서 내림차순으로 정렬을 한다.
> `main` 함수에서 `w(물건들 무게)`와 `v(물건들 가치)`, `c(배낭의 들어갈 수 있는 최대 무게)`의 값을 정하였다.
---

```Java
        double maxValue = woong(w, v, c);
        System.out.print("배낭에 담을 수 있는 최대 물건의 최대 가치 = "
                + maxValue);
    }
}

```
>`woong`함수를 호출하여 `maxv`에 저장 후 `print`해준다.
>이 때 `woong`함수는 `Comparator a`함수에 의해서 내림차순으로 된 물건들을 `for`문으로 인해 가치가 가장 큰 값을 먼저 배낭에 넣어준 뒤 나머지 무게에 대해 무게와 가치를 비교하여 가장 높은 가치의 물건을 `c` 값 50에 맞춰서 넣어준다.
---

###결과값

>배낭에 담을 수 있는 최대 물건의 최대 가치 = 160.0
---
