### 소스 코드

```java
import java.util.*;

class Solution {
    public String solution(String[] survey, int[] choices) {
        
        Map<String, Integer> mbti = new HashMap<>();
        mbti.put("R", 0);
        mbti.put("T", 0);

        mbti.put("C", 0);
        mbti.put("F", 0);

        mbti.put("J", 0);
        mbti.put("M", 0);

        mbti.put("A", 0);
        mbti.put("N", 0);

        for (int i = 0; i < survey.length; i++) {
            if (choices[i] > 4) {
                String substring = survey[i].substring(1,2);
                Integer score = mbti.get(substring);
                mbti.put(substring, score + (choices[i] - 4));
            } else {
                String substring = survey[i].substring(0,1);
                Integer score = mbti.get(substring);
                mbti.put(substring, score + (4 - choices[i]));
            }
        }

        StringBuilder sb = new StringBuilder();

        sb.append(mbti.get("R") >= mbti.get("T") ? "R" : "T");
        sb.append(mbti.get("C") >= mbti.get("F") ? "C" : "F");
        sb.append(mbti.get("J") >= mbti.get("M") ? "J" : "M");
        sb.append(mbti.get("A") >= mbti.get("N") ? "A" : "N");
        
        return sb.toString();
    }
}
```

---

### 풀이

해당 값을 어디에 저장해야 할 지 몰라서 일단 Map을 사용하기로 했다. 해당 유형에 맞게 점수를 넣어야 하기 때문   
유형별로 이미 사전순으로 정의가 되어있기 때문에 배열을 사용해 볼까도 했는데 유형에 맞는 점수를 어떻게 넣어야 할 지 생각이 안나서... 그냥 Map 사용 ㅎㅎ 

그리고 `map.get()` 을 사용해서 점수를 가져와 비교를 한 후 맞는 Key 값을 넘겨주기 위해 StringBuilder 를 사용한 하드 코딩을 했다. 흠흠.. 맘에 쏙 들진 않지만 아직까진 다른 방법을 생각 못했다.

### 문제점

제일 처음 제출한 코드에는 `Integer score` 부분이 없어서 유형별로 점수를 바로바로 `put()` 해버렸기 때문에 테스트 실패가 났다! 오잉..??? 뭐야 했는데 손으로 풀때는 get을 해서 점수를 가져와 놓고 코드에 그 부분을 작성 안한 것 ㅋㅋㅋㅋ

---

### 결과
![image](https://github.com/Drum-J/algorithm/assets/102205699/e84ff8bc-1bd6-49ff-a053-a8f311483d74)

속도는 나름 빠르고 메모리는... 음... 메모리 맞나? 여튼 좀 크넹

