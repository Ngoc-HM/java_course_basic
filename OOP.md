Lập trình hướng đối tượng (Object-Oriented Programming - OOP) là một trong những nền tảng quan trọng của Java. OOP giúp tổ chức mã nguồn bằng cách sử dụng các **đối tượng (objects)** và **lớp (classes)**. Các khái niệm chính của OOP bao gồm: **tính đóng gói (encapsulation)**, **tính kế thừa (inheritance)**, **tính đa hình (polymorphism)** và **tính trừu tượng (abstraction)**. Dưới đây là chi tiết về từng khái niệm:

### 1. **Lớp (Class) và Đối tượng (Object)**

- **Lớp (Class)**: Một lớp là một khuôn mẫu hoặc bản thiết kế để tạo ra các đối tượng. Lớp định nghĩa các thuộc tính (fields) và phương thức (methods) mà đối tượng sẽ có.
- **Đối tượng (Object)**: Là một thực thể được tạo ra từ lớp. Đối tượng có trạng thái (dữ liệu) và hành vi (phương thức).

Ví dụ:

```java
class Animal {
    // Thuộc tính (fields)
    String name;
    int age;

    // Phương thức (methods)
    void eat() {
        System.out.println(name + " is eating.");
    }

    void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

// Tạo đối tượng từ lớp Animal
public class Main {
    public static void main(String[] args) {
        Animal dog = new Animal();  // Tạo đối tượng dog từ lớp Animal
        dog.name = "Buddy";
        dog.age = 5;
        dog.eat();  // Gọi phương thức eat
        dog.sleep();  // Gọi phương thức sleep
    }
}
```

### 2. **Tính đóng gói (Encapsulation)**

- **Tính đóng gói** là việc giấu thông tin bên trong đối tượng và chỉ cho phép truy cập thông qua các phương thức công khai. Điều này giúp bảo vệ dữ liệu và ngăn truy cập trực tiếp từ bên ngoài.
- Các thuộc tính thường được đặt là `private` và truy cập thông qua các phương thức getter và setter.

Ví dụ:

```java
class Person {
    // Các thuộc tính private chỉ có thể truy cập từ bên trong lớp
    private String name;
    private int age;

    // Getter và Setter để truy cập các thuộc tính
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

### 3. **Tính kế thừa (Inheritance)**

- **Kế thừa** cho phép tạo ra một lớp mới dựa trên lớp đã có, thừa hưởng tất cả các thuộc tính và phương thức của lớp cha (superclass). Lớp con (subclass) có thể thêm các thuộc tính và phương thức mới, hoặc ghi đè (override) các phương thức của lớp cha.
- Kế thừa sử dụng từ khóa `extends`.

Ví dụ:

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    // Ghi đè phương thức makeSound
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.makeSound();  // In ra "Dog barks"
    }
}
```

### 4. **Tính đa hình (Polymorphism)**

- **Đa hình** cho phép một phương thức có nhiều cách thực thi khác nhau. Có hai loại đa hình:
  - **Đa hình lúc biên dịch (Compile-time Polymorphism)**: Là khi một phương thức có thể được gọi bằng nhiều cách, thường được gọi là **nạp chồng phương thức (method overloading)**.
  - **Đa hình lúc chạy (Runtime Polymorphism)**: Là khi một đối tượng của lớp con có thể được gán cho một tham chiếu của lớp cha và gọi các phương thức bị ghi đè.

Ví dụ:

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();  // Đối tượng kiểu Animal
        Animal myCat = new Cat();  // Đa hình - Đối tượng kiểu Cat gán cho biến kiểu Animal
        
        myAnimal.makeSound();  // In ra "Animal makes a sound"
        myCat.makeSound();  // In ra "Cat meows"
    }
}
```

### 5. **Tính trừu tượng (Abstraction)**

- **Trừu tượng** là việc ẩn các chi tiết phức tạp và chỉ hiển thị những thứ cần thiết. Trong Java, trừu tượng được thực hiện thông qua **lớp trừu tượng (abstract class)** và **giao diện (interface)**.
- Lớp trừu tượng có thể có cả phương thức cụ thể (đã định nghĩa) và phương thức trừu tượng (chỉ có phần khai báo, không có phần thân).
- Giao diện chỉ chứa các phương thức trừu tượng và có thể được triển khai bởi các lớp khác.

Ví dụ lớp trừu tượng:

```java
abstract class Animal {
    // Phương thức trừu tượng
    abstract void makeSound();

    // Phương thức cụ thể
    void sleep() {
        System.out.println("Animal is sleeping");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}
```

Ví dụ giao diện:

```java
interface Animal {
    void makeSound();  // Phương thức trừu tượng
}

class Cat implements Animal {
    @Override
    public void makeSound() {
        System.out.println("Cat meows");
    }
}
```

### 6. **Từ khóa quan trọng trong OOP Java**

- **this**: Dùng để tham chiếu đến đối tượng hiện tại.
- **super**: Dùng để tham chiếu đến lớp cha (superclass).
- **final**: Dùng để ngăn chặn kế thừa hoặc ghi đè phương thức.
- **static**: Dùng để định nghĩa các thuộc tính hoặc phương thức có thể được gọi mà không cần tạo đối tượng.

Ví dụ về `this` và `super`:

```java
class Animal {
    String name;

    Animal(String name) {
        this.name = name;  // Dùng this để tham chiếu đến biến của đối tượng hiện tại
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);  // Dùng super để gọi constructor của lớp cha
    }
}
```

Trên đây là toàn bộ khái niệm cơ bản của OOP trong Java. Nếu bạn cần giải thích thêm hoặc ví dụ cụ thể hơn về bất kỳ khái niệm nào, đừng ngần ngại hỏi nhé!