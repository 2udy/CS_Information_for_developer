# Binary Search Tree

#### 개념

이진 탐색 + 연결 리스트

- 이진 탐색: 배열은 탐색에 유리하지만 삽입 삭제 불가능
- 연결리스트: 삽입 삭제에 유리하지만 탐색 속도가 느림

이 두가지를 합해서 장점을 취한 것

중위순회를 통해 정렬된 결과를 얻을 수 있다.

#### 검색

찾으려는 값이 현재 노드보다 크면 오른쪽 자식으로, 작으면 왼쪽자식으로 이동하며 검색한다.

#### 삽입

검색과 동일한 로직을 반복하며 위치가 비어있다면 노드를 추가한다.

#### 삭제

- 삭제할 노드의 자식노드가 없는 경우: 해당 노드만 삭제
- 삭제할 노드의 자식노드가 1개인 경우: 해당 노드만 삭제
- 삭제할 노드의 자식노드가 2개인 경우: 삭제된 노드를 대신 할 노드를 찾아야 한다.
  - 왼쪽 자식 노드에서 가장 큰 값과 오른쪽 자식 노드에서 가장 작은 값을 비교하여 대체한다.

