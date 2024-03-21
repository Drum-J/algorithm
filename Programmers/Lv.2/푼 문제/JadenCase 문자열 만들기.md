### 소스 코드

[문제](https://school.programmers.co.kr/learn/courses/30/lessons/12951)

```java
class Solution {
    public String solution(String s) {
        
        StringBuilder answer = new StringBuilder();

        String[] split = s.split("");

        int start = 0;
        for (int i = 0; i < split.length; i++) {
            if (split[i].equals(" ")) {
                answer.append(" ");
                start = 0;
            } else {
                if (start == 0) {
                    answer.append(split[i].toUpperCase());
                    start++;
                } else {
                    answer.append(split[i].toLowerCase());
                }
            }
        }
        
        return answer.toString();
    }
}
```

![image](https://github.com/Drum-J/algorithm/assets/102205699/aa21484b-2508-4f3d-b56c-acb39b823cd3)

---

### 문제 풀이

처음에는 split을 공백으로 했다. `.split(" ")` 이런 식으로. 문제에 제한 사항에 공백이 연속해서 나올 수도 있다해서 여러 공백을 하나로 바꾸기 위해 replaceAll 을 사용해서 공백이 연속해서 나올 경우 하나의 공백으로 바꿔주기도 하고 앞과 뒤에 공백을 없애기 위해
trim을 사용하기도 했다.

근데 이것저것 다 사용해서 문제를 제출하니 자꾸 8번에서 실패를 해서 질문하기를 읽어봤다.

다음과 같은 예제가 주어질 경우에 실패를 하게 되는 것! `String s = "  for the what 1what  ";`

앞뒤로 공백이 있고 해당 공백이 연속해서 나오기도 한다. 문제에 따로 적혀있지 않았기 때문에 생각을 못했는데 공백이 나올 경우 그냥 그대로 공백을 돌려줘야 했던 것...

그래서 어떻게 하지...? 하다가 그냥 아무조건 없이 split을 하고 첫 글자만 toUpperCase 를 사용하기로 했다. 그렇다면 어떻게 판단하는게 좋을까? 따로 `int start` 라는 변수를 사용해서 공백을 만나면 0으로 바꾸고 처음 만나는 글자가 올 경우 start++ 을 사용해서 첫 글자는 UpperCase로 만들도록 코드를 작성했다.

이렇게 하면 for 문이 엄청나게 길어져서 시간 초과가 나오지 않을까... 했는데 문자열의 최대 길이가 200이기 때문에 시간은 크게 신경 쓸 필요가 없었다.

공백일 경우 공백을 그대로 돌려줘야 한다는 것을 생각하지 못해서 조금 애를 먹은 문제였다.
