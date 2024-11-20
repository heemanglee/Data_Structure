## 선택 정렬(Selection Sort)

> 가장 큰 값을 리스트의 끝으로 보내면서 정렬을 수행하는 방법이다.
 
- 초기 범위 : [0, N - 1]
    - 배열의 크기 : N
    - 범위를 [0, N - 1] → [0, N - 2] → [0, N - 3]처럼 범위를 줄여나가며 정렬을 수행한다.
- 정렬된 값을 제외한, 나머지 값들에 대하여 대소비교하며 정렬을 수행한다.

### 선택 정렬 진행 과정

- 회전이 수행될 때마다, 정렬된 리스트의 크기가 증가한다.
- 부분 리스트는 이미 정렬된 상태이므로, 이를 고려하지 않고 나머지 값들에 대해서만 대소비교를 수행한다.
- `노란색`은 부분 리스트에서 가장 큰 값이며, `회색`은 이미 정렬된 값으로 더이상 고려하지 않아도 되는 값이다.

![스크린샷 2024-11-20 오후 1 37 52](https://github.com/user-attachments/assets/df8706a1-327e-402d-b814-942aceb7a42b)


### 선택 정렬 코드

```java
public class Main {
    public static void main(String[] args) throws IOException {

        int[] arr = {8, 31, 48, 73, 3, 65, 20, 29, 11, 15};
        selectionSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    /**
     * 선택 정렬
     * 시간 복잡도 : O(n^2)
     */
    static void selectionSort(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            int max = -1;
            int idx = -1;
            for (int j = 0; j < arr.length - i; j++) {
                if (max < arr[j]) {
                    max = arr[j];
                    idx = j;
                }
            }
            swap(arr, idx, arr.length - 1 - i);
        }
    }
    
    static void swap(int[] arr, int idx1, int idx2) {
        int tmp = arr[idx1];
        arr[idx1] = arr[idx2];
        arr[idx2] = tmp;
    }
}
```

## 버블 정렬(Bubble Sort)

> 가장 큰 값을 리스트의 끝으로 보내면서 정렬을 수행하는 방법이다.
단, 선택 정렬은 1회전마다 1번의 swap을 한다면, 버블 정렬은 1회전마다 여러 번의 swap이 발생한다.
> 
- 초기 범위 : [0, N - 1]
    - 배열의 크기 : N
    - 범위를 [0, N - 1] → [0, N - 2] → [0, N - 3]처럼 범위를 줄여나가며 정렬을 수행한다.
- 정렬된 값을 제외한, 나머지 값들에 대하여 대소비교하며 정렬을 수행한다.
- 대소비교 시에 A[i] > A[i + 1]을 만족한다면, 두 수를 교환(Swap)한다.

### 버블 정렬 진행 과정

- 회전이 수행될 때마다, 정렬된 리스트의 크기가 증가한다.
- 부분 리스트는 이미 정렬된 상태이므로, 이를 고려하지 않고 나머지 값들에 대해서만 대소비교를 수행한다.
- `노란색`은 인접한 두 수간에 대소비교를 하는 것이고, `회색`은 이미 정렬된 숫자이다.
- 사진은 1회전 결과이며, 동일한 과정을 거쳐 정렬을 수행한다.

![스크린샷 2024-11-20 오후 1 37 31](https://github.com/user-attachments/assets/2840977f-cbf8-40ba-bccd-b0381797e901)


### 버블 정렬 코드

```java
import java.io.IOException;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) throws IOException {

        int[] arr = {8, 31, 48, 73, 3, 65, 20, 29, 11, 15};
        bubbleSort(arr);
        System.out.println(Arrays.toString(arr));
    

    /**
     * 버블 정렬
     * 시간 복잡도 : O(n^2)
     * 버블 정렬은 인접한 두 수간에 대소비교 후, 자리 교환을 수행한다.
        -> 자리를 한 번만 교체하는 "선택 정렬"보다 현저히 느리다.
     */
    static void bubbleSort(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    swap(arr, j, j + 1);
                }
            }
        }
    }

    static void swap(int[] arr, int idx1, int idx2) {
        int tmp = arr[idx1];
        arr[idx1] = arr[idx2];
        arr[idx2] = tmp;
    }
}
```

## 삽입 정렬(Insertion Sort)

> 정렬되어 있는 값들과 대소비교를 하며 정렬하는 방법이다.
반대로 선택 정렬과 버블 정렬은 정렬되어있지 않은 값들과 대소비교하며 정렬한다.
> 
- 초기 범위 : [0, N - 1]
    - 배열의 크기 : N
    - 범위를 [0, N - 1] → [1, N - 1] → [2, N - 1]처럼 범위를 줄여나가며 정렬을 수행한다.
- 정렬된 값들(0 ~ i-1)과 정렬되지 않은 값(i)을 대소비교하며 정렬한다.

### 삽입 정렬 진행 과정

- 회전이 수행될 때마다, 정렬된 리스트의 크기가 증가한다.
- 이미 정렬된 부분 리스트를 사용하여, 정렬되지 않은 값과 대소비교한다.
- `노란색`은 정렬을 해야하는 숫자이고, `회색`은 이미 정렬이 된 숫자들이다.

![스크린샷 2024-11-20 오후 2 05 30](https://github.com/user-attachments/assets/b9cf0c39-8e8d-4a9d-844e-9ea947115759)


### 삽입 정렬 코드

```java
public class Main {
    public static void main(String[] args) throws IOException {

        int[] arr = {8, 31, 48, 73, 3, 65, 20, 29, 11, 15};
        insertionsSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    /**
     * 삽입 정렬
     * 버블, 삽입 정렬 -> "정렬되지 않은" 숫자들과 대소비교를 하며 정렬한다.
     * 삽입 정렬 -> "정렬된" 숫자들과 대소비교를 하며 정렬한다.
     */
    static void insertionsSort(int[] arr) {
        for(int i = 1; i < arr.length; i++) {
            int target = arr[i]; // 기존의 "정렬된 리스트"에 추가할 값
            int j = i - 1; // 정렬된 리스트를 탐색하기 위한 인덱스
            while(j >= 0 && target < arr[j]) {
                arr[j + 1] = arr[j];
                j--;
            }

            arr[j + 1] = target; // 정렬된 리스트에 값을 저장한다.
        }
    }
    
}
```

## 결론
![스크린샷 2024-11-20 오후 2 07 23](https://github.com/user-attachments/assets/7bb33974-6abd-4602-aedf-a55eed242416)
