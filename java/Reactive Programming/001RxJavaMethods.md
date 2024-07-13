# RxJava Methods Examples

## 1. Creating Observables

  - ### `just`
  Creates an Observable that emits a specified item.
  
  ```java
  Observable<String> observable = Observable.just("Hello, world!");
  ```
  
  
  - ### `fromArray`
  Converts an array to an Observable that emits each item.
  
  ```
  String[] words = {"Hello", "world"};
  Observable<String> observable = Observable.fromArray(words);
  
  ```
  
  - ### `create`
  Creates an Observable from scratch by means of a function.
  
  ```
  Observable<String> observable = Observable.create(emitter -> {
      emitter.onNext("Hello");
      emitter.onNext("World");
      emitter.onComplete();
  });
  
  ```

## 2. Transforming Observables
![image](https://github.com/user-attachments/assets/cf4620de-23e9-49b2-8441-ef93546c8002)


- ### `map`
Transforms the items emitted by an Observable by applying a function to each item.

![image](https://github.com/user-attachments/assets/78bc388a-3a53-45f1-bb89-e7c8c357e222)


```
Observable<Integer> observable = Observable.just(1, 2, 3);
observable.map(item -> item * 2)
          .subscribe(System.out::println);
```

- ### `flatMap`
Transforms the items emitted by an Observable into Observables, then flattens these Observables into a single Observable.

```
Observable<Integer> observable = Observable.just(1, 2, 3);
observable.flatMap(item -> Observable.just(item * 2))
          .subscribe(System.out::println);
```


## 3. Filtering Observables
![image](https://github.com/user-attachments/assets/67bfd13d-e95f-446f-a05d-30f3fcd5bdd8)

- ### `filter`
Emit only those items from an Observable that pass a predicate test.

```
Observable<Integer> observable = Observable.just(1, 2, 3, 4, 5);
observable.filter(item -> item % 2 == 0)
          .subscribe(System.out::println);
```

- ### `distinct`
Suppress duplicate items emitted by an Observable.

```
Observable<Integer> observable = Observable.just(1, 2, 2, 3, 3, 3);
observable.distinct()
          .subscribe(System.out::println);
```

## Reducing Operators  
![image](https://github.com/user-attachments/assets/8e67fb19-a908-42c8-ad0c-2fa4e7ddc94f)

![image](https://github.com/user-attachments/assets/8976a7dd-3592-4955-8896-e4561f52b1ff)

![image](https://github.com/user-attachments/assets/28b12952-c3e7-45ec-94e5-43f324325ea4)

![image](https://github.com/user-attachments/assets/db4aff9f-2ffe-479d-8b8b-e9b3b07a8026)



## 4. Combining Observables
- ### `merge`
Combine multiple Observables into one by merging their emissions.

```
Observable<String> observable1 = Observable.just("Hello");
Observable<String> observable2 = Observable.just("World");
Observable.merge(observable1, observable2)
          .subscribe(System.out::println);
```
- ### `zip`
Combine multiple Observables into one by combining their emissions with a specified function.

```
Observable<String> observable1 = Observable.just("Hello");
Observable<String> observable2 = Observable.just("World");
Observable.zip(observable1, observable2, (item1, item2) -> item1 + " " + item2)
          .subscribe(System.out::println);
```

## 5. Error Handling
- ### `onErrorReturn`
Instruct an Observable to emit a particular item when it encounters an error.

```
Observable<Integer> observable = Observable.just(1, 2, 0, 4)
    .map(item -> 10 / item)
    .onErrorReturn(error -> -1);
observable.subscribe(System.out::println);
```

- ### `retry`
If an Observable encounters an error, resubscribe to it in the hopes that it will complete without error.

```
Observable<Integer> observable = Observable.just(1, 2, 0, 4)
    .map(item -> 10 / item)
    .retry(3);
observable.subscribe(System.out::println, Throwable::printStackTrace);
```

## 6. Utility Operators
- ### `delay`
Shift the emissions from an Observable forward in time by a particular amount.

```
Observable<String> observable = Observable.just("Hello, world!");
observable.delay(1, TimeUnit.SECONDS)
          .subscribe(System.out::println);
```

- ### `doOnNext`
Register an action to take upon observing each emitted item.

```
Observable<Integer> observable = Observable.just(1, 2, 3);
observable.doOnNext(item -> System.out.println("Processing item: " + item))
          .subscribe(System.out::println);
```

## 7. Observing on Different Schedulers


- ### `subscribeOn`
Specify the Scheduler on which an Observable should operate.

```
Observable<String> observable = Observable.just("Hello, world!");
observable.subscribeOn(Schedulers.io())
          .subscribe(System.out::println);
```

- ### `observeOn`
Specify the Scheduler on which an Observer should observe the Observable.

```
Observable<String> observable = Observable.just("Hello, world!");
observable.observeOn(Schedulers.newThread())
          .subscribe(System.out::println);
```
