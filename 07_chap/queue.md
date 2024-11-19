## ArrayQueue

- ArrayList를 사용하여 Queue를 구현한다

```java
class ArrayQueue<T> {

    private final List<T> que = new ArrayList<>();

    // 삽입
    public T offer(T item) {
        que.add(item);
        return item;
    }

    // 삭제
    public T poll() {
        if (que.isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return que.remove(0);
    }

    // front 노드 조회
    public T peek() {
        if (que.isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return que.get(0);
    }

    public boolean isEmpty() {
        return que.isEmpty();
    }
}
```
<br/>

## LinkedQueue

- LinkedList를 사용하여 Queue를 구현한다.

```java
class LinkedQueue<T> {

    private final List<T> que = new LinkedList<>();

    // 삽입
    public T offer(T item) {
        que.add(item);
        return item;
    }

    // 삭제
    public T poll() {
        if (que.isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return que.remove(0);
    }

    // front 노드 조회
    public T peek() {
        if (que.isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return que.get(0);
    }

    public boolean isEmpty() {
        return que.isEmpty();
    }

}
```
<br/>

## Queue의 구현체
![스크린샷 2024-11-19 오전 9 44 24](https://github.com/user-attachments/assets/d3b9e2f5-505c-4f9a-8dbe-82b6a08af3ea)

### Queue의 구현체로 ArrayList를 사용할 수 없다.

Queue의 구현체로 LinkedList는 존재하나, ArrayList는 존재하지 않는다.

ArrayQueue처럼 ArrayList를 사용하여 Queue를 흉내낼 수 있겠지만, FIFO 특성상 성능이 비효율적이다.

FIFO(First In, First Out)는 먼저 삽입한 데이터부터 추출할 수 있다. 

즉, 데이터는 tail 노드로 삽입하되, 데이터 추출은 front 노드부터 한다.

이때, ArrayList에서 마지막 노드에 데이터를 삽입하는 `시간 복잡도는 O(1)`이지만, 중간에 있는 데이터를 삭제하는 경우 `시간 복잡도는 O(N)`이다. → 삭제된 노드를 기준으로 나머지 노드가 한 칸 씩 앞으로 복사 작업이 발생한다.
<br/>

### Queue의 구현체로 LinkedList를 사용할 수 있다.

```java
Queue<Character> que = new LinkedList<>();
```

LinkedList 자료 구조는 노드 기반의 자료 구조이다. 따라서 front 노드와 tail 노드가 존재한다.

FIFO 구조는 데이터 삽입 시에 마지막 노드에 삽입하게 되는데, 기존의 tail 노드를 삽입하는 새로운 노드를 가리키도록 하면 된다. → `시간 복잡도 O(1)`

데이터 추출의 경우 front 노드를 추출하고, front 노드를 다음 노드를 가리키도록 하면 된다. → `시간 복잡도 O(1)`

따라서 Queue의 구현체로 ArrayList가 아닌 LinkedList가 사용된다.

<br/>

## 팰린드롬(Palindrome) 구현하기

- `Stack`과 `Queue`를 사용하여 팰린드롬 여부를 확인할 수 있다.
- Stack은 마지막 요소부터 추출하고, Queue는 첫번째 요소부터 추출한다.
- Stack과 Queue에서 요소를 하나씩 추출하여 동일한 문자인지 확인한다.

```java
public class Main {
    public static void main(String[] args) throws IOException {
        String str = "lioninoil";
        System.out.println("팰린드롬인가? " + isPalindrome(str));
    }

    static boolean isPalindrome(String str) {
        Queue<Character> que = new LinkedList<>();
        Stack<Character> stack = new Stack<>();

        for (char c : str.toCharArray()) {
            que.offer(c);
            stack.push(c);
        }

        while (!que.isEmpty() && !stack.isEmpty()) {
            if (que.poll() != stack.pop()) {
                break;
            }
        }

        return stack.isEmpty();
    }
}
```
<br/>

그러나 Stack과 Queue를 사용하지 않고 단순히 배열만을 사용하여 팰린드롬 여부를 확인할 수 도 있다.

```java
public class Main {
    public static void main(String[] args) throws IOException {
        String str = "lioninoil";
        System.out.println("팰린드롬인가? " + isPalindrome(str));
    }

    static boolean isPalindrome(String str) {
        char[] arr = str.toCharArray();
        for (int i = 0; i < arr.length / 2; i++) {
            if (arr[i] != arr[arr.length - 1 - i]) {
                return false;
            }
        }
        return true;
    }
}
```
