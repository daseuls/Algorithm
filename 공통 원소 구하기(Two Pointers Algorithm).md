10 / 1

# 📚 문제

> 공통 원소 구하기 <br />
> A, B 두 개의 집합이 주어지면 두 집합의 공통 원소를 추출하여 오름차순으로 출력하는 프로그램을 작성하세요

> 스스로 해결 여부 <br />
> ⭕️ 👏🏻

# 🔍 문제 접근

1. 두 집합을 오름차순으로 정렬한다.
2. 각 집합의 인덱스를 가리킬 포인터 두개를 만든다.
3. 반복하면서 어떤 조건을 만족했을때 포인터를 이동시켜서 result값을 구한다.

> 어제 한 회사의 알고리즘 면접을 보면서 이중 for문을 사용하는 것보다 two pointers 알고리즘을 이용하는 것이 시간복잡도가 더 낮다는 설명을 들었다. 그도 그럴것이 이중 for문은 두 배열의 모든 경우의 수를 계산하게 된다. 하지만 두개의 포인터를 사용하여 어떤 조건을 만족했을 때 어떤 것을 취하고 포인터를 이동시키면 굳이 모든 경우의 수를 따질 필요가 없다. 이중 for문을 사용한다면 n^2의 경우의 수를 계산한다면 two pointer는 n \* 2의 경우의 수만 계산하기 때문! (맞나..?)

# 👩🏻‍💻 코드

```javascript
const getCommonElement = (arr1, arr2) => {
  const sortedArr1 = arr1.sort((a, b) => a - b)
  const sortedArr2 = arr2.sort((a, b) => a - b)

  let result = []
  let p1 = 0
  let p2 = 0
  while (p1 < arr1.length && p2 < arr2.length) {
    if (sortedArr1[p1] === sortedArr2[p2]) {
      result.push(sortedArr1[p1])
      p1++
    } else if (sortedArr1[p1] < sortedArr2[p2]) {
      p1++
    } else if (sortedArr1[p1] > sortedArr2[p2]) {
      p2++
    }
  }
  return result
}

getCommonElement([1, 3, 9, 5, 2], [3, 2, 5, 7, 8])
// [ 2, 3, 5 ]
getCommonElement([1, 3, 11, 5, 2, 13, 39, 23], [3, 11, 5, 9, 8, 23, 39, 2])
// [ 2, 3, 5, 11, 23, 39 ]
```

# 🕵🏻‍♀️ 문제 풀이

1. 먼저 인자로 들어온 두 배열을 sort메서드를 통해 오름차순으로 정렬한다.
2. 결과를 담을 빈 배열 result를 만들어준다.
3. 각 배열의 인덱스를 담당할 pointer두개를 만들어준다. 0부터 시작한다.
4. p1 포인터가 arr1의 배열의 길이보다 작을때, 또 p2 포인터가 arr2의 배열의 길이보다 작을때 둘다를 만족시킬때까지 반복해준다.(두 포인터를 모두 돌때까지)
5. 만약 정렬한 arr1의 배열의 p1의 값이 arr2의 배열의 p2값과 같다면 result에 둘중의 하나 값을 담는다.(둘다 어차피 같은 값이니까)
6. 그다음 p1이나 p2 둘중 하나의 값을 1증가시킨다. 처음 풀때 이 부분을 처리를 안해줬더니 무한루프가 돌았다. 이 부분을 처리를 안하게 되면 처음 값이 같게 될때 그 값을 담고나서 포인터가 이동하지 않기 때문에 계속 그 자리에 머물면서 result값에 담기만 하기 때문에 무한 루프가 돌았던 것!!
7. 만약 한쪽의 배열의 값이 다른 배열의 값보다 작게되면 그 작은 값의 포인터를 1증가시킨다. 오름차순으로 되어있기때문에 작을때 증가시켜야 그 다음 커진 원소와 비교가 되기 때문
8. 두개의 포인터가 끝날때까지 이 조건들을 반복한다!
