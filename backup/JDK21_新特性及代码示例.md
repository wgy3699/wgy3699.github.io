JDK 21 作为 Java 语言和平台的最新更新版本，引入了许多有趣的新特性和增强功能，继续提升开发者的生产力和应用的性能。以下是一些主要的新特性：

### 1. Virtual Threads (虚拟线程)

虚拟线程是 Java 项目 Loom 的一部分，旨在简化并发编程并提高并发任务的性能。虚拟线程提供轻量级的线程实现，允许数以百万计的线程在 JVM 中有效运行。

**代码示例：**
```java
import java.util.concurrent.Executors;

public class VirtualThreadsExample {
    public static void main(String[] args) throws InterruptedException {
        try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
            for (int i = 0; i < 10; i++) {
                int taskNumber = i;
                executor.submit(() -> {
                    System.out.println("Task " + taskNumber + " is running on: " + Thread.currentThread());
                });
            }
        }
    }
}
```
**说明：**
此代码示例展示了如何使用虚拟线程执行并发任务，代码中使用 `Executors.newVirtualThreadPerTaskExecutor()` 创建了一个虚拟线程执行器。

### 2. Pattern Matching for Switch (switch 模式匹配)

JDK 21 引入了 switch 语句的模式匹配增强功能，使得代码更加简洁和类型检查更加灵活。

**代码示例：**
```java
public class PatternMatchingSwitchExample {
    public static void main(String[] args) {
        Object obj = "Hello, Java!";
        
        switch (obj) {
            case String s -> System.out.println("It's a string: " + s);
            case Integer i -> System.out.println("It's an integer: " + i);
            default -> System.out.println("Unknown type");
        }
    }
}
```
**说明：**
该示例展示了如何使用模式匹配在 `switch` 语句中检查变量的类型，并在匹配后执行相应的操作。

### 3. Record Patterns (记录模式)

记录模式允许对记录类型（record）进行更深入的模式匹配，简化了从对象中提取数据的过程。

**代码示例：**
```java
public record Point(int x, int y) {}

public class RecordPatternExample {
    public static void main(String[] args) {
        Object obj = new Point(3, 4);

        if (obj instanceof Point(int x, int y)) {
            System.out.println("Point coordinates: x = " + x + ", y = " + y);
        }
    }
}
```
**说明：**
在该示例中，使用记录模式从 `Point` 对象中提取了 `x` 和 `y` 值，这样的代码更加直观和简洁。

### 4. Sequenced Collections (顺序集合)

JDK 21 引入了顺序集合接口 `SequencedCollection`，用于提供有序集合操作，适用于列表、队列等数据结构。

**代码示例：**
```java
import java.util.*;

public class SequencedCollectionExample {
    public static void main(String[] args) {
        SequencedCollection<String> sequencedList = new LinkedHashSet<>(List.of("a", "b", "c"));
        sequencedList.addFirst("first");
        sequencedList.addLast("last");

        sequencedList.forEach(System.out::println);
    }
}
```
**说明：**
此示例展示了如何使用新的顺序集合接口操作 `LinkedHashSet`，它提供了 `addFirst` 和 `addLast` 方法来操作集合的顺序。

### 5. Scoped Values (范围值)

JDK 21 引入了 `ScopedValues`，为局部数据的传递提供了更高效和安全的方式，尤其适用于并发上下文中。

**代码示例：**
```java
import jdk.incubator.concurrent.ScopedValue;

public class ScopedValuesExample {
    private static final ScopedValue<String> USER = ScopedValue.newInstance();

    public static void main(String[] args) {
        ScopedValue.where(USER, "Alice").run(() -> {
            System.out.println("Current user: " + USER.get());
        });
    }
}
```
**说明：**
`ScopedValue` 提供了一种更安全的方式来在不同的代码块之间传递数据，避免了使用线程局部变量的复杂性和安全隐患。

### JDK 21 与 JDK 17 的性能对比

JDK 21 相对于 JDK 17 进行了多方面的改进，尤其是在并发性能和语法增强方面。

1. **虚拟线程的性能提升**：相比于 JDK 17 中传统的线程模型，JDK 21 的虚拟线程可以更轻松地处理大量并发任务，使得服务器应用的吞吐量显著提升。传统线程的上下文切换开销较高，而虚拟线程则通过轻量级的方式来管理大量任务。

2. **模式匹配的简化**：JDK 21 的 `switch` 模式匹配相比 JDK 17，减少了手动类型检查和类型转换的代码量，代码更加简洁且不易出错，提高了开发效率。

3. **内存使用效率**：JDK 21 引入了 `ScopedValues`，可以替代部分线程局部变量的使用，从而减少内存占用，提高并发程序的整体内存使用效率。