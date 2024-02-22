### 소스 코드
```java
class Solution {
    public String[] solution(String my_string) {
        
        return my_string.trim().split("\\s+");
    }
}
```

---

### 왜 못 풀었는가

여러 공백을 하나로 처리할 수 있는 방법을 몰랐다.. \\s 로 하면 공백을 여기에 + 를 붙이면 하나 이상의 공백을 처리할 수 있다고 한다..

정규식에 대해서도 조금씩 찾아보고 해야겠다 ㅠㅠ

추가로 \\S 이렇게 대문자 S의 경우에는 공백을 제외한 문자라고 한다.
