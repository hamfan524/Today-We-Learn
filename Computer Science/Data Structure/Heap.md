# **Heap**

## **Heap(힙)이란**?
```우선순위``` 큐를 위해 만들어진 자료구조
```
- 완전 이진 트리의 일종이다.(마지막을 제외한 모든 노드에서 자식들이 꽉 채워진 이진트리)
- 여러 값 중, 최대값과 최소값을 빠르게 찾아내도록 만들어진 자료구조로 반정렬 상태이다.
- 힙 트리는 중복된 값을 허용한다. (이진 탐색 트리는 중복값 허용X) 
```
<p align="center">
<img width="400" alt="heap" src =https://user-images.githubusercontent.com/96968834/212826702-7933bf9a-86b7-4680-8bbd-c7541358c64b.jpg>
</p>


<br>

## **우선순위 큐**?
```
우선순위의 개념을 큐에 도입한 자료구조
데이터들이 우선순위를 가지고 있어 우선순위가 높은 데이터가 먼저 나간다
내부구조가 힙으로 구성되어 있기에 시간 복잡도는 O(NLogN)이다
```

### **우선순위 큐 구현** 
```
우선순위 큐는 배열, 연결리스트, 힙 으로 구현이 가능하다. 이 중에서 힙(heap)으로 구현하는 것이 가장 효율적이다.
```

### **우선순위 큐 사용법**
```java
import java.util.PriorityQueue; //import

//int형 priorityQueue 선언 (우선순위가 낮은 숫자 순)
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

//int형 priorityQueue 선언 (우선순위가 높은 숫자 순)
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());

```

<br>

## **힙의 종류**
### 1. **최대힙**<br>
```
부모 노드의 키 값이 자식 노드의 키 값보다 크거나 같은 완전 이진 트리
Key(parent) ≥ Key(child) 
가장 큰 값이 루트노드에 있음
```


 <img width="350" alt="maxHeap" src =https://user-images.githubusercontent.com/96968834/212827071-07f7b681-5872-4e1c-92d4-799d197964cd.jpg>

### 2. **최소힙**<br>
```
부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리
Key(parent) ≤ Key(child)
가장 작은 값이 루트노드에 있음
```


<img width="350" alt="maxHeap" src =https://user-images.githubusercontent.com/96968834/212827271-85000752-c74d-4674-a51b-f79d7209f9ff.jpg>

<br><br>

## **힙 표현**
```
힙은 일반적으로 배열로 표현합니다.
개발 편의성과 가독성 때문에 배열 인덱스 1부터 사용합니다.
```

**루트 노드의 인덱스 i가 1인 경우 다음과 같은 속성이 있습니다.**
- 노드 i의 부모노드 인덱스 : ```[i/2]```
- 노드 i의 왼쪽 자식 노드 인덱스 : ```2*i```
- 노드 i의 오른쪽 자식 노드 인덱스 : ```2*i + 1```

<img width="350" alt="maxHeap" src =https://user-images.githubusercontent.com/96968834/212830589-65ec7f52-1436-4d2a-b310-a0586cca9bf8.jpg>


<br><br>

## **사용 사례**
```
- 우선순위 큐
- Dijkstra 알고리즘
- 힙 정렬
```
<br>









