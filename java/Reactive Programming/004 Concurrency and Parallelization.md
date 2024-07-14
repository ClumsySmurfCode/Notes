![image](https://github.com/user-attachments/assets/319efbc8-4c80-4ee0-b7a3-692cb8bb4579)


# Concurrency and Parallelization in RxJava

## Introduction
Concurrency and parallelization are key concepts in reactive programming with RxJava. Concurrency refers to the ability to handle multiple tasks at the same time, while parallelization refers to executing multiple tasks simultaneously. RxJava provides several operators and schedulers to help manage these concepts effectively.

## Schedulers
Schedulers in RxJava are a way of controlling the threads on which an Observable operates. There are several built-in schedulers in RxJava:

- `Schedulers.io()`
- `Schedulers.computation()`
- `Schedulers.newThread()`
- `Schedulers.single()`
- `Schedulers.trampoline()`
- `Schedulers.from(Executor)`

### Example
```java
Observable.just("Task")
    .subscribeOn(Schedulers.io())
    .observeOn(Schedulers.computation())
    .subscribe(System.out::println);
```

## Common Operators for Concurrency and Parallelization

### `subscribeOn`
Specifies the Scheduler on which an Observable should operate.

``` java
Observable.just("Task")
    .subscribeOn(Schedulers.io())
    .subscribe(System.out::println);
```

### `observeOn` 
Specifies the Scheduler on which an Observer should observe the Observable.

```java
Observable.just("Task")
    .observeOn(Schedulers.computation())
    .subscribe(System.out::println);
```

### `flatMap` 
Transforms the items emitted by an Observable into Observables, then flattens these Observables into a single Observable.

```java
Observable.just(1, 2, 3, 4)
    .flatMap(item -> Observable.just(item)
        .subscribeOn(Schedulers.computation())
        .map(i -> i * 2))
    .subscribe(System.out::println);
```

### `concatMap`
Similar to flatMap, but preserves the order of the emitted items.

```java
Observable.just(1, 2, 3, 4)
    .concatMap(item -> Observable.just(item)
        .subscribeOn(Schedulers.computation())
        .map(i -> i * 2))
    .subscribe(System.out::println);
```

### `merge` 
Combines multiple Observables into one by merging their emissions.

```java
Observable<String> observable1 = Observable.just("Task1")
    .subscribeOn(Schedulers.io());
Observable<String> observable2 = Observable.just("Task2")
    .subscribeOn(Schedulers.io());

Observable.merge(observable1, observable2)
    .subscribe(System.out::println);
```

## Advanced Concurrency Operators

### `zip`
Combines multiple Observables into one by combining their emissions with a specified function.

```java
Observable<String> observable1 = Observable.just("Task1")
    .subscribeOn(Schedulers.io());
Observable<String> observable2 = Observable.just("Task2")
    .subscribeOn(Schedulers.io());

Observable.zip(observable1, observable2, (task1, task2) -> task1 + " & " + task2)
    .subscribe(System.out::println);
```

### `combineLatest`
Combines the latest values from multiple Observables and emits them as a single Observable.

```java
Observable<String> observable1 = Observable.just("Task1")
    .subscribeOn(Schedulers.io());
Observable<String> observable2 = Observable.just("Task2")
    .subscribeOn(Schedulers.io());

Observable.combineLatest(observable1, observable2, (task1, task2) -> task1 + " & " + task2)
    .subscribe(System.out::println);
```

### `switchMap`
Maps each item to an Observable, then flattens these Observables into a single Observable, cancelling the previous Observable if a new item is emitted.

```java
Observable.just(1, 2, 3, 4)
    .switchMap(item -> Observable.just(item)
        .subscribeOn(Schedulers.computation())
        .map(i -> i * 2))
    .subscribe(System.out::println);
```

### `amb`
Given two or more source Observables, amb emits all of the items from only the first of these Observables to emit an item or notification.

```java
Observable<String> observable1 = Observable.just("Task1")
    .delay(1, TimeUnit.SECONDS)
    .subscribeOn(Schedulers.io());
Observable<String> observable2 = Observable.just("Task2")
    .subscribeOn(Schedulers.io());

Observable.ambArray(observable1, observable2)
    .subscribe(System.out::println);
```
### `buffer`
Periodically gather items emitted by an Observable into bundles and emit these bundles rather than emitting the items one at a time.

```java
Observable.interval(100, TimeUnit.MILLISECONDS)
    .take(10)
    .buffer(3)
    .subscribe(System.out::println);
```

### `window`
Periodically subdivide items from an Observable into Observable windows and emit these windows rather than emitting the items one at a time.

```java
Observable.interval(100, TimeUnit.MILLISECONDS)
    .take(10)
    .window(3)
    .flatMapSingle(Observable::toList)
    .subscribe(System.out::println);
```

### `groupBy`
Divide an Observable into a set of Observables that each emit a different subset of items from the original Observable, organized by key.

```java
Observable.range(1, 10)
    .groupBy(i -> i % 2 == 0 ? "Even" : "Odd")
    .flatMapSingle(group -> group.toList())
    .subscribe(System.out::println);
```
### `delay`
Shift the emissions from an Observable forward in time by a particular amount.

```java
Observable.just("Task")
    .delay(1, TimeUnit.SECONDS)
    .subscribe(System.out::println);
```

## Practical Example

### Parallel Execution

```java
Observable.range(1, 10)
    .flatMap(item -> Observable.just(item)
        .subscribeOn(Schedulers.computation())
        .map(i -> i * 2))
    .subscribe(System.out::println);
```
### Concurrent and Parallel Execution
```java
Observable<Integer> observable1 = Observable.range(1, 5)
    .subscribeOn(Schedulers.io())
    .map(item -> item * 2);

Observable<Integer> observable2 = Observable.range(6, 10)
    .subscribeOn(Schedulers.io())
    .map(item -> item * 2);

Observable.merge(observable1, observable2)
    .observeOn(Schedulers.computation())
    .subscribe(System.out::println);
```

### Parallel Execution with parallel
```java
Flowable.range(1, 10)
    .parallel()
    .runOn(Schedulers.computation())
    .map(item -> item * 2)
    .sequential()
    .subscribe(System.out::println);
```
### Concurrent and Parallel Execution
```java
Observable<Integer> observable1 = Observable.range(1, 5)
    .subscribeOn(Schedulers.io())
    .map(item -> item * 2);

Observable<Integer> observable2 = Observable.range(6, 10)
    .subscribeOn(Schedulers.io())
    .map(item -> item * 2);

Observable.merge(observable1, observable2)
    .observeOn(Schedulers.computation())
    .subscribe(System.out::println);
```

#### Conclusion
- RxJava provides powerful tools for managing concurrency and parallelization, allowing developers to handle multiple tasks efficiently. By understanding and using the right operators and schedulers, you can write highly performant and responsive applications.
