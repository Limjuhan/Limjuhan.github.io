---
layout: single
title: "LinkedList 대하여 알아보기"

tags: [LinkedList]
---
[참조사이트:네이버 블로그](https://cdragon.tistory.com/entry/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-LinkedList%EC%97%B0%EA%B2%B0-%EB%A6%AC%EC%8A%A4%ED%8A%B8)

# 연결리스트(Linked List)란?

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpxZ2o%2FbtrVh5sOJs2%2FhGZXGsD5miCXnPFCF7FUZK%2Fimg.png)

LinkedList는 Node라는 객체로 이루어져 있는데 Node는 데이터를 저장하는 field와 다음 노드를 가리킬 수 있는 next pointer field로 구성이 되어있습니다.
이말인 즉슨, 이 노드들이 연결된 형태의 자료구조를 바로 LinkedList라고 하는 것입니다.

### Head: 가장 앞에 위치한 노드

LinkedList의 값이 있더라도 Head 노드는 반드시 비어있습니다. 따라서 head 노드에는 무조건 null값을 주게 됩니다. 그래서 head node는 보통 dummy node라고 불리기도 합니다.(아무런 값이 존재하지 않고 그저 수단으로만 사용되기 때문)
 

### Tail: 가장 뒤에 위치한 노드

Tail은 자신의 다음에 가리킬 노드가 없기 때문에 Tail의 next pointer 또한 null입니다.
단순 연결 리스트에서는 노드가 뒤에 계속 추가 된다면 tail 노드는 바뀔 수 있지만, 이중 연결 리스트에서는 tail노드를 따로 지정을 해두기 때문에(이름이 '이중'인 이유) tail노드가 바뀌지 않습니다.


# 검색
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcyzsNo%2FbtrVmXG4gIl%2F3kPBFGS92Ak0dHEicB1FG0%2Fimg.png)
LinkedList에서의 검색은 ArrayList의 검색과 마찬가지로 head 노드에서부터 tail 노드까지 순차적으로 순회하면서 데이터를 찾아갑니다. 그렇기 때문에 마찬가지로 O(N)의 시간 복잡도를 가집니다.
ArrayList는 대신 index로 검색을 하는 경우 Randon Access(임의 접근 방식)가 가능하여 데이터를 처음부터 찾을 필요가 없기 때문에 O(1)의 시간 복잡도를 갖습니다.

# 추가
'추가'는 원하는 노드를 하나 만들고 그 노드와 Tail노드의 next pointer를 연결하는 작업입니다.
마찬가지로 처음부터 끝까지 순회하면서 마지막 노드가 가리키고 있는 Null 위치에 우리가 원하고자 하는 노드를 추가 시키는 개념입니다.
ArrayList와는 달리, 끝 노드를 찾아야 하지 않아도 되고 그저 tail노드에서 새로운 노드를 추가하는 것이기 때문에 O(1)의 시간 복잡도를 갖습니다.

# 삽입
삽입은 제일 끝이 아니라 중간에 넣는 경우를 말하며 LinkedList는 ArrayList와는 다르게 데이터를 뒤로 한 칸씩 전부 밀어줄 필요가 없습니다. 
그냥 간단히 pointer만 바꿔주면 되기 때문에 논리는 간단하지만 삽입 위치를 찾기 위해서는 순회를 통해 찾아야 하기 때문에 시간복잡도는 O(n) 입니다.
해당 과정은 다음과 같이 진행됩니다.

 

1. 먼저, 삽입을 원하는 노드를 생성한다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdc71F8%2FbtrVk5ZDton%2Fy5cgTQ9SiD2smnbsPnajk1%2Fimg.png)

2. 해당 노드의 previous(이전의) node의 next 포인터를 본인 노드와 연결하고 previous node의 next pointer가 가리키고 있던 노드를 본인 노드의 next pointer로 가리킴로써 연결을 삽입을 마무리한다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbJdgqn%2FbtrVjMsTslr%2Fg7GdokG7O5uFz4sIAT7kL1%2Fimg.png)


# 삭제
LinkedList에서 삭제하고자 하는 노드가 있을 때는 그 위치를 찾아가야 하기 때문에 결정되는 시간복잡도는 O(N)입니다.
- head와 tail노드로 무작정 알아낼 수 없기 때문
ArrayList에서는 삭제할 위치를 찾고 뒤의 데이터들을 앞으로 한 칸씩 당기는데 또 시간이 O(N)만큼 소요가 됐다면,
LinkedList는 데이터를 당겨오지 않고 pointer만 조금 바꾸어 주면 삭제 과정이 자동으로 이루어지게 됩니다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FceKdBu%2FbtrVjOjO44G%2FChU6fwtK5Muakk1wxK4kK0%2Fimg.png)

빨간 점선으로 된 노드를 삭제해야 한다고 합시다. 앞으로 삭제하고자 하는 노드를 삭제노드, 그 노드의 이전 노드는 이전노드 다음 노드는 다음노드라 부르겠습니다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHIZcY%2FbtrVmf8YyCd%2FwNGPB2OKYJXqOuoSK1LhFk%2Fimg.png)

이전 노드의 next pointer는 삭제 노드의 next pointer가 가리키고 있던 노드를 가리키게되고 삭제 노드의 next pointer는 아무것도 가리키지 않는 상태인 null 상태가 되게 합니다.
즉, node.next = null; 로 표현할 수 있습니다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FW3QMJ%2FbtrVo3UrHIx%2F5Dm3MYKWUyErk9Cc1Zjh10%2Fimg.png)

그 이후 자바에서는 garbage collector에 의해 붕떠 있던 삭제 노드는 알아서 사라지게 됩니다. 그리하여 LinkedList의 삭제를 진행한 후 연결이 잘 되어 있는 것을 볼 수 있습니다.

# 정리

- 장점

배열의 복사나 재할당 없이 데이터 추가 가능 + 유연한 공간
ArrayList는 배열이 꽉 차있는 경우 크기를 늘려 준 다음 데이터를 다시 추가해 주는 과정을 진행해야 했는데 LinkedList는 쓰는 공간만큼만 크기가 늘었다 줄었다 하기 때문에 메모리 측면에서 훨씬 효율적입니다.

- 단점

데이터 접근에 대한 시간이 늘어남
배열(Array List)과 달라, Random Access가 되지 않기 때문에 원하는 노드를 찾아야 하는 경우 O(N)의 시간복잡도가 발생한다는 점이 단점이라면 단점이겠습니다.













