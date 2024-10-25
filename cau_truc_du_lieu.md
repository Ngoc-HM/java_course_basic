### 1. **Lớp (Class) và Đối tượng (Object)**

Trong OOP, lớp là một khuôn mẫu dùng để tạo ra các đối tượng. Lớp định nghĩa các thuộc tính và phương thức mà đối tượng sẽ có. Khi một đối tượng được tạo ra từ lớp, nó sẽ có những thuộc tính và phương thức mà lớp đã định nghĩa. Cấu trúc lớp và đối tượng là nền tảng của OOP.

#### Cấu trúc:

- **Thuộc tính (Attributes)**: Các biến được khai báo bên trong lớp để lưu trữ trạng thái của đối tượng.
- **Phương thức (Methods)**: Các hàm bên trong lớp để biểu diễn hành vi của đối tượng.

#### Ví dụ:

```java
class Car {
    // Thuộc tính
    String model;
    String color;
    int year;

    // Constructor để khởi tạo đối tượng
    Car(String model, String color, int year) {
        this.model = model;
        this.color = color;
        this.year = year;
    }

    // Phương thức để in thông tin của xe
    void printCarDetails() {
        System.out.println("Model: " + model);
        System.out.println("Color: " + color);
        System.out.println("Year: " + year);
    }
}

public class Main {
    public static void main(String[] args) {
        // Tạo đối tượng car1 từ lớp Car
        Car car1 = new Car("Toyota", "Red", 2020);
        car1.printCarDetails();  // In thông tin của xe
    }
}
```

Trong ví dụ trên, **`Car`** là lớp, và **`car1`** là một đối tượng của lớp **`Car`**. Mỗi đối tượng **Car** có các thuộc tính như **model**, **color**, và **year**.

### 2. **Mảng (Array)**

Mảng là một cấu trúc dữ liệu quan trọng trong OOP, cho phép lưu trữ nhiều giá trị có cùng kiểu dữ liệu. Mảng có thể được dùng như một thuộc tính trong lớp, giúp lưu trữ nhiều đối tượng hoặc dữ liệu liên quan.

#### Đặc điểm:
- Mảng có chỉ số bắt đầu từ 0.
- Độ dài của mảng là cố định sau khi khởi tạo.

#### Ví dụ:

```java
class Classroom {
    // Mảng lưu danh sách tên học sinh
    String[] students;

    // Constructor
    Classroom(String[] students) {
        this.students = students;
    }

    // Phương thức để in danh sách học sinh
    void displayStudents() {
        System.out.println("Danh sách học sinh:");
        for (String student : students) {
            System.out.println(student);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        // Tạo mảng học sinh
        String[] studentNames = {"An", "Bình", "Cường", "Dũng"};
        // Tạo đối tượng Classroom
        Classroom classroom = new Classroom(studentNames);
        // In danh sách học sinh
        classroom.displayStudents();
    }
}
```

Trong ví dụ này, **`students`** là một mảng chứa các tên học sinh và được quản lý bởi lớp **`Classroom`**. Các mảng này giúp lưu trữ nhiều giá trị thuộc cùng một loại (tên học sinh).

### 3. **Danh sách liên kết (Linked List)**

Danh sách liên kết là một cấu trúc dữ liệu mà mỗi phần tử là một **nút (node)**. Mỗi nút chứa dữ liệu và một tham chiếu đến nút tiếp theo trong danh sách. Điều này khác với mảng ở chỗ danh sách liên kết có thể thay đổi kích thước động, trong khi mảng có kích thước cố định.

#### Đặc điểm:
- **Danh sách liên kết đơn (Singly Linked List)**: Mỗi nút chỉ chứa một tham chiếu đến nút tiếp theo.
- **Danh sách liên kết đôi (Doubly Linked List)**: Mỗi nút chứa tham chiếu đến cả nút trước và nút sau.

#### Ví dụ:

```java
// Lớp Node đại diện cho mỗi nút trong danh sách liên kết
class Node {
    int data;  // Dữ liệu của nút
    Node next;  // Tham chiếu đến nút tiếp theo

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

// Lớp LinkedList để quản lý danh sách liên kết
class LinkedList {
    Node head;  // Đầu danh sách liên kết

    // Thêm một nút mới vào cuối danh sách
    void add(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
        } else {
            Node temp = head;
            while (temp.next != null) {
                temp = temp.next;
            }
            temp.next = newNode;
        }
    }

    // In danh sách liên kết
    void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class Main {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.add(10);
        list.add(20);
        list.add(30);
        list.display();  // In ra: 10 20 30
    }
}
```

Ở ví dụ này, danh sách liên kết đơn được triển khai với lớp **`Node`** và **`LinkedList`**. Mỗi nút chứa dữ liệu và tham chiếu đến nút tiếp theo.

### 4. **Ngăn xếp (Stack)**

Ngăn xếp là một cấu trúc dữ liệu tuân theo nguyên tắc **LIFO (Last In, First Out)**, tức là phần tử được thêm vào sau cùng sẽ được lấy ra đầu tiên. Ngăn xếp có thể được triển khai trong OOP thông qua các lớp để quản lý dữ liệu.

#### Đặc điểm:
- **push**: Thêm phần tử vào đỉnh của ngăn xếp.
- **pop**: Lấy phần tử ra khỏi đỉnh của ngăn xếp.

#### Ví dụ:

```java
class Stack {
    int[] stack;  // Mảng lưu trữ các phần tử trong ngăn xếp
    int top;  // Đỉnh của ngăn xếp
    int maxSize;  // Kích thước tối đa của ngăn xếp

    // Constructor
    Stack(int size) {
        stack = new int[size];
        maxSize = size;
        top = -1;
    }

    // Thêm phần tử vào ngăn xếp
    void push(int data) {
        if (top == maxSize - 1) {
            System.out.println("Stack is full");
        } else {
            stack[++top] = data;
        }
    }

    // Lấy phần tử ra khỏi ngăn xếp
    int pop() {
        if (top == -1) {
            System.out.println("Stack is empty");
            return -1;
        } else {
            return stack[top--];
        }
    }

    // Kiểm tra ngăn xếp có rỗng không
    boolean isEmpty() {
        return top == -1;
    }
}

public class Main {
    public static void main(String[] args) {
        Stack myStack = new Stack(5);
        myStack.push(10);
        myStack.push(20);
        myStack.push(30);

        System.out.println(myStack.pop());  // Lấy ra 30
        System.out.println(myStack.pop());  // Lấy ra 20
    }
}
```

### 5. **Hàng đợi (Queue)**

Hàng đợi (Queue) là một cấu trúc dữ liệu tuân theo nguyên tắc **FIFO (First In, First Out)**, nghĩa là phần tử được thêm vào đầu tiên sẽ là phần tử được lấy ra đầu tiên. Cấu trúc này giống như một hàng người xếp hàng: người đầu tiên vào hàng sẽ là người đầu tiên được phục vụ.

Trong OOP và Java, hàng đợi có thể được triển khai bằng cách sử dụng mảng hoặc danh sách liên kết, và nó thường được sử dụng để quản lý các yêu cầu trong hệ thống, như quản lý hàng đợi các tác vụ cần thực hiện trong hệ thống đa nhiệm.

#### Các thao tác chính của hàng đợi:
- **enqueue**: Thêm phần tử vào cuối hàng đợi.
- **dequeue**: Lấy phần tử ra khỏi đầu hàng đợi.
- **isEmpty**: Kiểm tra xem hàng đợi có rỗng không.
- **peek**: Xem phần tử ở đầu hàng đợi mà không loại bỏ nó.

#### Triển khai hàng đợi bằng mảng:

Khi triển khai bằng mảng, hàng đợi sẽ có một chỉ số đầu (front) và chỉ số cuối (rear). Khi thêm phần tử vào hàng đợi, chỉ số `rear` sẽ tăng, và khi lấy phần tử ra khỏi hàng đợi, chỉ số `front` sẽ tăng. Tuy nhiên, cần phải xử lý tốt trường hợp mảng đầy hoặc mảng có chỗ trống ở đầu nhưng lại không thể sử dụng.

##### Ví dụ 1: Hàng đợi tuyến tính bằng mảng

```java
class Queue {
    int[] elements;  // Mảng lưu trữ các phần tử trong hàng đợi
    int front, rear, size, capacity;  // Chỉ số front, rear, kích thước hiện tại và khả năng tối đa của hàng đợi

    // Constructor
    Queue(int capacity) {
        this.capacity = capacity;
        front = 0;
        size = 0;
        rear = -1;
        elements = new int[capacity];
    }

    // Kiểm tra hàng đợi có đầy hay không
    boolean isFull() {
        return size == capacity;
    }

    // Kiểm tra hàng đợi có rỗng hay không
    boolean isEmpty() {
        return size == 0;
    }

    // Thêm phần tử vào hàng đợi
    void enqueue(int data) {
        if (isFull()) {
            System.out.println("Queue is full");
            return;
        }
        rear = (rear + 1) % capacity;  // Đảm bảo rear không vượt quá kích thước mảng
        elements[rear] = data;
        size++;
        System.out.println(data + " enqueued to queue");
    }

    // Lấy phần tử ra khỏi hàng đợi
    int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return Integer.MIN_VALUE;
        }
        int data = elements[front];
        front = (front + 1) % capacity;  // Đảm bảo front không vượt quá kích thước mảng
        size--;
        return data;
    }

    // Xem phần tử ở đầu hàng đợi
    int peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return Integer.MIN_VALUE;
        }
        return elements[front];
    }
}

public class Main {
    public static void main(String[] args) {
        Queue queue = new Queue(5);  // Tạo hàng đợi với kích thước 5

        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);
        queue.enqueue(40);
        queue.enqueue(50);

        System.out.println(queue.dequeue() + " dequeued from queue");  // Lấy phần tử 10 ra khỏi hàng đợi

        System.out.println("Front item is " + queue.peek());  // Phần tử đầu tiên là 20
        System.out.println("Queue isEmpty: " + queue.isEmpty());  // Kiểm tra hàng đợi có rỗng không
    }
}
```

##### Giải thích ví dụ:
- **enqueue**: Khi thêm một phần tử vào cuối hàng đợi, chỉ số `rear` sẽ tăng, và phần tử mới sẽ được thêm vào vị trí `rear`. Khi hàng đợi đầy, thông báo "Queue is full" sẽ hiển thị.
- **dequeue**: Khi lấy phần tử ra khỏi hàng đợi, chỉ số `front` sẽ tăng và phần tử đầu tiên sẽ bị loại bỏ.
- **peek**: Phương thức này giúp xem phần tử ở đầu hàng đợi mà không loại bỏ nó.

### 6. **Hàng đợi liên kết (Linked Queue)**

Khi triển khai hàng đợi bằng **danh sách liên kết** (linked list), chúng ta không cần lo lắng về kích thước cố định như khi sử dụng mảng. Trong hàng đợi liên kết, mỗi phần tử là một nút (node) chứa dữ liệu và một tham chiếu tới phần tử tiếp theo.

#### Ví dụ 2: Hàng đợi bằng danh sách liên kết

```java
// Lớp Node đại diện cho mỗi phần tử trong hàng đợi
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

// Lớp Queue sử dụng danh sách liên kết
class LinkedQueue {
    Node front, rear;

    // Constructor khởi tạo hàng đợi rỗng
    LinkedQueue() {
        this.front = this.rear = null;
    }

    // Kiểm tra hàng đợi có rỗng không
    boolean isEmpty() {
        return front == null;
    }

    // Thêm phần tử vào cuối hàng đợi
    void enqueue(int data) {
        Node newNode = new Node(data);

        // Nếu hàng đợi rỗng, cả front và rear đều là newNode
        if (this.rear == null) {
            this.front = this.rear = newNode;
            return;
        }

        // Thêm newNode vào cuối hàng đợi và cập nhật rear
        this.rear.next = newNode;
        this.rear = newNode;
    }

    // Lấy phần tử ra khỏi đầu hàng đợi
    int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return Integer.MIN_VALUE;
        }

        Node temp = this.front;
        this.front = this.front.next;

        // Nếu front trở thành null, cập nhật rear thành null
        if (this.front == null) {
            this.rear = null;
        }

        return temp.data;
    }

    // Xem phần tử ở đầu hàng đợi mà không lấy ra
    int peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return Integer.MIN_VALUE;
        }
        return this.front.data;
    }
}

public class Main {
    public static void main(String[] args) {
        LinkedQueue queue = new LinkedQueue();

        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);

        System.out.println(queue.dequeue() + " dequeued from queue");  // Lấy ra 10

        System.out.println("Front item is " + queue.peek());  // Phần tử đầu tiên là 20
    }
}
```

##### Giải thích ví dụ:
- **enqueue**: Mỗi lần thêm phần tử vào cuối hàng đợi, một nút mới sẽ được tạo và `rear` sẽ được cập nhật để trỏ tới nút mới đó.
- **dequeue**: Phần tử ở đầu hàng đợi (được tham chiếu bởi `front`) sẽ bị loại bỏ, và `front` sẽ được cập nhật để trỏ tới phần tử tiếp theo. Nếu hàng đợi trở nên rỗng sau khi lấy phần tử ra, cả `front` và `rear` sẽ được đặt thành `null`.

### 7. **Hàng đợi ưu tiên (Priority Queue)**

Hàng đợi ưu tiên là một loại hàng đợi trong đó các phần tử không được xử lý theo thứ tự FIFO thông thường mà theo mức độ ưu tiên. Phần tử có mức độ ưu tiên cao hơn sẽ được xử lý trước, bất kể thời điểm nó được thêm vào hàng đợi.

Trong Java, hàng đợi ưu tiên có thể được triển khai bằng **PriorityQueue**, trong đó các phần tử có thể được so sánh với nhau để xác định thứ tự ưu tiên.

#### Ví dụ 3: Hàng đợi ưu tiên sử dụng `PriorityQueue`:

```java
import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) {
        // Tạo PriorityQueue
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

        // Thêm phần tử vào hàng đợi
        priorityQueue.add(30);
        priorityQueue.add(10);
        priorityQueue.add(20);

        // Lấy phần tử ra khỏi hàng đợi theo thứ tự ưu tiên
        System.out.println(priorityQueue.poll());  // In ra 10 (ưu tiên thấp nhất)
        System.out.println(priorityQueue.poll());  // In ra 20
        System.out.println(priorityQueue.poll());  // In ra 30
    }
}
```

#### Giải thích:
- **`PriorityQueue`**: Các phần tử được sắp xếp theo thứ tự tự nhiên (ví dụ: số nhỏ nhất có ưu tiên cao hơn).
- **`poll()`**: Lấy phần tử có ưu tiên cao nhất ra khỏi hàng đợi.
