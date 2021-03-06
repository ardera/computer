# Computer

Computer is a lightweight library for concurrent computations, which provides Flutter's compute() like API.

## Features

- Easy to use API
- No overhead for creating & releasing isolates for each task. Workers initialized on start and ready to solve your tasks
- Strictly defined count of workers

## Update

Computer is no longer a singleton. If you still need a singleton solution, you can make it on your own like in example

<!--
TODO:

- Add a singleton example
-->

## How to use

Computer provides just 3 methods

### turnOn()

```dart
final computer = Computer();

await computer.turnOn(
  workersCount: 4, // optional, default 2
  areLogsEnabled: false, // optional, default false
);
```

Before using the `Computer` you need to `turnOn` it. This will create workers and initialize them. Then you may use `compute()` method.

### compute()

```dart
var answer = await computer.compute(
  fib,
  param: 45, // optional
);
```

`compute` will execute your function inside one of the workers. Function may be `async`

### turnOff()

```dart
await computer.turnOff();
```

If you don't need workers anymore, you should `turnOff` the Computer. It will destroy workers.
