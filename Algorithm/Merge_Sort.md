# 병합 정렬 (Merge Sort)
> 병합 정렬은 어떠한 문제를 우선 작은 문제로 쪼개고 난 후 다시 조합하여 원래의 문제를 해결하는 `분할정복 알고리즘` 중 하나입니다.

## 정렬 과정
1. 주어진 배열을 절반으로 분할하여 부분배열로 나눕니다.
2. 해당 부분배열의 길이가 1이 아니라면 **1**번 과정을 되풀이합니다.
3. 인접한 부분배열끼리 정렬하며 합칩니다.

## GIF로 이해하기
![병합정렬](https://user-images.githubusercontent.com/37105602/214002517-d881b6fa-9e97-47d6-936c-14b187997893.gif)


## 특징
* 공간 복잡도
    - 다른 정렬 알고리즘들과 다르게 인접한 값들 간에 교환(swap)은 일어나지 않습니다.
    - 두 개의 배열을 병합할 때 병합 결과를 담아 놓을 배열이 추가로 필요하기 때문에 공간 복잡도는 `O(n)`입니다.
* 시간 복잡도
    - 전반적인 반복의 수는 점점 절반으로 줄어들기 때문에 O(logN)시간이 필요하며, 각 패스에서 병합할 때 모든 값들을 비교해야 하므로 O(N) 시간이 소모됩니다.
    - 따라서 총 시간복잡도는  최선, 평균, 최악 모두 `O(NlogN)`입니다.

### 장점
* 최선, 최악의 경우에도 `O(NlogN)`의 시간이 소요되기 때문에 데이터 분포에 영향을 덜 받습니다.
* 만약 **연결 리스트**로 구현하면, 링크 인덱스만 빈경되므로 데이터의 이동은 무시 할 수 있을 정도로 작아집니다.
* 크기가 큰 레코드를 정렬할 경우에 연결 리스트를 사용한다면, 퀵 정렬 포함 다른 어떤 정렬 방법보다 효율적입니다.

### 단점
* `in place`알고리즘이 아니기 때문에 별도의 메모리 공간이 필요합니다.

## 📌 예제 (Baekjoon)
[백준 - 수 정렬하기](https://www.acmicpc.net/problem/2750)

>문제

<img width="1058" alt="스크린샷 2023-01-18 오후 6 01 12" src="https://user-images.githubusercontent.com/37105602/213128316-d9ee24f1-88c2-4acd-bc3c-4db6ea27511b.png">

>풀이  

입력 값들을 오름차순으로 정렬하는 문제입니다.  
병합정렬 알고리즘을 이용하여 정렬합니다.

### 코드(Python)
```Python
def merge_sort(arr, first, last):
	if first >= last:
		return
    
	merge_sort(arr, first, (first+last) // 2)
	merge_sort(arr, (first+last) // 2 + 1, last)

	return merge(arr, first, last)

def merge(arr, first, last):
	mid = (first + last) // 2
	i, j = first, mid+1
	temp = []

	while i <= mid and j <= last:
		if arr[i] <= arr[j]:
			temp.append(arr[i])
			i += 1
		else:
			temp.append(arr[j])
			j += 1
	while i <= mid:
		temp.append(arr[i])
		i += 1
	while j <= last:
		temp.append(arr[j])
		j += 1
	for k in range(first, last+1):
		arr[k] = temp[k-first]

	return arr

n = int(input())
numbers = []

for _ in range(n):
    numbers.append(int(input()))

for n in merge_sort(numbers, 0, n - 1):
    print(n)
```
[병합정렬 정렬과정](#정렬-과정) 에 따라 `분할 - 정복 - 병합`합니다. 
## Reference
- https://jinhyy.tistory.com/9
