# **Graph**

### **Graph(그래프)란**?
<br>

```
그래프는 정점(Vertex)과 간선(Edge)으로 이루어진 자료구조이다.
연결 되어있는 원소간의 관계를 표현한 자료구조입니다.
그래프를 G=(V,E)로 정의하는데, V는 정점의 집합, E는 간선들의 집합을 의미합니다.
```
<img width="500" src =https://user-images.githubusercontent.com/96968834/213973630-90f75593-37e8-416b-9628-82b0dd3dd957.jpg>

<br>
<br>



## 그래프와 관련된 용어
- **정점** (vertex) : 노드(node), 데이터가 저장되는 그래프 기본 원소
- **간선** (edge) : 링크(link), 정점간의 관계를 나타냄
- **인접 정점** (adjacent vertex) : 간선에 의해 연결된 정점
- **단순 경로** (simple path) : 동일한 간선을 지나지 않는 경로
- **차수 degree** = 무방향 그래프에서 한 정점에 인접한 정점의 수 
- **진출 차수**(out-degree) : 방향 그래프에서 한 정점에서 다른 정점으로 나가는 간선의 수
- **진입 차수**(in-degree) : 방향 그래프에서 외부에서 한 정점으로 들어오는 간선의 수
- **경로 길이**(path length) : 경로를 구성하는 간선의 수

- **사이클** (cycle) : 한 정점에서 시작해 해당 정점으로 끝나는 경로 ( ex : A-B-C-D-A )

<br><br>


## 그래프 종류

1. ```무방향``` 그래프<br>
무방향 그래프는 두 정점을 연결하는 간선에 방향이 없는 그래프이다.<br>
<img src=https://user-images.githubusercontent.com/96968834/215669990-ffb215d5-f4d6-4b54-8db4-2a5b95a250a1.png>
<br><br>


2. ```방향``` 그래프<br>
방향 그래프는 두 정점을 연결하는 간선에 방향이 존재하는 그래프이다.<br>
간선의 방향으로만 이동할 수 있다.<br>
<img src=https://user-images.githubusercontent.com/96968834/215670237-4528d20b-8aa1-4726-8e85-e1d3fa91edc8.png>
<br><br>

3. ```가중치``` 그래프<br>
가중치 그래프는 간선에 가중치(비용)가 할당된 그래프로, 두 정점을 이동할 때 비용이 드는 그래프이다.
<img src=https://user-images.githubusercontent.com/96968834/215670325-cc60e7f9-0d8b-4099-b426-14b06ad1f3c0.png>
<br><br>

4. ```완전``` 그래프<br>
그래프의 모든 정점이 서로 연결되어 있는 그래프이다. (인접 연결)<br>
<img width="200" src=https://user-images.githubusercontent.com/96968834/215670406-3aa6c8a6-31b1-4e01-91fb-cfdcbddf0e89.png>
<br><br>


5. ```순환``` 그래프<br>
단순 경로에서 시작 정점과 도착 정점이 동일한 그래프이다. (A에서 시작-> A에서 끝 가능)<br>
<img width="200" src=https://user-images.githubusercontent.com/96968834/215670566-f98f3c9b-d189-483f-a2cb-d97088d5ecd1.png>



6. ```비순환``` 그래프<br>
사이클 그래프를 제외한 그래프로, 사이클이 없는 그래프이다.<br>
<img width="200" src=https://user-images.githubusercontent.com/96968834/215670597-f8ea4e89-497c-4e64-94f6-0ef24931516a.png>


<br>

## Reference
- https://hongcoding.tistory.com/78