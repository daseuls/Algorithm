# ☑️ 문제

프로그래머스 Lv.1 없는 숫자 더하기 (7/6)

<img width="798" alt="스크린샷 2022-07-06 오후 4 09 36" src="https://user-images.githubusercontent.com/71131248/177490773-17424fed-6a58-442e-987e-b95470ddc76a.png">

# ☑️ 문제 접근

1. 0부터 9까지 반복문을 돌며 배열이 그 값을 포함하는 지 확인 후 값을 계산한다.

# ☑️ 코드

```javascript
function solution(numbers) {
  let sum = 0;
  for (let i = 0; i <= 9; i++) {
    if (!numbers.includes(i)) {
      sum += i;
    }
  }
  return sum;
}
```

## 실행 결과

테스트 1 〉 통과 (0.04ms, 30.1MB)<br>
테스트 2 〉 통과 (0.04ms, 30MB)<br>
테스트 3 〉 통과 (0.04ms, 30.2MB)<br>
테스트 4 〉 통과 (0.04ms, 30.1MB)<br>
테스트 5 〉 통과 (0.04ms, 30MB)<br>
테스트 6 〉 통과 (0.04ms, 30.1MB)<br>
테스트 7 〉 통과 (0.04ms, 30.1MB)<br>
테스트 8 〉 통과 (0.05ms, 29.7MB)<br>
테스트 9 〉 통과 (0.04ms, 30MB)

# ☑️ 문제 풀이

1. sum을 0으로 초기화해준다.
2. 0부터 9까지 반복하며 includes 메서드를 통해 numbers 배열안에 값이 들어있는지 확인한다.
3. 만약 값이 들어있지 않다면 sum에 그 값을 더해준다.
4. sum을 리턴한다.
