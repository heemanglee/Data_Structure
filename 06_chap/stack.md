## ArrayList vs LinkedList
![스크린샷 2024-11-19 오전 1 50 08](https://github.com/user-attachments/assets/359df54d-5a52-4cde-84c6-3874cd3db6be)

- ArrayList의 경우 마지막 원소를 top으로 설정한다.
    - 첫 번째 노드가 top이라면? → **시간 복잡도 O(N)** 발생
        - 추가 : 첫 번째 자리에 원소를 삽입하면 기존 모든 원소를 한 칸씩 뒤로 이동한다.
        - 삭제 : 첫 번째 원소를 삭제하면 나머지 원소를 한 칸씩 앞으로 이동한다.
    - 마지막 노드가 top이라면? → **시간 복잡도 O(1)** 발생
        - 추가 : 단순히 배열 끝에 새로운 원소를 추가한다.
        - 삭제 : 마지막 원소를 삭제한다.
- LinkedList는 첫 번째 원소를 top으로 설정한다.
    - 첫 번째 노드가 top이라면? → **시간 복잡도 O(1)** 발생
        - 추가 : 새로운 노드를 생성하고, 기존의 첫 번째 노드를 포인터로 가리킨다.
        - 삭제 : 첫 번째 노드를 삭제하고, 두 번째 노드를 첫 번째 노드로 설정한다.
    - 마지막 노드가 top이라면? → **시간 복잡도 O(N)** 발생
        - 추가 : 새로운 노드를 생성하고 마지막 노드의 포인터를 변경한다. 마지막 노드를 찾기 위해 리스트 전체를 순회한다.
        - 삭제 : 마지막 노드를 삭제하기 위해 리스트를 순회하며 삭제할 노드를 찾아야한다.
<br/>

## ArrayList 기반 Stack

```java
class ArrayStack<T> {

    private final List<T> stack = new ArrayList<>();

    // 삽입
    public T push(T item) {
        stack.add(item);
        return item;
    }

    // 삭제
    public T pop() {
        if (isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return stack.remove(stack.size() - 1);
    }

    // top 조회
    public T peek() {
        if (isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return stack.get(stack.size() - 1);
    }

    // 원소 존재 여부 확인
    public boolean isEmpty() {
        return stack.isEmpty();
    }

    @Override
    public String toString() {
        return stack.toString();
    }
    
}
```
<br/>

## LinkedList 기반 Stack

```java
class LinkedStack<T> {

    private final List<T> stack = new LinkedList<>();

    // 삽입
    public T push(T item) {
        stack.add(0, item);
        return item;
    }

    // 삭제
    public T pop() {
        if (stack.isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return stack.remove(0);
    }

    // top 조회
    public T peek() {
        if (stack.isEmpty()) {
            throw new NoSuchElementException("스택이 비어 있습니다.");
        }
        return stack.get(0);
    }

    // 원소 존재 여부 조회
    public boolean isEmpty() {
        return stack.isEmpty();
    }

    @Override
    public String toString() {
        return stack.toString();
    }
}

```
<br/>

## 후위 연산자 구현

```java
public class Main {

    static final Set<String> operators = Set.of("+", "-", "*", "/");

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        Stack<Integer> stack = new Stack<>();
        for (String input : br.readLine().split(" ")) {
            if (operators.contains(input)) { // 연산자
                int num1 = stack.pop();
                int num2 = stack.pop();
                switch (input) {
                    case "+":
                        stack.push(num2 + num1);
                        break;
                    case "-":
                        stack.push(num2 - num1);
                        break;
                    case "*":
                        stack.push(num2 * num1);
                        break;
                    case "/":
                        stack.push(num2 / num1);
                }
            } else { // 피연산자
                stack.push(Integer.parseInt(input));
            }
        }

        // input : 700 3 47 + 6 * - 4 /
        System.out.println("후위 표현식 계산 결과 : " + stack.pop());
    }
}
```
