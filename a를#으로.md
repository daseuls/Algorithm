8 / 11

> 대문자로 이루어진 영어단어가 입력되면 단어에 포함된 'A'를 모두 '#'으로 바꾸어 출력하는 프로그램을 작성하세요

```javascript
const changeSharp = (str) => {
  const arr = str.split("")
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === "A") {
      arr[i] = "#"
    }
  }
  const result = arr.join("")
  return result
}

console.log(changeSharp("BANANA")) // 'B#N#N#'
```

```javascript
const changeSharp = (str) => {
  let s = ""
  for (x of str) {
    if (x === "A") {
      s += "#"
    } else {
      s += x
    }
  }
  return s
}
console.log(changeSharp("BANANA"))
```

- 풀이

  첫 번째 방법

1. 인자로 들어온 문자열을 하나씩 쪼개 배열로 만들어준다.
2. 배열에 반복문을 돌려 만약 요소가 'A'이면 그것을 "#"으로 바꿔준다
3. 배열을 문자열로 바꾼다
4. 결과값을 리턴한다.

두 번째 방법

1. s라는 빈 문자열을 만든다.
2. 인자로 들어온 문자열 하나하나를 반복문을 돌려 만약 문자열이 A이면 빈 s에 #을 붙이고 아니면 그 문자열 하나의 값을 붙인다.
3. s를 리턴한다.
