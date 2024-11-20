<img width="523" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 26 34" src="https://github.com/user-attachments/assets/5305f9c6-6aff-442e-8ecd-5ce4f8d043e8"><img width="515" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 24 02" src="https://github.com/user-attachments/assets/5e835c26-3faa-48d0-9156-24eff11c5192"># 우선순위 큐: 힙

## 우선순위 큐(Priority Queue)

> 우선순위 큐는 각 요소가 우선순위를 가지며, 높은 우선순위를 가진 요소가 먼저 처리되는 자료구조이다.
> 

우선순위 큐는 `삽입`과 `삭제`를 중점적으로 사용하는 자료구조이다.

따라서 특정 값을 가진 원소를 검색할 수 있는 기능이 필요없다.

`힙(Heap)` 자료구조는 `우선순위 큐`를 구현하기 위한 자료구조로 사용된다.

## 최대 힙(Max-Heap)과 최소 힙(Min-Heap)

- 최대 힙 : 부모 노드가 자식 노드보다 크거나 같은 값을 갖는 완전 이진 트리
    - 루트 노드에 가장 큰 값이 위치한다.
- 최소 힙 : 부모 노드의 값이 자식 노드의 값보다 작거나 같은 완전 이진 트리
    - 루트 노드에 가장 작은 값이 위치한다.

<img width="668" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1 53 09" src="https://github.com/user-attachments/assets/c490afeb-18a5-4ebc-88c2-f5f5ec98f8d7">

## 포화 이진 트리와 완전 이진 트리

<img width="425" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1 54 22" src="https://github.com/user-attachments/assets/cee65433-ca83-48e1-af9f-41da4a1fa6aa">

<img width="416" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1 54 29" src="https://github.com/user-attachments/assets/9be10fe3-059c-46ef-9090-f8ac9e8efc89">

- 포화 이진 트리
    - 모든 레벨이 완전히 채워진 이진 트리
    - 노드의 개수는 2^k - 1개이다.
    - 모든 노드가 정확히 2개의 자식 노드를 가진다.
- 완전 이진 트리
    - 마지막 레벨을 제외한 모든 레벨이 완전히 채워진 이진 트리
    - 마지막 레벨의 노드들은 왼쪽부터 순서대로 채워진다.

## 힙(Heap)을 만족하는 2가지 조건

1. 완전 이진 트리
2. 힙의 특성을 만족
    1. 최대 힙(Max Heap) : 부모 노드의 값이 자식 노드의 값보다 크거나 같다.
    2. 최소 힙(Min Heap) : 부모 노드의 값이 자식 노드의 값보다 작거나 같다.

## 리스트(List)를 사용하면 완전 이진 트리를 만족할 수 있다.

<img width="546" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 03 37" src="https://github.com/user-attachments/assets/7300f3af-f119-4529-9e20-00efa9a2342d">

완전 이진 트리는 왼쪽부터 차례대로 2개의 자식 노드를 갖는다.

리스트(List)를 사용하였을 때, [9, 8, 8, 4, 7, 3, 5] 순서대로 값을 삽입하면, 사진처럼 완전 이진 트리가 구성된다.

### 완전 이진 트리의 특징

- 부모 노드 인덱스를 알면 자식 노드(왼쪽, 오른쪽) 인덱스를 구할 수 있다.
    - 부모 노드 인덱스 : k
    - 왼쪽 자식 노드 인덱스 : (2k + 1)
    - 오른쪽 자신 노드 인덱스 : (2k + 2)
- 자식 노드(왼쪽, 오른쪽) 인덱스를 알면 부모 노드의 인덱스를 구할 수 있다.
    - 왼쪽, 오른쪽 자식 노드 인덱스 : k
    - 부모 노드 인덱스 : (k - 1) / 2

## 삽입 예제

1. 새로운 원소 6이 트리에 삽입된다. 
    1. 삽입된 원소는 리스트의 마지막 위치에 삽입된다.

<img width="586" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 13 25" src="https://github.com/user-attachments/assets/97633232-a8de-4916-8e7d-5e923ba87d6d">

1. 최대 힙 성질을 만족하지 않는다. 
    1. 최대 힙을 만족하기 위해서는 부모 노드가 자식 노드의 값보다 커야한다.
    2. A[3] < A[7]을 만족하므로 최대 힙을 만족하지 않는다.
2. 힙 업(HeapifyUp)을 수행한다.
    1. 먼저 삽입된 원소(A[7]))과 부모 노드의 위치를 변경한다.

<img width="597" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 16 15" src="https://github.com/user-attachments/assets/d72f1783-740f-4d60-8c74-925b6606006a">


1. 최대 힙의 성질을 만족할 때까지 3번 과정을 반복한다.
    1. 본 예제에서는 힙 업을 1회 수행한 결과 최대 힙을 만족한다.

### 삽입 최종 결과

<img width="602" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 17 33" src="https://github.com/user-attachments/assets/bd5ea071-91cb-40cc-a53c-6f51e9bf12ac"><img width="602" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 17 33" src="https://github.com/user-attachments/assets/7db02ed1-503e-4854-8788-b2b48612cfa5">

### 삽입 코드

```java
public void add(int value) {
    heap.add(value);
    int idx = heap.size() - 1; // 마지막 위치에 삽입

    // 부모 노드와 비교하며 위로 올라간다.
    while (idx > 0) {
        int parentIdx = (idx - 1) / 2; // 부모 노드의 인덱스
        if (heap.get(parentIdx) < heap.get(idx)) { // 부모 노드 < 자식 노드
            swap(idx, parentIdx); // 두 노드 자리 교체
            idx = parentIdx;
        } else {
            break;
        }
    }
}

// 스왑(Swap)
private void swap(int idx1, int idx2) {
    int tmp = heap.get(idx1);
    heap.set(idx1, heap.get(idx2));
    heap.set(idx2, tmp);
}
```

## 삭제 예제

1. 최대 힙의 경우 가장 큰 값이 루트 노드에 저장된다.
    1. 따라서 루트 노드인 A[0]을 삭제하면 된다.

<img width="536" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 19 01" src="https://github.com/user-attachments/assets/920555e5-fdca-44d5-9ca3-65fc25afe346">

1. 단순히 루트 노드를 삭제하지 않는다.
    1. 루트 노드 A[0]을 삭제하게 되면, 사진처럼 2개의 트리로 끊어진다.

<img width="538" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 20 37" src="https://github.com/user-attachments/assets/8cb6c57b-0305-4ea0-82e7-93df33264aae">

1. 가장 마지막 요소를 루트 노드에 저장하고, 마지막 요소는 삭제한다.
    1. 기존의 가장 마지막 원소인 A[6]이 루트 노드에 저장된다.
    2. A[6] 원소는 삭제된다.

<img width="503" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 21 58" src="https://github.com/user-attachments/assets/70128832-a8de-41d3-9154-812c1306de46">

1. 최대 힙을 만족할 수 있도록 힙 다운(HeapifyDown) 작업을 수행한다.
    1. A[0] < A[1], A[0] < A[2] 이므로 최대 힙을 만족하지 않는다.
    2. 루트 노드(부모 노드)는 두 자식 노드보다 작으므로 왼쪽 or 오른쪽 노드와 교체할 수 있다.
        1. 본 예제에서는 왼쪽 노드와 교체한다.

<img width="515" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 24 02" src="https://github.com/user-attachments/assets/a4434575-c282-4123-b1ec-4716947054c0">


1. 최대 힙의 성질을 만족할 때까지 3번 과정을 반복한다.
    1. A[1] < A[4] 이므로, 두 노드의 자리를 교체한다.
    2. 힙 다운을 2회 수행한 결과 사진처럼 최대 힙 성질을 만족한다.

<img width="523" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 26 34" src="https://github.com/user-attachments/assets/6a86bf3f-dca9-4451-89fb-5b5c21df9899">

### 삭제 최종 결과

<img width="513" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-19_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2 27 50" src="https://github.com/user-attachments/assets/0e622504-bc42-40e6-9501-17429cae1e1d">

### 삭제 코드

```java
public int poll() {
    if (heap.isEmpty()) {
        throw new NoSuchElementException("힙에 요소가 존재하지 않습니다.");
    }

    // 마지막 노드를 루트 노드로 이동한다.
    int root = heap.get(0); // 루트 노드
    int last = heap.remove(heap.size() - 1); // 마지막 노드 제거

    // 마지막 노드가 루트 노드로 왔을 때, 힙의 성질이 깨질 수 있다.
    // 힙의 성질을 만족한다 : 자식 노드의 우선 순위 < 부모 노드의 우선 순위
    // 루트 노드를 제외한 나머지 노드는 힙의 성질을 만족하는 상태이므로, 루트 노드부터 시작해서 "힙 다운" 작업을 통해 힙의 성질을 만족시킨다.
    if (!heap.isEmpty()) {
        heap.set(0, last);
        heapifyDown(0);
    }

    return root;
}

// 삭제 작업 시에 수행되는 힙 다운(Heapfiy)
private void heapifyDown(int idx) {
    int left = (2 * idx) + 1; // 왼쪽 자식
    int right = (2 * idx) + 2; // 오른쪽 자식
    int largest = idx;

    // 왼쪽 자식과 오른쪽 자식 중에 더 큰 노드를 찾는다.
    if (left < heap.size() && heap.get(idx) < heap.get(left)) {
        largest = left;
    }
    if (right < heap.size() && heap.get(idx) < heap.get(right)) {
        largest = right;
    }

    // 현재 노드(idx)보다 자식 노드의 우선 순위가 더 크다면 down 작업 수행
    if (idx != largest) {
        swap(idx, largest);
        heapifyDown(largest);
    }
}
```

## 최대 힙(Max Heap) 코드

```java
class MaxHeap {

    private final List<Integer> heap;

    public MaxHeap() {
        this.heap = new ArrayList<>();
    }

    // 삽입, 반복문
    public void add(int value) {
        heap.add(value);
        int idx = heap.size() - 1; // 마지막 위치에 삽입

        // 부모 노드와 비교하며 위로 올라간다.
        while (idx > 0) {
            int parentIdx = (idx - 1) / 2; // 부모 노드의 인덱스
            if (heap.get(parentIdx) < heap.get(idx)) { // 부모 노드 < 자식 노드
                swap(idx, parentIdx); // 두 노드 자리 교체
                idx = parentIdx;
            } else {
                break;
            }
        }
    }

    // 삽입, 재귀함수
    public void add2(int value) {
        // 1. 새로운 원소 삽입
        heap.add(value);

        // 2. 힙의 성질을 만족하기 위해 "힙 업" 수행
        // 새로운 원소가 부모 노드보다 값이 우선순위가 클 수도 있으므로, 힙 업 해야함.
        heapifyUp(heap.size() - 1);
    }

    // 삭제
    public int poll() {
        if (heap.isEmpty()) {
            throw new NoSuchElementException("힙에 요소가 존재하지 않습니다.");
        }

        // 마지막 노드를 루트 노드로 이동한다.
        int root = heap.get(0); // 루트 노드
        int last = heap.remove(heap.size() - 1); // 마지막 노드 제거

        // 마지막 노드가 루트 노드로 왔을 때, 힙의 성질이 깨질 수 있다.
        // 힙의 성질을 만족한다 : 자식 노드의 우선 순위 < 부모 노드의 우선 순위
        // 루트 노드를 제외한 나머지 노드는 힙의 성질을 만족하는 상태이므로, 루트 노드부터 시작해서 "힙 다운" 작업을 통해 힙의 성질을 만족시킨다.
        if (!heap.isEmpty()) {
            heap.set(0, last);
            heapifyDown(0);
        }

        return root;
    }

    // 스왑(Swap)
    private void swap(int idx1, int idx2) {
        int tmp = heap.get(idx1);
        heap.set(idx1, heap.get(idx2));
        heap.set(idx2, tmp);
    }

    // 힙 업
    private void heapifyUp(int idx) {
        int parentIdx = (idx - 1) / 2; // 부모 인덱스 계산
        if (idx > 0 && heap.get(idx) > heap.get(parentIdx)) { // 부모보다 크면 교환
            swap(idx, parentIdx); // 현재 노드와 부모 노드 교체
            heapifyUp(parentIdx); // 힙의 성질을 만족해야하므로 재귀적으로 힙 업 수행
        }
    }

    // 삭제 작업 시에 수행되는 힙 다운(Heapfiy)
    private void heapifyDown(int idx) {
        int left = (2 * idx) + 1; // 왼쪽 자식
        int right = (2 * idx) + 2; // 오른쪽 자식
        int largest = idx;

        // 왼쪽 자식과 오른쪽 자식 중에 더 큰 노드를 찾는다.
        if (left < heap.size() && heap.get(idx) < heap.get(left)) {
            largest = left;
        }
        if (right < heap.size() && heap.get(idx) < heap.get(right)) {
            largest = right;
        }

        // 현재 노드(idx)보다 자식 노드의 우선 순위가 더 크다면 down 작업 수행
        if (idx != largest) {
            swap(idx, largest);
            heapifyDown(largest);
        }
    }

    @Override
    public String toString() {
        return heap.toString();
    }
}

```

## 시간 복잡도

힙의 경우 삽입, 삭제 시에 재배열하는 heapify 연산이 발생한다. 해당 연산은 트리의 높이만큼 재귀 호출한다. 즉, 삽입 및 삭제 연산은 heapify(재배열) 연산에 의해 시간 복잡도가 결정된다.

- 삽입
    - 시간 복잡도 O(log n)
- 삭제
    - 시간 복잡도 O(log n)
