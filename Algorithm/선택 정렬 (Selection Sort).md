

# 선택 정렬 (Selection Sort)

## 과정

1. 주어진 배열 중에 최소값을 찾는다

2. 최소값을 배열 맨 앞에 위치한 값과 교체

3. 이전 과정을 통해 정렬된 원소를 제외한 나머지 배열에 **과정1, 2**를 반복

   

## 구현

```python
def selection_sort(a):
  	# 정렬하려는 위치를 순회
    for i in range(0, len(a) - 1):
        min_val = i
        # 최소값 찾아서 정렬하려는 위치에 넣기
        for j in range(i + 1, len(a)):
            if a[min_val] > a[j]:
                min_val = j
        a[i], a[min_val] = a[min_val], a[i]
```

![JavaScript Sorting Algorithms Explained: Selection Sort -](https://i0.wp.com/thedukh.com/wp-content/uploads/2020/12/selectionsort.gif?resize=494%2C261&ssl=1)

## 시간복잡도

`(n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2`이므로, **O(n^2)**  

n개의 주어진 배열을 정렬하는데 O(n^2) 만큼의 시간 소요. 

최선, 평균, 최악의 경우 시간복잡도는 **O(n^2)** 으로 동일



## 장점

- Bubble sort와 마찬가지로 알고리즘이 단순합니다.

- 정렬을 위한 비교 횟수는 많지만, Bubble Sort에 비해 실제로 교환하는 횟수는 적기 때문에 많은 교환이 일어나야 하는 자료상태에서 비교적 효율적입니다.

- B정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않는다. 

  => 제자리 정렬(in-place sorting), 공간복잡도 **O(n)**  

## 단점

- 시간복잡도가 O(n^2)으로, 비효율적입니다.
- **불안정 정렬(Unstable Sort)** 입니다.