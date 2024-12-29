# Sets

## Anagram
| Anagram : 단어의 문자 순서를 바꿔서 다른 단어를 만드는 것


## Problem 1. 거대한 단어 목록에서 마지막으로 등장하는 중복되지 않은 단어 찾기
Given a vast list of words, you must identify the final word that is not repeated. 
Imagine sorting through a database of unique identifiers and finding one identifier towards the end of the list that is unlike any others.

### Example 
- input : `["apple", "banana", "orange", "apple", "kiwi", "banana", "grape"]`
- output : `grape`

### Naive Approach
brute-force : `O(n^2)`

### Efficient Approach  

```
const wordSet = new Set() // O(u) 
const duplicateSet = new Set() // O(u)

// O(n)
for (let word of words) {
  if (wordSet.has(word)) {
    duplicateSet.add(word)
  } else {
    wordSet.add(word)
  }
}

let lastUniqueWord = ""

// O(n)
for (let i = words.length - 1; i >= 0; i--) {
  const word = words[i]
  if (!duplicateSet.has(word) && wordSet.has(word)) { // O(1)
    lastUniqueWord = word
    break
  }
}

return lastUniqueWord
```

- Time complexity : `O(n)`
- Space complexity : `O(u)` (`u` : the number of unique words in array)


#### Concise Version

```
function findLastDuplicateID(ids) {
  const visitedSet = new Set()

  for (const i = ids.length - 1; i >= 0; i--) {
    const id = ids[i]
    if (visitedSet.has(id)) return id
    visitedSet.add(id)
  }

  return ""
}
```
```
function findFirstDuplicateID(ids) {
    // TODO: Find an id that appears more than once and return it
    const visitedSet = new Set()

    for (const id of ids) {
        if (visitedSet.has(id)) return id
        visitedSet.add(id)
    }

    // Return an empty string if no duplicate ids are found
    return "";
}
```

## Problem 2. 두 배열에서 Anagram 단어들 찾기
You have two arrays of strings, and your task is to find all the words from the first array that have an anagram in the second array.

### Example
- input
  ```
  const array1 = ["listen", "rat", "god", "evil", "tar", "silent"]
  const array2 = ["tinsel", "art", "dog", "live", "star"]
  ```
- output : `["listen", "rat", "god", "evil", "tar", "silent"]`

### Efficient Approach
문자를 정렬하여 고유한 서명(unique signature)을 만든 후, 이 고유한 서명들끼리 비교하기. 
```
sortedArray1 = ["eilnst", "art", "dgo", "eilv", "art", "eilnst"]
sortedArray2 = ["eilnst", "art", "dgo", "eilv", "arst"]
```

```
function sortCharacters(input) {
  return [...input].sort().join("")
}

const sortedWordsInArray2 = new Set(array2.map(sortCharacters)) // O(n * m log m)

const result = []

// O(n)
for (let word of array1) {
  const sortedWord = sortCharacters(word) // O(m log m)
  if (sortedWordsInArray2.has(sortedWord)) {
    result.push(word)
  }
}

return result
```

- Time complexity : `O(n * m log m)` `(n : the number of words, m : the length of word)`
- Space complextiy : `O(n * m)`






