### 소스 코드

[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42747)

```java
import java.util.Arrays;

class Solution {
    public int solution(int[] citations) {
        Arrays.sort(citations);

        int answer = 0;
        for (int i = 0; i < citations.length; i++) {
            int h = citations.length - i; // 인용된 논문의 수

            if (citations[i] >= h) {
                answer = h;
                break;
            }
        }
        
        return answer;
    }
}
```

---

### 풀이 방법

해당 문제를 처음 봤을 때는 정렬을 한 이후 중간 인덱스 값을 기준으로 좌우로 왔다갔다 하면서 값을 찾을 생각이었다.

> 어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

이 조건에서 h번 이상 인용된 논문 중 중간 값을 중간 인덱스에서 바로 찾을 수 있다고 판단했기 때문.. 근데 이 이후 어떻게 오른쪽,왼쪽으로 이동할 지 몰라서 좀 많이 해매다가 결국 풀이를 봐버렸다.

생각보다 너무 단순한 풀이에 깜짝 놀람... ㅠㅠ 

정렬한 이후 해당 배열을 돌면서 인용된 논문의 수는 1씩 줄이고 배열의 값과 크거나 같아지는 상황이 발생했을 때 바로 `break` 이후 값을 return 하는 것..!

배열이 정렬된 이후 값이 {0,1,3,5,6} 이라고 한다면 `for`문을 순서대로 돌면

1. 0번 인용, h = 5
2. 1번 인용, h = 4
3. 3번 인용, h = 3
4. 5번 인용, h = 2
5. 6번 인용, h = 1

이 되기 때문에 3이 이 과학자의 h-index가 되는 것이다.

레벨2라서 너무 어렵게 생각한 것이 문제인 것 같다. 간단하게 구현할 수 있으면 그것부터 해보고 다음으로 넘어가도록 해보자!
