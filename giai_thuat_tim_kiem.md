Các giải thuật tìm kiếm là một trong những thành phần cơ bản và quan trọng của khoa học máy tính, đặc biệt là trong xử lý dữ liệu. Có nhiều giải thuật tìm kiếm khác nhau, và dưới đây là những giải thuật tìm kiếm phổ biến nhất cùng với cách chúng hoạt động và ví dụ minh họa trong Java.

### 1. **Tìm kiếm tuyến tính (Linear Search)**

#### Mô tả:
Tìm kiếm tuyến tính là giải thuật đơn giản nhất, trong đó ta duyệt qua từng phần tử của danh sách từ đầu đến cuối và so sánh với giá trị cần tìm. Nếu tìm thấy, trả về vị trí của phần tử; nếu không, trả về kết quả là không tìm thấy.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(n) với n là số phần tử trong danh sách.
- Thích hợp cho các danh sách nhỏ hoặc không có yêu cầu về sắp xếp.

#### Ví dụ:

```java
public class LinearSearch {
    // Hàm tìm kiếm tuyến tính
    public static int linearSearch(int[] array, int target) {
        for (int i = 0; i < array.length; i++) {
            if (array[i] == target) {
                return i;  // Trả về vị trí của phần tử cần tìm
            }
        }
        return -1;  // Không tìm thấy phần tử
    }

    public static void main(String[] args) {
        int[] numbers = {10, 30, 25, 50, 40};
        int target = 30;
        int result = linearSearch(numbers, target);

        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

### 2. **Tìm kiếm nhị phân (Binary Search)**

#### Mô tả:
Tìm kiếm nhị phân chỉ hoạt động trên các mảng đã sắp xếp. Giải thuật hoạt động bằng cách chia mảng thành hai nửa và so sánh giá trị cần tìm với phần tử giữa mảng. Nếu giá trị cần tìm nhỏ hơn phần tử giữa, tiếp tục tìm kiếm ở nửa bên trái, ngược lại tìm kiếm ở nửa bên phải.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(log n), với n là số phần tử trong danh sách.
- Tốc độ nhanh hơn nhiều so với tìm kiếm tuyến tính, nhưng yêu cầu mảng phải được sắp xếp trước.

#### Ví dụ:

```java
public class BinarySearch {
    // Hàm tìm kiếm nhị phân
    public static int binarySearch(int[] array, int target) {
        int left = 0;
        int right = array.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            // Kiểm tra phần tử giữa
            if (array[mid] == target) {
                return mid;  // Trả về vị trí của phần tử cần tìm
            }

            // Nếu phần tử giữa lớn hơn giá trị cần tìm, tìm bên trái
            if (array[mid] > target) {
                right = mid - 1;
            } else {
                // Nếu phần tử giữa nhỏ hơn, tìm bên phải
                left = mid + 1;
            }
        }

        return -1;  // Không tìm thấy phần tử
    }

    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};  // Mảng đã sắp xếp
        int target = 30;
        int result = binarySearch(numbers, target);

        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

### 3. **Tìm kiếm nhị phân đệ quy (Recursive Binary Search)**

#### Mô tả:
Tìm kiếm nhị phân có thể được triển khai bằng cách sử dụng đệ quy. Thay vì sử dụng vòng lặp, phương pháp đệ quy sẽ liên tục chia mảng và gọi lại chính nó để tìm kiếm trong nửa bên trái hoặc bên phải cho đến khi tìm thấy giá trị cần tìm hoặc kết thúc quá trình.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(log n).
- Yêu cầu mảng phải được sắp xếp.

#### Ví dụ:

```java
public class RecursiveBinarySearch {
    // Hàm tìm kiếm nhị phân đệ quy
    public static int recursiveBinarySearch(int[] array, int left, int right, int target) {
        if (left <= right) {
            int mid = left + (right - left) / 2;

            // Kiểm tra phần tử giữa
            if (array[mid] == target) {
                return mid;  // Trả về vị trí của phần tử cần tìm
            }

            // Nếu phần tử giữa lớn hơn giá trị cần tìm, tìm bên trái
            if (array[mid] > target) {
                return recursiveBinarySearch(array, left, mid - 1, target);
            }

            // Nếu phần tử giữa nhỏ hơn, tìm bên phải
            return recursiveBinarySearch(array, mid + 1, right, target);
        }

        return -1;  // Không tìm thấy phần tử
    }

    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};  // Mảng đã sắp xếp
        int target = 40;
        int result = recursiveBinarySearch(numbers, 0, numbers.length - 1, target);

        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

### 4. **Tìm kiếm nhảy (Jump Search)**

#### Mô tả:
Tìm kiếm nhảy hoạt động trên các mảng đã sắp xếp. Giải thuật này duyệt qua mảng bằng cách "nhảy" các bước cố định và sau đó thực hiện tìm kiếm tuyến tính trong phạm vi bước nhảy đó nếu tìm thấy một phần tử lớn hơn hoặc bằng giá trị cần tìm.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(√n).
- Thích hợp cho các mảng lớn đã được sắp xếp.

#### Ví dụ:

```java
public class JumpSearch {
    // Hàm tìm kiếm nhảy
    public static int jumpSearch(int[] array, int target) {
        int length = array.length;
        int step = (int) Math.sqrt(length);  // Bước nhảy (căn bậc hai của độ dài mảng)
        int prev = 0;

        // Nhảy tới vị trí có phần tử lớn hơn hoặc bằng giá trị cần tìm
        while (array[Math.min(step, length) - 1] < target) {
            prev = step;
            step += (int) Math.sqrt(length);
            if (prev >= length) {
                return -1;  // Không tìm thấy
            }
        }

        // Thực hiện tìm kiếm tuyến tính trong phạm vi bước nhảy
        while (array[prev] < target) {
            prev++;
            if (prev == Math.min(step, length)) {
                return -1;  // Không tìm thấy
            }
        }

        // Kiểm tra nếu phần tử được tìm thấy
        if (array[prev] == target) {
            return prev;
        }

        return -1;  // Không tìm thấy
    }

    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50, 60, 70, 80};  // Mảng đã sắp xếp
        int target = 40;
        int result = jumpSearch(numbers, target);

        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

### 5. **Tìm kiếm nội suy (Interpolation Search)**

#### Mô tả:
Tìm kiếm nội suy là phiên bản nâng cao của tìm kiếm nhị phân, áp dụng cho các mảng đã sắp xếp mà trong đó các giá trị được phân bố đều. Thay vì chọn phần tử giữa, tìm kiếm nội suy tính toán vị trí dựa trên giá trị cần tìm và giá trị ở đầu và cuối mảng.

#### Đặc điểm:
- **Độ phức tạp thời gian**: O(log log n) trong trường hợp tốt nhất, O(n) trong trường hợp tệ nhất.
- Thích hợp khi các phần tử trong mảng được phân bố đều.

#### Ví dụ:

```java
public class InterpolationSearch {
    // Hàm tìm kiếm nội suy
    public static int interpolationSearch(int[] array, int target) {
        int low = 0;
        int high = array.length - 1;

        while (low <= high && target >= array[low] && target <= array[high]) {
            if (low == high) {
                if (array[low] == target) {
                    return low;
                }
                return -1;
            }

            // Tính toán vị trí dựa trên giá trị cần tìm
            int pos = low + (((high - low)

 / (array[high] - array[low])) * (target - array[low]));

            // Kiểm tra phần tử tại vị trí đã tính toán
            if (array[pos] == target) {
                return pos;
            }

            // Nếu giá trị cần tìm lớn hơn phần tử tại pos, tìm bên phải
            if (array[pos] < target) {
                low = pos + 1;
            } else {
                // Nếu giá trị cần tìm nhỏ hơn, tìm bên trái
                high = pos - 1;
            }
        }

        return -1;  // Không tìm thấy phần tử
    }

    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50, 60, 70};  // Mảng đã sắp xếp
        int target = 50;
        int result = interpolationSearch(numbers, target);

        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---
