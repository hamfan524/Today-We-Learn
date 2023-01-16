# **Stack**

### **Stack(스택)이란**?
<br>

```
스택은 한쪽 끝에서만 데이터를 넣고 뺄 수 있는 제한적으로 접근할 수 있는 
후입선출(Last-In-First-Out) 형태의 선형 자료구조이다.
```
<br>

### **후입선출(LIFO)**

가장 최근에 들어온 데이터가 가장 먼저 나간다는 의미

<img width="400" alt="stack" src =https://user-images.githubusercontent.com/96968834/212623880-8eba03ae-bb92-4d02-89c8-b5a21e54cc51.jpg>


<br>

### **스택에서 발생하는 오류**
- 비어있는 스택에서 데이터를 꺼내려 할때 (스택 언더플로우: Stack Underflow)
- 꽉찬 스택에 데이터를 넣으려 할 때 (스택 오버플로우: Stack Overflow)
<br><br>


### **Stack(스택)의 연산**
- push(x): 스택에 데이터 x를 추가합니다.
- pop(): 스택의 맨 위의 데이터 원소를 제거하며, 반환합니다.
- size(): 현재 스택에 들어 있는 데이터 원소 개수를 반환합니다.
- isEmpty(): 현재 스택이 비어 있는지를 판단합니다.
  - 비어있으면 True를 비어있지 않으면 False를 반환합니다.
- peek(): 스택의 맨위의 데이터 원소를 반환합니다.

<br><br>
## **배열의 시간 복잡도(Time complexity)**

Operation|average case|worst case
|:---|:---:|:---:
**Access**|Θ(n)|Θ(n)
**Search**|Θ(n)|Θ(n)
**Insert(push)**|Θ(1)|Θ(1)
**Delete(pop**|Θ(1)|Θ(1)

push(),pop(),isEmpty(),peek() 모두 O(1) 시간이 걸립니다.<br>
이유는 삽입 삭제는 항상 Top에서만 일어나기 때문입니다. 


