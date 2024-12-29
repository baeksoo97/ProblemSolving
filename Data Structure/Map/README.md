# Map

Map은 자바스크립트에서 다용도 데이터 구조입니다. 키-값 쌍을 저장하고 객체와 함수를 포함한 모든 데이터 유형을 키로 사용할 수 있습니다.

- 자바스크립트는 해시 테이블을 사용하여 맵을 구현합니다. 이 테이블은 저장된 데이터에 따라 맵의 크기를 조정하여 메모리 사용량을 최적화합니다.

- 맵에서 `get`, `set`, `has`, `delete` operation의 시간 복잡도는 `O(1)`입니다. 이는 맵의 크기에 관계없이 즉시 실행된다는 것을 의미합니다.


## Problem 1. 텍스트에서 단어 빈도수 구하기

> 사용 예 : 검색 엔진 최적화에 사용되는 텍스트 분석 도구에서 필수적인 기능

1. 텍스트를 normalize 하는 과정 필요


  ```
  function normalizeText(input) {
    return input.toLowerCase().replace(/[^\w\s]/g, "");
  }
  ```

2. normalized한 텍스트에서 단어 찾기 및 <단어, 빈도수> pair 저장

  ```
  function countWordFrequencies(text) {
    const normalizedText = normalizeText(text)
  
    const frequencyMap = new Map()
  
    for (const word of normalizedText.split(/\s+/)) {
      const count = frequencyMap.get(word) || 0
      frequencyMap.set(word, count + 1)
    }
  
    return frequencyMap
  }
  ```

## Problem 2. HashMap에서 value들의 총 합 구하기 

> 사용 예 : 월별 지출 표시하는 개인 금융 앱에서 카테고리별 재정 상태 파악할 때

```
function sumOfMapValues(numberMap) {
  let sum = 0
  for (let quantity of numberMap.values()) {
      sum += quantity
  }
}



