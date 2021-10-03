10 / 2

# 📚 문제

> 연속 부분 수열 (Two Pointers Algorithm) <br/>
> n개의 수로 이루어진 수열이 주어진다. 이 수열에서 연속부분수열의 합이 특정숫자 M이 되는 경우가 몇 번 있는지 구하는 프로그램을 작성하세요. 만약 N=8, M=6이고, 수열이 다음과 같다면 1 2 1 3 1 1 1 2 합이 6이 되는 연속 부분 수열은 {2,1,3}, {1,3,1,1}, {3,1,1,1}로 총 3가지 입니다.

> 스스로 해결 여부 <br />
> ⭕️

# 🔍 문제 접근

두개의 포인터를 통해 시간복잡도를 줄이기 위함인데, 내가 푼 방법은 시간복잡도가 문제 풀이보다 더 크다... 일단은 내가 접근한 방법이다.

1. 두개의 포인터를 둔다. 하나의 포인터는 각 배열의 요소 인덱스를 증가시키며 합을 구하기 위함이고 하나의 포인터는 조건을 만족하거나 만족시키지 못할때 첫번째 포인터를 초기화 하는 용도이다. 초기화를 할때는 1을 증가시킨 값으로 초기화 한다. 왜냐면 그 다음 인덱스부터 다시 시작해서 계산해야하기 때문
2. 근데 이 방법으로 풀게되면 시간 복잡도가 결국엔 이중 for문과 비슷해질것같다. 결국 경우의 수를 다 구해보는 것이기 때문..?

# 👩🏻‍💻 코드

```javascript
const getCaseOfSum = (sum, arr) => {
  let p1 = 0
  let p2 = 0
  let calculatedSum = 0
  let count = 0
  while (p2 < arr.length && p1 < arr.length) {
    calculatedSum += arr[p1]
    if (calculatedSum < sum) {
      p1++
    } else if (calculatedSum === sum) {
      count++
      p2++
      p1 = p2
      calculatedSum = 0
    } else if (calculatedSum > sum) {
      p2++
      p1 = p2
      calculatedSum = 0
    }
  }
  return count
}

getCaseOfSum(6, [1, 2, 1, 3, 1, 1, 1, 2]) // 3
getCaseOfSum(2, [1, 2, 1, 3, 1, 1, 1, 2]) // 4
```

# 🕵🏻‍♀️ 문제 풀이

1. 0부터 시작하는 포인터 두개를 둔다.
2. 위에 문제 접근에서와 같이 p1의 포인터는 누적계산을 위한 인덱스용이고, p2는 값을 만족하거나 만족시키지 못할때 p1을 초기화 시키는 역할을 한다.
3. 일단 먼저 배열의 요소를 p1을 통해 하나씩 돌면서 calculatedSum에 누적을 시킨다.
4. 만약 calculatedSum의 값이 인자로 들어온 sum보다 작을 경우에는 p1을 1증가시켜 다음 인덱스값을 누적시킨다.
5. 만약 이렇게 누적시키다가 그 값이 sum과 같다면 우리는 이 경우를 구해야 하기 때문에 count에 1을 더하고, 다음 경우의 수를 계산하기 위해 p2를 1증가시킨뒤 p1을 p2로 초기화한다.
6. 이것은 만약 calculatedSum이 sum보다 커지게 될경우도 마찬가지이다. count를 증가시키는 것을 제외하고 똑같이 p2를 1증가시키고 p1을 초기화한다.
7. 이것을 p1과 p2가 배열의 길이보다 작을때까지 반복한다.
8. 반복문이 끝난 뒤 계산된 count를 리턴해준다

강의를 보고 시간복잡도를 줄여 푸는 방법을 다시 정리해보겠다.

- 새로 풀어본 방법

```javascript
const getCaseOfSum = (sum, arr) => {
  let lt = 0
  let rt = 0
  let count = 0
  let calculatedSum = 0
  while (rt < arr.length) {
    if (calculatedSum < sum) {
      calculatedSum += arr[rt]
      rt++
    } else if (calculatedSum === sum) {
      count++
      calculatedSum -= arr[lt]
      lt++
    } else if (calculatedSum > sum) {
      calculatedSum -= arr[lt]
      lt++
    }
  }
  return count
}

getCaseOfSum(6, [1, 2, 1, 3, 1, 1, 1, 2])
getCaseOfSum(5, [1, 2, 1, 3, 1, 1, 1, 2])
```
