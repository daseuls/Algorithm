# ☑️ 문제

<img width="683" alt="스크린샷 2022-06-16 오후 2 53 31" src="https://user-images.githubusercontent.com/71131248/174001351-d1e6ebbc-2d1a-44b6-8311-d8a739b31b8b.png">

# ☑️ 사용 메서드

## Array.prototype.slice() <br/>

slice() 메서드는 어떤 배열의 begin부터 end까지(end 미포함)에 대한 얕은 복사본을 새로운 배열 객체로 반환합니다. 원본 배열은 바뀌지 않습니다.

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

console.log(animals.slice());
// expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
```

## Array.prototype.sort()

sort() 메서드는 배열의 요소를 적절한 위치에 정렬한 후 그 배열을 반환합니다. 기본 정렬 순서는 문자열의 유니코드 코드 포인트를 따릅니다.

# ☑️ 코드

```javascript
function solution(array, commands) {
  let result = [];
  for (let i = 0; i < commands.length; i++) {
    const sliceArr = array.slice(commands[i][0] - 1, commands[i][1]);
    const num = sliceArr.sort((a, b) => a - b)[commands[i][2] - 1];
    result.push(num);
  }
  return result;
}
```

## 실행 결과

테스트 1 〉 통과 (0.07ms, 29.8MB)<br />
테스트 2 〉 통과 (0.10ms, 30MB)<br />
테스트 3 〉 통과 (0.07ms, 30MB)<br />
테스트 4 〉 통과 (0.07ms, 30MB)<br />
테스트 5 〉 통과 (0.07ms, 30.1MB)<br />
테스트 6 〉 통과 (0.07ms, 30MB)<br />
테스트 7 〉 통과 (0.07ms, 29.8MB)

# ☑️ 문제 풀이

1. 결과 값을 담을 빈 배열인 result를 선언한다.
2. 두 번째 인자로 들어온 배열의 요소를 담고 있는 배열을 for 문을 통해 하나의 배열 요소씩 순회한다.
3. 첫 번째 인자로 들어온 배열을 두 번째 배열요소의 요소들을 통해 자르고(slice) 정렬(sort)한다.
4. 마지막 요소의 값 - 1번째 인덱스를 빈 result에 담은 후 리턴한다.
