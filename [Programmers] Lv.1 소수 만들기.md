# ☑️ 문제

<img width="717" alt="스크린샷 2022-06-17 오후 4 47 06" src="https://user-images.githubusercontent.com/71131248/174251704-c28a60a0-9255-4794-9d42-193be5783b58.png">

# ☑️ 코드

```javascript
function solution(nums) {
  const result = [];

  const isPrime = (n) => {
    if (n === 1) return false;
    for (let i = 2; i < n; i++) {
      if (n % i === 0) return false;
    }
    return true;
  };

  for (let i = 0; i < nums.length - 2; i++) {
    for (let j = i + 1; j < nums.length - 1; j++) {
      for (let z = j + 1; z < nums.length; z++) {
        const sum = nums[i] + nums[j] + nums[z];
        if (isPrime(sum)) {
          result.push(sum);
        }
      }
    }
  }
  return result.length;
}
```

## 실행 결과

테스트 1 〉 통과 (2.50ms, 31.9MB) <br>
테스트 2 〉 통과 (2.71ms, 31.8MB)<br>
테스트 3 〉 통과 (0.99ms, 32.5MB)<br>
테스트 4 〉 통과 (0.32ms, 30MB)<br>
테스트 5 〉 통과 (2.73ms, 31.8MB)<br>
테스트 6 〉 통과 (4.35ms, 31.7MB)<br>
테스트 7 〉 통과 (1.14ms, 31.7MB)<br>
테스트 8 〉 통과 (8.28ms, 32MB)<br>
테스트 9 〉 통과 (2.62ms, 31.8MB)<br>
테스트 10 〉 통과 (8.06ms, 32MB)<br>
테스트 11 〉 통과 (0.16ms, 30MB)<br>
테스트 12 〉 통과 (0.11ms, 29.9MB)<br>
테스트 13 〉 통과 (0.17ms, 29.9MB)<br>
테스트 14 〉 통과 (0.14ms, 30.1MB)<br>
테스트 15 〉 통과 (0.10ms, 30MB)<br>
테스트 16 〉 통과 (16.42ms, 31.8MB)<br>
테스트 17 〉 통과 (3.04ms, 31.9MB)<br>
테스트 18 〉 통과 (1.39ms, 31.8MB)<br>
테스트 19 〉 통과 (0.15ms, 30.1MB)<br>
테스트 20 〉 통과 (18.67ms, 32.1MB)<br>
테스트 21 〉 통과 (16.89ms, 32MB)<br>
테스트 22 〉 통과 (0.45ms, 29.5MB)<br>
테스트 23 〉 통과 (0.11ms, 29.8MB)<br>
테스트 24 〉 통과 (14.90ms, 32.6MB)<br>
테스트 25 〉 통과 (15.21ms, 31.8MB)<br>
테스트 26 〉 통과 (0.11ms, 30MB)<br>

# ☑️ 문제 풀이

1. 가장 먼저 소수인지 아닌지를 판단할 수 있는 isPrime 함수를 만든다.
2. 소수는 1을 제외하고 1과 자기 자신으로 밖에 나누어 떨어지지않는 숫자이다.
3. 인자로 들어온 n이 1이면 소수가 아니므로 false를 리턴한다.
4. i는 2부터 시작해서 n보다 작을때까지 숫자가 커지고, 그만큼 반복을 한다. n을 i로 나누었을때 나누어 떨어지면 false를 리턴한다.
5. 만약 n보다 작은 모든 수로 나누었을때 나누어떨어지지 않는다면 소수이다. 그러므로 true를 리턴한다.
6. 이제 숫자를 더한 합이 소수인 경우의 수를 구해보자.
7. 3개의 수를 더해야 하므로 3중 for문을 사용했다. 서로 다른 3개를 골라서 더해야 하므로 반복문을 돌릴때 시작하는 index는 반복하면서 그 전의 index보다 1이 더 크다.
8. 또 반복을 할 횟수는 1보다 더 크다면 그 인덱스는 배열의 길이보다 줄여서 반복한다.
9. 3중 for문을 통해 반복한 값들을 더한 후 소수인지 판단하는 isPrime 함수를 통해 소수인 경우만 result에 담는다.
10. result의 length를 리턴한다.
