### 소스 코드

```java
class Solution {
    public int[] solution(int[] arr) {
        
        int target = 1;

        while (target < arr.length) {
            target *= 2;
        }

        int[] answer = new int[target];
        
        for (int i = 0; i < arr.length; i++) {
            answer[i] = arr[i];
        }
        
        return answer;
    }
}
```

---

### 왜 못 풀었는가?

처음에 2의 거듭제곱을 어떻게 구해야할까...? 를 계속 생각하다가 거듭제곱을 구하는 방식을 자꾸 기존 arr 의 길이와 비교를 하려고 했다.. arr의 길이가 2의 거듭제곱이 아니라면~~ 이라는 식으로 ㅠㅠ

그러다가 거듭제곱 구하는 글을 찾다가 두둥!!! 새로운 변수를 선언하고 그 변수가 arr의 길이보다 작을 경우 계속 2를 곱해서 거듭제곱 수를 찾으면 되는 거였.... 후..

그래서 바로 2의 거듭제곱을 만족하는 가장 작은 길이를 구하고 그 길이로 변수를 선언 후 원래 arr를 그대로 넣었다. 넣지 않은 부분은 기본적으로 0 으로 설정 되기 때문에 집어 넣기만 하면 된다.

Arrays.copy() 같은 메서드를 사용할 수 있지만 직접 구현하는게 더 속도가 빠르지 않을까 싶어서 for 를 사용.
