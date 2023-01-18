# **Linked List**

### **Linked List(연결 리스트)란**?
<br>

```
Linked List 는 Node라는 객체로 구성되어 있다.

노드는 데이터를 저장할 수 있는 필드와 다음 노드를 가르키는 넥스트 포인터를 가지고 있다.

이 노드들이 다 연결된 형태를 Linked List 라고 한다.
```

<img width="600" alt="heap" src =https://user-images.githubusercontent.com/96968834/213112430-29b24407-17fa-4d43-a211-8c601dc45c05.jpg>
</p>
<br>

## 장점

삭제나 추가가 ```O(1)``` 시간에 가능하다.<br>
데이터가 삭제되거나 추가되면 해당 노드의 가리키는 포인터만 변경

<img width="600" src =https://user-images.githubusercontent.com/96968834/213113596-cb32dbc6-31c0-4d9a-b4f9-d5af984ffd4f.jpg>

<br>

## 단점

특정 데이터를 검색하는데 무조건 ```O(n)```의 시간이 걸린다.<br>

- 배열의 경우 특정데이터를 찾을 때 인덱스가 있어 검색할 때 효율적입니다.<br>
- 하지만 연결 리스트는 정해진 위치를 알지 못하기 때문에 검색 시 데이터를 순회해 특정 데이터를 찾아야합니다.

<br><br>

## Linked List 종류
1. 단일 연결리스트<br>
```
각 노드 당 한 개의 포인터가 있고 포인터는 다음 노드의 위치를 가르킵니다.
테일은 가장 마지막이므로 다음을 가리키는 포인터를 갖지 않습니다.
```
<br>

2. 이중 연결 리스트<br>
```
단일 연결 리스트는 포인터를 한 개 가지고 있어 다음 노드만 가리킬 수 있었다면
이중 연결 리스트는 포인터를 두 개 가지고 있어 이전 노드와 다음 노드를 가리킵니다.
```

<img width="600" height="80" src=https://user-images.githubusercontent.com/96968834/213115169-6a1ddf7b-3d3d-42a8-adf2-430935f91b7d.jpg>

<br>

3. 원형 연결 리스트<br>
```
단일 연결 리스트의 테일에 포인터가 추가된 형태로 테일의 포인터는 헤더를 가르켜 원형이 되도록 합니다.
```

<img width="600" src=https://user-images.githubusercontent.com/96968834/213116683-d9d0cc2a-c89b-4760-85da-795e5dca7e3e.jpg>


