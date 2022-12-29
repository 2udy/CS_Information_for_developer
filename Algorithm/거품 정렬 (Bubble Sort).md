# 거품 정렬 (Bubble Sort)

## 과정

1. 첫번째 원소부터 마지막까지 순서대로 인접한 두 원소를 비교하며 조건에 맞는 경우 교환
2. 한단계가 끝나면 가장 큰 원소가 맨 뒤에 정렬
3. 이전 과정을 통해 정렬된 원소 앞까지 **과정1**을 반복



## 구현

```python
def bubble_sort(numbers):
    # 1. 첫번째 수행이 n-1번의 비교가 일어나도록 설정
    for i in range(len(numbers) - 1, 0, -1):
        # 2. 해당하는 횟수만큼 반복을 돌면서 요소를 비교
        for j in range(0, i):
					# 3. 교환이 일어나는 조건 (이전 요소가 이후 요소보다 클 때)
          if numbers[j] > numbers[j + 1]:
						# 두번째 방법 - 파이썬의 swap 방식
						numbers[j], numbers[j + 1] = numbers[j + 1], numbers[j]
    return numbers
numbers = [54, 26, 93, 17, 77, 31, 44, 55, 20]
print(bubble_sort(numbers))
```

![How to implement Bubble sort algorithm in JavaScript | Reactgo](https://reactgo.com/acb6082891086b779854ec1fc0cb420b/bubble-sort-visualization.gif)



## 시간복잡도

`(n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2`이므로, **O(n^2)**  

Bubble Sort는 정렬이 돼있던 안돼있던, 2개의 원소를 비교하기 때문에 최선, 평균, 최악의 경우 모두 시간복잡도가 **O(n^2)** 으로 동일



## 장점

- 구현이 매우 간단하고, 소스코드가 직관적입니다.

- 정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않습니다. 

  => 제자리 정렬(in-place sorting), 공간복잡도 **O(n)**  

- 안정 정렬(Stable Sort) 



## 단점

- 시간복잡도가 최악, 최선, 평균 모두 O(n^2)으로, 굉장히 비효율적입니다.
- 정렬 돼있지 않은 원소가 정렬 됐을때의 자리로 가기 위해서, 교환 연산(swap)이 많이 일어나게 됩니다.



## 안정정렬과 불안정 정렬

- 정렬 후 같은 값인 요소의 순서 보장여부에 따라 구분됨

![안정 정렬 vs 불안정 정렬(feat. 제자리 정렬)](https://images.velog.io/images/aiden/post/8043d2c5-cad9-4869-8a2b-546fe264040a/%EC%95%88%EC%A0%95%20%EC%A0%95%EB%A0%AC%20vs%20%EB%B6%88%EC%95%88%EC%A0%95%20%EC%A0%95%EB%A0%AC.PNG)