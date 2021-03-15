# Automatically determining return Type of a callback function

Use `typeof` and `ReturnType<>`:

```
let callback: typeof ClassUnderTest.someCallback;
let x: ReturnType<typeof ClassUnderTest.someCallback>;
beforeEach(() => {
  callback = objectOfClassUnderTest.someCallback;
  x = objectOfClassUnderTest.someCallback();
})
```

# Creating interface for optional parameters in a function using Partial<>

```
inteface OptInterface {
  val: number;
  predicate: () => boolean;
  getter: () => Somestuff?;
}

function create(
  {val = 200, predicate = () => false, getter = () => undefined}
  : Partial<OptInterface>) {
  //...
}
