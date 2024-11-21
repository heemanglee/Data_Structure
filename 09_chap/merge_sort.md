## 합병 정렬(Merge Sort)

> 하나의 리스트를 `균등한 크기의 두 개의 리스트로 분할하고, 분할된 부분 리스트를 정렬한다.
정렬된 부분 리스트를 합쳐 하나의 전체 리스트를 만든다.
> 

합병 정렬은 세 가지 과정을 거친다.

1. 분할(Divide) : 입력 배열을 같은 크기의 2개의 부분 배열로 분할한다.
2. 정복(Conquer) : 부분 배열을 정렬한다. 
3. 결합(Combine) : 정렬된 부분 배열들을 하나의 배열에 합병한다.

### 분할 과정

1번 과정에서는 두 개의 포인터(`left`, `right`)를 사용하여 중간 인덱스(`mid`)를 계산한다. 중간 인덱스를 기준으로 `균등한 크기`의 `두 개의 부분 배열`로 분리한다.

위 과정은 `left == right`를 만족할 때까지 반복한다. left == right는 `부분 배열의 크기가 1`임을 의미한다. 부분 배열의 크기가 1이라는 것은 더이상 분할(Divide)할 원소가 없음을 의미한다.

아래 사진은 원본 배열(original)을 균등한 크기로 분할한 배열 중에서, 왼쪽 배열이 분할되는 과정이다.

![%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-21_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4 18 27](https://github.com/user-attachments/assets/1d6df87a-816b-4240-9edb-2e3b9316efe4)


### 정복 및 결합 과정

분할이 완료된 부분 배열에 대해 `정복 및 결합`을 수행한다. 

![%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-21_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4 30 52](https://github.com/user-attachments/assets/05e0e5c4-a680-422a-8f6a-94a9c93b66d1)


### 최종 결과

최종 결과는 다음과 같다.

![%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-11-21_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4 32 17](https://github.com/user-attachments/assets/9fe959f6-851c-4a51-b04d-3bbf04582afe)


### 합병 정렬 코드

- 시간 복잡도 : `O(n logn)`
    - 최악, 평균, 최선 모두 해당
- 분할된 부분 배열을 정렬하는 과정에서 임시 리스트 sorted가 사용된다. → `추가 공간`이 사용된다.
    - 두 개의 부분 리스트를 하나로 합쳐서 정렬한 결과를 sorted에 저장하고, 원본 리스트 original에 복사한다.

```java
public class MergeSort {

    static int[] original = {21, 10, 12, 20, 25, 13, 15, 22};
    static int[] sorted;

    public static void main(String[] args) {
        sorted = new int[original.length];
        merge_sort(0, original.length - 1);

        System.out.println(Arrays.toString(original));
    }

    static void merge_sort(int left, int right) {
        int mid;

        if (left < right) {
            mid = (left + right) / 2; // 중간 인덱스
            merge_sort(left, mid); // 분할(Divide)
            merge_sort(mid + 1, right); // 분할(Divide)
            merge(left, mid, right); // 정복(Conquer) && 결합(Combine)
        }
    }

    static void merge(int left, int mid, int right) {
        int i = left;
        int j = mid + 1;
        int k = left;

        while (i <= mid && j <= right) {
            if (original[i] < original[j]) {
                sorted[k++] = original[i++];
            } else {
                sorted[k++] = original[j++];
            }
        }

        if (i > mid) { // 2개의 부분 배열(왼쪽, 오른쪽)이 존재할 때, 왼쪽 배열이 정렬된 경우
            for (int l = j; l <= right; l++) { // 오른쪽 배열에 정렬되지 않은 값들을 임시 리스트(sorted)에 저장한다.
                sorted[k++] = original[l];
            }
        }
        if (j > right) { // 2개의 부분 배열(왼쪽, 오른쪽) 중에서, 오른쪽 배열이 정렬된 경우
            for (int l = i; l <= mid; l++) { // 왼쪽 배열에 정렬되지 않은 값들을 임시 리스트(sorted)에 저장한다.
                sorted[k++] = original[l];
            }
        }

        // 임시 리스트(sorted)에 저장된 정렬된 값들을 원본 리스트(original)에 복사한다.
        for (int l = left; l <= right; l++) {
            original[l] = sorted[l];
        }
    }
}

```




참고
https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html
