# ☑️ 문제

프로그래머스 레벨 1. 카펫 (완전 탐색) (7/6)
<img width="939" alt="스크린샷 2022-07-06 오후 3 45 12" src="https://user-images.githubusercontent.com/71131248/177486343-88a71880-bb8f-49eb-b425-0768bbf955d0.png">

# ☑️ 문제 접근

1. brown과 yellow를 더하면 카펫의 합계이다.
2. 곱하면 카펫의 합계가 되는 수 각각에서 2를 제외한 값을 곱하면 yellow의 값이 나와야 한다.
3. 먼저 카펫의 합계의 약수들을 구한다.
4. 약수들 중 2를 뺀 값을 각각 곱했을 때 yellow인 경우를 찾는다.

# ☑️ 코드

```javascript
function solution(brown, yellow) {
  const sum = brown + yellow;
  const arr = [];

  for (let i = 1; i <= sum / 2; i++) {
    if (sum % i === 0) {
      arr.push(i);
    }
  }
  arr.push(sum);

  const result = [];
  for (let i = 0; i <= Math.ceil(arr.length / 2 - 1); i++) {
    if ((arr[i] - 2) * (arr[arr.length - i - 1] - 2) === yellow) {
      result.push(arr[arr.length - i - 1], arr[i]);
    }
  }
  return result;
}
```

## 실행 결과

테스트 1 〉 통과 (0.07ms, 30.3MB) <br/>
테스트 2 〉 통과 (0.09ms, 29.8MB) <br/>
테스트 3 〉 통과 (4.11ms, 32.8MB)<br/>
테스트 4 〉 통과 (0.17ms, 30.1MB)<br/>
테스트 5 〉 통과 (0.32ms, 30.2MB)<br/>
테스트 6 〉 통과 (2.87ms, 33MB)<br/>
테스트 7 〉 통과 (4.42ms, 32.8MB)<br/>
테스트 8 〉 통과 (4.21ms, 32.6MB)<br/>
테스트 9 〉 통과 (4.48ms, 32.9MB)<br/>
테스트 10 〉 통과 (4.81ms, 32.9MB)<br/>
테스트 11 〉 통과 (0.09ms, 30.1MB)<br/>
테스트 12 〉 통과 (0.07ms, 29.8MB)<br/>
테스트 13 〉 통과 (0.07ms, 30.1MB)

# ☑️ 문제 풀이

1. 먼저 for문을 통해 sum의 약수를 구해서 배열로 만들었다. for문에서 sum만큼을 반복하기보다 sum에서 2를 나눈 값만큼 반복한다. 이렇게 하면 반복을 줄일 수 있는데, 어떤 값의 약수는 2로 나눈 값보다 클 수 없기 때문이다!
2. 약수가 들어있는 배열 arr를 for문을 통해 반복해준다.
3. 이때, arr의 길이에서 2로 나누고 1을 뺀 값을 올림한 만큼 반복해준뒤 서로의 쌍이 yellow와 같을 때의 값을 result 배열에 추가해준다.

# 다른 사람의 풀이

```javascript
function solution(brown, red) {
  var answer = [];
  for (var i = 3; i <= (brown + red) / i; i++) {
    var x = Math.floor((brown + red) / i);
    if ((x - 2) * (i - 2) === red) {
      break;
    }
  }

  return [x, i];
}
```

다른 사람의 풀이를 보았는데 훨씬 코드도 짧고, 시간복잡도도 적었다.

위의 풀이는 for문에서 답이 나온다면 break로 for문을 탈출한다.
