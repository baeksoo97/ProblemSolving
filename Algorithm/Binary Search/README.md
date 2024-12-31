# Binary Search

이진 탐색은 분할 및 정복 전략을 따릅니다. 
정렬된 목록의 중간에서 시작합니다. 중간 값이 원하는 값이면 좋습니다. 
그렇지 않은 경우 목록의 정렬된 특성을 사용하여 목록의 절반을 제거합니다. 제거할 쪽은 대상이 중간 값보다 작은지 큰지에 따라 선택됩니다.

- 이진 탐색은 정렬된 데이터에서 빠르고 효율적으로 값을 찾을 수 있음. 
- **정렬되지 않은 데이터는 먼저 정렬해야 하므로**, 그 경우에는 **정렬 비용이 추가**됨. 

## Binary Search using Recursion
```
function recursiveBinarySearch(arr, start, end, target) {
  // Base case : the search area is empty
  if (start > end) return -1

  const mid = Math.floor((start + end) / 2)

  if (arr[mid] === target) return mid

  // If the target is less than the midpoint, search the left half
  if (arr[mid] > target)
    return recursiveBinarySearch(arr, start, mid - 1, target)
  // Else, search the right half
  else
    return recursiveBinarySearch(arr, mid + 1, end, target)
}
```


## Binary Search using Iteration
```
function iterativeBinarySearch(arr, target) {
  let start = 0
  let end = arr.length - 1

  while (start <= end) {
    const mid = Math.floor((start + end) / 2)

    if (arr[mid] === target) return mid
    else if (arr[mid] > target) end = mid - 1
    else start = mid + 1
  }
  return -1
}
```

## Complexity

### Time Complexity
이진 검색은 매 단계마다 입력 크기를 절반으로 줄이므로 n 크기의 배열에서 대상을 찾는 데 로그(n) 단계가 걸리며, 
따라서 이진 검색의 시간 복잡성은 `O(log n)`입니다. 
재귀 방식과 반복 방식 모두 시간 복잡성은 `O(log n)`로 동일합니다.
- 최악, 평균 : `O(logn)`
- 최선 : `O(1)`

### Space Complexity
- recursion : `O(logn)` (호출 스택 사용량)
- iteration : `O(1)`

