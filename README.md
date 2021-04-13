# greed2
  
  
#### 팀원: 강현규, 류연수, 이종웅
  
---
  
  
### 코드설명  

```import java.util.Arrays;
import java.util.Comparator;```
-> 배열을 다루기 위해 `util.java.` 패키지에서 `Arrays` 클래스를 불러온다.
-> Arrays.sort() 메소드의 기준으로 삽입해줄 정렬 기준을 가진 `Comparator` 클래스를 불러온다.
---

```Java
public class FractionalKnapSack { // 최대값을 구하는 함수
    private static double getMaxValue(int[] wt, int[] val, int c) {
        ItemValue[] iVal = new ItemValue[wt.length];
        for (int i = 0; i < wt.length; i++) {
            iVal[i] = new ItemValue(wt[i], val[i], i); }
        Arrays.sort(iVal, new Comparator<ItemValue>() {       // 값별로 항목 정렬
            public int compare(ItemValue o1, ItemValue o2) {
                return o2.cost.compareTo(o1.cost); }});
        double totalValue = 0;

        for (ItemValue i : iVal) {
            int w = (int)i.wt;
            int v = (int)i.val;
            if (c - w >= 0) { // 이 중량은 다음과 같이 선택할 수 있다.
                c = c - w;
                totalValue += v; }
            else {
                double fraction = ((double)c / (double)w); // 전체를 선택할 수 없다.
                totalValue += (v * fraction);
                c = (int)(c - (w * fraction));
                break; }
        }
        return totalValue;
    }

    static class ItemValue {    // 항목 값 클래스
        Double cost;
        double wt, val, i2;

        public ItemValue(int wt, int val, int i2)// 항목item 값 함수
        {
            this.wt = wt;
            this.val = val;
            this.i2 = i2;
            cost = new Double((double)val / (double)wt);
        }
    }
    public static void main(String[] args) { // 운전자 코드
        int[] wt = { 10, 40, 20, 30 };
        int[] val = { 60, 40, 100, 120 };
        int c= 50;

        double maxValue = getMaxValue(wt, val, c);       // 함수 호출
        System.out.println("배낭에 담을 수 있는 최대 물건의 최대 가치 = "
                + maxValue);
    }
}

