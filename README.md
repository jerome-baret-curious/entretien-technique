# Pour les entretiens techniques

## POO

## Programmation fonctionnelle

## Programmation événementielle

## Programmation orientée aspect

## Programmation réactive

## Java

### Java 17

```java
record Rectangle(double length, double width) { }
```

équivaut à

```java
public final class Rectangle {
    private final double length;
    private final double width;

    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }

    double length() { return this.length; }
    double width()  { return this.width; }

    public boolean equals...
    public int hashCode...

    public String toString() {...}
}
```

```java
public sealed interface Result<E, A> {

    record Success<E, A>(A value) implements Result<E, A> {
    }

    record Failure<E, A>(E error) implements Result<E, A> {
    }
}
```

```java
public sealed interface Shape permits Polygon { }
public non-sealed interface Polygon extends Shape { }
public final class UtahTeapot { }
public class Ring { }

public void work(Shape s) {
    UtahTeapot u = (UtahTeapot) s;  // Error
    Ring r = (Ring) s;              // Permitted
}
```

```java
public static boolean bigEnoughRect(Shape s) {
    if (!(s instanceof Rectangle r)) {
        // Cannot use r here
        return false;
    }
    return r.length() > 5; 
}
```

Une ``switch`` expression ``yield`` obligatoirement
```java
int numLetters = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> {
        System.out.println(6);
        yield 6;
    }
    case TUESDAY -> {
        System.out.println(7);
        yield 7;
    }
    case WEDNESDAY -> 3;
    default -> {
        throw new IllegalStateException("Invalid day: " + day);
    }
};
```

En preview, pour les ``switch`` expression et statement
```java
static void test(Object obj) {
    switch (obj) {
        case null -> System.out.println("null!");
        case Character c -> {
            if (c.charValue() == 7) {
                System.out.println("Ding!");
            }
            System.out.println("Character, value " + c.charValue());
        }
        case Integer i -> System.out.println("Integer: " + i);  
        default -> throw new IllegalStateException("Invalid argument"); 
    }
}
```

### Java 21

```java
static void printSum(Object obj) {
    if (obj instanceof Point(int x, int y)) {
        System.out.println(x+y);
    }
}
```

```java
public record Point(int x, int y) {
}

class Cartesian {

    static void printQuadrant(Point p) {
        switch (p) {
            case Point(var x, var y) when x > 0 && y > 0 -> 
                System.out.println("first");
            default -> 
                System.out.println("other");
        }
    }
}
```

Les virtual threads pour les applications concurrentes à haut débit.

### Spring

Différences ApplicationContext et BeanFactory

#### Spring Boot

#### Spring MVC

#### Spring Data

#### Spring Security

#### Spring Batch

### Quarkus

Différences avec Spring Boot

## Hibernate

## Angular

### Cycle de vie des composants

### Injection de dépendances

### Formulaires

#### Reactive forms

FormControl

#### Template-driven forms

ngModel

### Angular router

## RxJS

## Vue

### Réactivité

### Vue Router
