Item 01 - Consider static factory methods instead of constructor
----------------------------------------------------------------

First of all this *static factory methods* is not the same of *Factory Method* described on book Design Patterns ([wiki](https://en.wikipedia.org/wiki/Factory_method_pattern)).

This item show us that using *static factory methods* - simply a static method that returns an instance of the class - has some advantages over the use common constructor.

1. **Can use a well-chosen name** - Instead the name of class, resulting client code easier to read;
2. **Are not required to create a new object each time** - Allow immutable classes, or cached instances;
3. **Can return an object of any subtype of their return** - ??
4. **The class of the returne object can vary from call to call as a function of the input parameters** - ??
5. **The class of the returned object need not exist when the class containing the method is written** - ??

But this approach has some limitation
1. **Classes without public or protected constructor cannot be subclassed** - ?;
2. **Is hard for programmers to find** -  Sometimes the API documentation cannot be so clear about the methods that returns an instance. For that reason is a good approach uses some commons names;

Common names for *static factory methods* used in Java SDK
* *from* - [Date.from()](https://docs.oracle.com/javase/9/docs/api/java/util/Date.html#from-java.time.Instant-)
```java
Date d = Date.from(instant);
```
* *of* - [EnumSet.of()](https://docs.oracle.com/javase/9/docs/api/java/util/EnumSet.html#of-E-E-E-)
```java
Set<Rank> faceCards = EnumSet.of(JAC, QUEEN, KING);
```
* *valueOf* - [BigInteger.valueOf()](https://docs.oracle.com/javase/9/docs/api/java/math/BigInteger.html#valueOf-long-)
```java
BigInteger prime = BigInteger.valueOf(Integer.MAX_VALUE);
```
* *instance* or *getInstance* - [StackWalker.getInstance()](https://docs.oracle.com/javase/9/docs/api/java/lang/StackWalker.html#getInstance-java.lang.StackWalker.Option-)
```java
StackWalker luke = StackWalker.getInstance(options);
```
* *create* or *newInstance* - [Array.newInstance()](https://docs.oracle.com/javase/9/docs/api/java/lang/reflect/Array.html#newInstance-java.lang.Class-int-)
```java
Object newArray = Array.newInstance(classObject, arrayLen);
```
* *getType* - [Files.getFileStore()](https://docs.oracle.com/javase/9/docs/api/java/nio/file/Files.html#getFileStore-java.nio.file.Path-)
```java
FileStore fs = Files.getFileStore(path);
```
* *newType* - [Files.newBufferedReader()](https://docs.oracle.com/javase/9/docs/api/java/nio/file/Files.html#newBufferedReader-java.nio.file.Path-)
```java
BufferedReader br = Files.newBufferedReader(path);
```
* *type* - [Collections.list()](https://docs.oracle.com/javase/9/docs/api/java/util/Collections.html#list-java.util.Enumeration-)
```java
List<Complaint> litany = Collections.list(legacyLitany);
```
