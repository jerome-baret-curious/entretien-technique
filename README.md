# Pour les entretiens techniques

## POO

Abstraction, encapsulation, composition, héritage, polymorphisme, récursion ouverte (les méthodes d'objet peuvent appeler des méthodes du même objet)

Single responsibility : au maximum une raison de changer une classe

Open-closed : ouverture aux extensions, mais fermeture aux modifications

Substitution de Liskov : un objet de classe T peut être remplacé par un objet d'une classe S dérivée de T

Ségrégation des interfaces : le code ne doit pas être forcé de dépendre de méthodes qu'il n'utilise pas (=> faire de petites interfaces)

Inversion de dépendances : dépendances envers des abstractions

## Programmation fonctionnelle

Fonctions de première classe, d'ordre supérieur, pures, récursivité, évaluation stricte ou non, typage, transparence référentielle (les variables sont constantes), structures de données

## Programmation événementielle

Exécution d'une fonction en réaction à un événement, généralement grâce à une boucle qui attend les événements

## Programmation orientée aspect

Ajout de comportements à un code existant. Cela permet de séparer les logiques

## Programmation réactive

Propagation du changement

Optimise le temps CPU, lequel est coûteux

## Java

JVM : machine virtuelle exécutant le bytecode Java

JRE : environnement d'exécution Java (JVM + lib)

JDK : des libs et des outils dont le compilateur


Cycle de vie d'un Thread :

NEW, avant l'appel à ``start()``

RUNNABLE, en cours d'exécution ou prêt à l'être

BLOCKED, en attente de moniteur

WAITING, en attente d'un autre thread

TIMED_WAITING, en attente d'un autre thread avec un temps maximal

TERMINATED, l'exécution est terminée, normalement ou non

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

La ``BeanFactory`` fournit un mécanisme de configuratio capable de gérer n'importe quel objet. L'``ApplicationContext`` ajoute une intégration à Spring AOP, l'internationalisation,
la publication d'événements et des contextes spécifiques.

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

#### Nested routes

#### Lazy loading

#### Guards

## RxJS

## Vue

### Réactivité

### Vue Router
