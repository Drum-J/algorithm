### 소스 코드

```java
import java.math.BigInteger;

class Solution {
    public String solution(String a, String b) {
        BigInteger numA = new BigInteger(a);
        BigInteger numB = new BigInteger(b);
        BigInteger sum = numA.add(numB);
        
        String answer = sum.toString();
        return answer;
    }
}
```

---

### 왜 못 풀었는가?

숫자가 문자열로 주어지고 해당 숫자를 더해서 다시 문자열로 반환해야 한다. 문자열의 길이가 최대 100,000이기 때문에 Integer나 Long 을 사용해도 에러가 나온다.

그래서 어떻게 풀어야 하징...? 하다가 문자열을 짤라서 해야하나...? 근데 그래도 100,000 길이의 숫자를 계속 하기에는 문제가 있다고 판단.

다른 방법을 찾아보다가 결국 [해당 블로그](https://tiny-stone.com/359)를 참조 했다.

BigInteger 는 문자열을 그대로 받아서 내부에서 숫자로 바꾸고 사칙연산에 대한 메서드도 제공한다고 한다.
