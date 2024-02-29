### 소스 코드
```java
class Solution {
    public int solution(int n, int k) {
        StringBuilder number = new StringBuilder();

        while (n != 0) {
            int i = n % k;
            number.append(i);
            n = n / k;
        }

        String binary = number.reverse().toString();
        String[] split = binary.split("[0]+");

        int answer = 0;
        
        for (int i = 0; i < split.length; i++) {
            if (isPrime(split[i])) {
                answer++;
            }
        }
        
        return answer;
    }
    
    private static boolean isPrime(String s) {
        long n = Long.parseLong(s);
        if (n <= 1) {
            return false;
        }

        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```

---

### 왜 못 풀었는가?

진수를 구하는 것도 잘 했고, 문제를 읽다보니 0으로 그냥 나눠서 체크해도 될 것 같은데..?? 0으로 split 쳐버리자!! 까지도 잘 했고...

그렇게 구한 문자열 배열을 사용해서 for 문도 잘 돌렸고!!! 뭐가 문제였을까??

그건 바로 소수(Prime Number) 구하기... 소수 구하는 방법을 그저 이름이랑 방법만 들어본 `에라토스테네스의 체` 이 녀석을.. 어떻게 자바로 구현하는 지 몰랐다 ㅠㅠ 

---

### 소수 구하기 (Prime Number)

그래서 결국 소수 구하는 방법을 구현하기 위해 구글링을 했다... ㅠㅠ 

총 3가지의 방법이 있다고 한다. [여기 블로그](https://sfida.tistory.com/28)에 아주 잘 정리가 되어있다.

1. N보다 작은 수로 나누기 -> 시간 복잡도 O(N)
2. N의 제곱근 보다 작은 수로 나누기 -> 시간 복잡도 O(root(N))
3. 에라토스테네스의 체를 사용하기 -> 시간 복잡도 O(N log(log N))

이 중에 나는 2번 N의 제곱근 보다 작은 수로 나누기를 사용하기로 했다. 시간 복잡도는 에라토스테네스의 체 보다는 늦지만.. 코드를 살펴보면 엄청 간단하게 구현할 수 있기 때문이다.

위의 소스 코드에서 작성한 `isPrime()` 부분이 그 코드 이다.

또!! 1은 소수가 아니라는 점을 알고가자. 오래되다 보니까 1과 자기 자신만을 약수로 가진 수인데 자꾸 1도 소수라고 생각해서 왜 1은 제외하지..? 하고 있었다.. ㅋㅋㅋ 

그래서 for 를 보면 2부터 시작해서 Math.sqrt(n) 과 같을 때 까지 i를 계속 1씩 증가 시키고 있다. 그리고 if를 사용해서 나누어 떨어진다면 해당 수로 약수로 가지고 있기 때문에 바로 false 를 반환하고 있다.

이렇게 코드를 수행하면 1과 자기 자신만 약수로 가지는 경우에만 true 를 반환하기 때문에 answer를 (소수의 갯수) 정확하게 구할 수 있다!

### 소수 구하는 방법만 알았으면 풀 수 있었는데!!!!!
