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
```

## Problem 3. 최다 등장 요소 찾기 - frequency
> 사용 예 : 검색 엔진 최적화

맵을 사용하면 각 정수에 대해 전체 목록을 검토하는 대신(`O(n^2)`), 배열을 한 번씩 살펴보면서 각 요소의 총합을 유지할 수 있습니다.


```
function findCelebrityElement(array) {
  const majorityThreshold = array.length / 2
  const countMap = new Map()

  for (const num or elements) {
    countMap.set(num, (countMap.get(num) || 0) + 1)

    if (countMap.get(num) > majorityThreshold)
      return num
  }
  return -1
}
```

## Problem 4. Keyword Document Indexer 특정한 키워드 indexing하기

> 사용 예 : 빠른 액세스를 위한 데이터 구조화

특정 단어가 어떤 documents에 있는지 색인이 필요함 

```
function createKeywordIndex(documents) {
  const index = new Map()

  documents.forEach((doc, docIndex) => {
    const words = doc.split(/+s/)
    for (const word of words) {
      if (index.has(word))
        index.get(word).add(docIndex)
      else
        index.set(word, new Set([docIndex]))
    }
  })
  return index
}



