Các giải thuật sắp xếp là một phần quan trọng trong khoa học máy tính, giúp sắp xếp các phần tử theo một thứ tự nhất định (tăng dần hoặc giảm dần). Có nhiều giải thuật sắp xếp khác nhau, với các ưu nhược điểm riêng. Dưới đây là một số giải thuật sắp xếp phổ biến và cách triển khai chúng trong Java.

### 1. **Sắp xếp nổi bọt (Bubble Sort)**

#### Mô tả:
Sắp xếp nổi bọt là một trong những giải thuật sắp xếp đơn giản nhất. Giải thuật hoạt động bằng cách lặp qua mảng và so sánh từng cặp phần tử liên tiếp, hoán đổi chúng nếu chúng không theo thứ tự mong muốn (ví dụ: nếu phần tử sau nhỏ hơn phần tử trước trong sắp xếp tăng dần).

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(n²) cho cả trường hợp tốt nhất, trung bình và xấu nhất.
- Không hiệu quả cho các mảng lớn, nhưng dễ hiểu và triển khai.

#### Ví dụ:

```java
public class BubbleSort {
    // Hàm sắp xếp nổi bọt
    public static void bubbleSort(int[] array) {
        int n = array.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (array[j] > array[j + 1]) {
                    // Hoán đổi hai phần tử nếu không theo thứ tự
                    int temp = array[j];
                    array[j] = array[j + 1];
                    array[j + 1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        int[] numbers = {64, 34, 25, 12, 22, 11, 90};
        bubbleSort(numbers);
        System.out.println("Sorted array:");
        for (int number : numbers) {
            System.out.print(number + " ");
        }
    }
}
```

### 2. **Sắp xếp chọn (Selection Sort)**

#### Mô tả:
Sắp xếp chọn hoạt động bằng cách tìm phần tử nhỏ nhất (hoặc lớn nhất, tùy theo yêu cầu) từ phần chưa được sắp xếp của mảng và hoán đổi nó với phần tử ở đầu của phần chưa sắp xếp. Quá trình lặp lại cho đến khi toàn bộ mảng được sắp xếp.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(n²).
- Thích hợp cho các tập dữ liệu nhỏ và không yêu cầu thêm bộ nhớ phụ.

#### Ví dụ:

```java
public class SelectionSort {
    // Hàm sắp xếp chọn
    public static void selectionSort(int[] array) {
        int n = array.length;
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;  // Tìm phần tử nhỏ nhất trong phần chưa sắp xếp
            for (int j = i + 1; j < n; j++) {
                if (array[j] < array[minIndex]) {
                    minIndex = j;
                }
            }
            // Hoán đổi phần tử nhỏ nhất với phần tử đầu của phần chưa sắp xếp
            int temp = array[minIndex];
            array[minIndex] = array[i];
            array[i] = temp;
        }
    }

    public static void main(String[] args) {
        int[] numbers = {64, 25, 12, 22, 11};
        selectionSort(numbers);
        System.out.println("Sorted array:");
        for (int number : numbers) {
            System.out.print(number + " ");
        }
    }
}
```

### 3. **Sắp xếp chèn (Insertion Sort)**

#### Mô tả:
Sắp xếp chèn hoạt động bằng cách chia mảng thành hai phần: phần đã được sắp xếp và phần chưa được sắp xếp. Mỗi lần lặp, phần tử đầu tiên của phần chưa được sắp xếp sẽ được chèn vào đúng vị trí của phần đã sắp xếp, đảm bảo rằng phần đã sắp xếp luôn theo đúng thứ tự.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(n²) cho trường hợp xấu nhất, nhưng O(n) cho trường hợp tốt nhất (khi mảng đã gần như sắp xếp).
- Hiệu quả hơn so với sắp xếp nổi bọt và chọn cho các tập dữ liệu nhỏ.

#### Ví dụ:

```java
public class InsertionSort {
    // Hàm sắp xếp chèn
    public static void insertionSort(int[] array) {
        int n = array.length;
        for (int i = 1; i < n; i++) {
            int key = array[i];
            int j = i - 1;

            // Dịch chuyển các phần tử lớn hơn key lên một vị trí
            while (j >= 0 && array[j] > key) {
                array[j + 1] = array[j];
                j = j - 1;
            }
            array[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        int[] numbers = {12, 11, 13, 5, 6};
        insertionSort(numbers);
        System.out.println("Sorted array:");
        for (int number : numbers) {
            System.out.print(number + " ");
        }
    }
}
```

### 4. **Sắp xếp nhanh (Quick Sort)**

#### Mô tả:
Sắp xếp nhanh là một trong những giải thuật sắp xếp hiệu quả nhất. Nó hoạt động bằng cách chọn một phần tử gọi là **pivot**, chia mảng thành hai phần dựa trên pivot (các phần tử nhỏ hơn pivot ở bên trái và các phần tử lớn hơn ở bên phải), sau đó đệ quy sắp xếp hai phần này.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(n log n) cho trường hợp trung bình, O(n²) cho trường hợp xấu nhất.
- Sử dụng rộng rãi trong thực tế do hiệu quả cao, đặc biệt là khi dữ liệu đã được sắp xếp ngẫu nhiên.

#### Ví dụ:

```java
public class QuickSort {
    // Hàm phân chia mảng và chọn pivot
    public static int partition(int[] array, int low, int high) {
        int pivot = array[high];  // Chọn phần tử cuối cùng làm pivot
        int i = low - 1;  // Chỉ số của phần tử nhỏ hơn pivot

        for (int j = low; j < high; j++) {
            if (array[j] <= pivot) {
                i++;
                // Hoán đổi array[i] và array[j]
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }

        // Hoán đổi array[i+1] và pivot
        int temp = array[i + 1];
        array[i + 1] = array[high];
        array[high] = temp;

        return i + 1;  // Trả về vị trí của pivot
    }

    // Hàm sắp xếp nhanh đệ quy
    public static void quickSort(int[] array, int low, int high) {
        if (low < high) {
            int pi = partition(array, low, high);

            // Đệ quy sắp xếp các phần tử trước và sau pivot
            quickSort(array, low, pi - 1);
            quickSort(array, pi + 1, high);
        }
    }

    public static void main(String[] args) {
        int[] numbers = {10, 7, 8, 9, 1, 5};
        quickSort(numbers, 0, numbers.length - 1);
        System.out.println("Sorted array:");
        for (int number : numbers) {
            System.out.print(number + " ");
        }
    }
}
```

### 5. **Sắp xếp trộn (Merge Sort)**

#### Mô tả:
Sắp xếp trộn là giải thuật đệ quy, hoạt động bằng cách chia mảng thành hai nửa, sắp xếp mỗi nửa và sau đó trộn (merge) chúng lại với nhau để tạo thành một mảng đã được sắp xếp.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(n log n) cho mọi trường hợp.
- Sử dụng thêm bộ nhớ phụ để lưu trữ tạm thời các nửa của mảng.

#### Ví dụ:

```java
public class MergeSort {
    // Hàm trộn hai nửa của mảng
    public static void merge(int[] array, int left, int mid, int right) {
        // Tính kích thước của hai nửa
        int n1 = mid - left + 1;
        int n2 = right - mid;

        // Tạo các mảng tạm để chứa hai nửa
        int[] L = new int[n1];
        int[] R = new int[n2];

        // Sao chép dữ liệu vào hai mảng tạm
        for (int i = 0; i < n1; i++) {
            L[i] = array[left + i];
        }
       

 for (int j = 0; j < n2; j++) {
            R[j] = array[mid + 1 + j];
        }

        // Trộn hai mảng tạm lại
        int i = 0, j = 0;
        int k = left;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                array[k] = L[i];
                i++;
            } else {
                array[k] = R[j];
                j++;
            }
            k++;
        }

        // Sao chép các phần tử còn lại của L[] nếu có
        while (i < n1) {
            array[k] = L[i];
            i++;
            k++;
        }

        // Sao chép các phần tử còn lại của R[] nếu có
        while (j < n2) {
            array[k] = R[j];
            j++;
            k++;
        }
    }

    // Hàm sắp xếp trộn đệ quy
    public static void mergeSort(int[] array, int left, int right) {
        if (left < right) {
            int mid = left + (right - left) / 2;

            // Đệ quy sắp xếp hai nửa
            mergeSort(array, left, mid);
            mergeSort(array, mid + 1, right);

            // Trộn hai nửa đã sắp xếp
            merge(array, left, mid, right);
        }
    }

    public static void main(String[] args) {
        int[] numbers = {12, 11, 13, 5, 6, 7};
        mergeSort(numbers, 0, numbers.length - 1);
        System.out.println("Sorted array:");
        for (int number : numbers) {
            System.out.print(number + " ");
        }
    }
}
```

---

### Tổng kết:
- **Bubble Sort**: Đơn giản nhưng không hiệu quả với mảng lớn (O(n²)).
- **Selection Sort**: Hiệu quả hơn Bubble Sort, nhưng vẫn có độ phức tạp O(n²).
- **Insertion Sort**: Tốt cho mảng nhỏ hoặc gần như sắp xếp, có thể đạt O(n) trong trường hợp tốt nhất.
- **Quick Sort**: Nhanh và hiệu quả, với độ phức tạp trung bình O(n log n), nhưng có thể đạt O(n²) trong trường hợp xấu nhất.
- **Merge Sort**: Luôn có độ phức tạp O(n log n), nhưng cần thêm bộ nhớ phụ.
