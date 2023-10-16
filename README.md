# JavaSE-UnaryOperator

In Java, UnaryOperator is a functional interface in the java.util.function package. 
 
It represents a function that takes a single argument and produces a result of the same type. 
 
The functional method of UnaryOperator is called apply, and it applies the operation to the given argument.

```java
import java.util.function.UnaryOperator;

public class UnaryOperatorExample {
    public static void main(String[] args) {
        // Example 1: UnaryOperator with Integer
        UnaryOperator<Integer> square = num -> num * num;
        int result1 = square.apply(5);
        System.out.println("Square of 5: " + result1);

        // Example 2: UnaryOperator with String
        UnaryOperator<String> addExclamation = str -> str + "!";
        String result2 = addExclamation.apply("Hello");
        System.out.println("Modified String: " + result2);
    }
}
```

In the first example, we define a UnaryOperator<Integer> called square that squares the input integer.

In the second example, we define a UnaryOperator<String> called addExclamation that adds an exclamation mark to the input string.

The apply method is then called on instances of UnaryOperator, passing the input values, and the result is obtained.

This is particularly useful in scenarios where you need to represent a function that transforms objects of a certain type into objects of the same type.

# More examples of using UnaryOperator in Java:

```java
import java.util.function.UnaryOperator;

public class MoreUnaryOperatorExamples {
    public static void main(String[] args) {
        // Example 1: Convert String to uppercase
        UnaryOperator<String> toUpperCase = String::toUpperCase;
        String result1 = toUpperCase.apply("hello");
        System.out.println("Uppercase: " + result1);

        // Example 2: Increment each element in an Integer array
        UnaryOperator<Integer[]> incrementArray = array -> {
            for (int i = 0; i < array.length; i++) {
                array[i] = array[i] + 1;
            }
            return array;
        };
        Integer[] numbers = {1, 2, 3, 4};
        Integer[] result2 = incrementArray.apply(numbers);
        System.out.println("Incremented Array: " + java.util.Arrays.toString(result2));

        // Example 3: Length of a String
        UnaryOperator<Integer> stringLength = str -> str.length();
        int result3 = stringLength.apply("Java");
        System.out.println("Length of 'Java': " + result3);
    }
}
```

In the first example, the UnaryOperator<String> toUpperCase is used to convert a string to uppercase. 

In the second example, a UnaryOperator<Integer[]> is used to increment each element in an integer array. In the third example, a UnaryOperator<Integer> calculates the length of a string.

These examples showcase different use cases for UnaryOperator based on the type of transformation or operation you want to perform.

# More advance topics about "java.util.function.UnaryOperator"

Let's delve into some more advanced topics and scenarios involving UnaryOperator in Java.

## 1. Chaining UnaryOperators:
You can chain multiple UnaryOperator instances using the andThen method. This creates a new UnaryOperator that represents the composition of two unary operations.

```java
UnaryOperator<Integer> addTwo = x -> x + 2;
UnaryOperator<Integer> square = x -> x * x;

UnaryOperator<Integer> addTwoAndSquare = addTwo.andThen(square);

int result = addTwoAndSquare.apply(3); // (3 + 2)^2 = 25
System.out.println(result);
```

## 2. Using Method References:
You can use method references to simplify the lambda expressions, especially when the lambda expression is calling an existing method.

```java
UnaryOperator<String> toUpperCase = String::toUpperCase;
String result = toUpperCase.apply("hello");
```

## 3. Nullable Input and Output:
If your UnaryOperator can handle null inputs or produce null outputs, you can use the UnaryOperator<T> with T as a nullable type.

```java
UnaryOperator<String> nullableUpperCase = str -> str != null ? str.toUpperCase() : null;
```

## 4. Exception Handling:
When dealing with operations that may throw exceptions, you can use a try-catch block within the lambda expression or wrap it with a helper method.

```java
UnaryOperator<String> safeUpperCase = str -> {
    try {
        return str.toUpperCase();
    } catch (Exception e) {
        // Handle the exception or return a default value
        return "Unable to convert to uppercase";
    }
};
```

## 5. Immutable Objects:
If your object is immutable, you can use UnaryOperator to create a modified copy of the object without changing the original.

```java
class ImmutablePerson {
    private final String name;

    public ImmutablePerson(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

UnaryOperator<ImmutablePerson> changeName = person -> new ImmutablePerson("New " + person.getName());
```

## 6. Functional Composition:
You can use UnaryOperator in functional composition to build more complex functions.

```java
UnaryOperator<Integer> addTwo = x -> x + 2;
UnaryOperator<Integer> square = x -> x * x;

// Composition: (f * g)(x) = f(g(x))
UnaryOperator<Integer> addTwoAndSquare = addTwo.andThen(square);
```

These advanced topics showcase the flexibility and power of UnaryOperator in various scenarios, from composition to handling exceptions and working with immutable objects.
