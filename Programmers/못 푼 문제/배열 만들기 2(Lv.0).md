### 소스 코드

```java
import java.util.ArrayList;

class Solution {
    public int[] solution(int l, int r) {
        
        ArrayList<Integer> list = new ArrayList<>();
        
        for (int i = l; i <= r; i++) {
            boolean contains = String.valueOf(i).matches("[05]+");
            if (contains) {
                list.add(i);
            }
        }

        if (list.isEmpty()) {
            return new int[]{-1};
        }
        
        int[] answer = new int[list.size()];
        
        for (int i = 0; i < answer.length; i++) {
            answer[i] = list.get(i);
        }
        
        return answer;
    }
}
```

---

### 또 정규식...

정규식을 활용해서 풀어야 한다까지는 파악!! 그렇다면 어떻게 정규식을 작성해야 하는가?

처음에는 String.matches() 를 사용하지 않고 contains 를 사용했다. 그리고 정규식도 `String.valueOf(i).contains("[\"05\"]");` 이렇게.... 

정규식은 도대체 어떻게 쓰는 거야!!! 하고 결국 검색해서 문제를 해결했다 ㅠㅠ 

[여기](https://megak.tistory.com/158)에서 정규식에 대한 해석과 사용한 메서드에 대한 해석을 쉽게 파악 할 수 있었다.

