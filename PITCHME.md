# Functional Programming

C++ and Javascript

---

## Functional Programming

- more emphasis on the *evaluation of expressions*
- a fixed set of things, but constantly adding more *operation* on things

---

## Functional Programming

Building blocks are functions, not objects.

- discourage procedures and commands to complete a task
- only need to define the needed result

---

## Example

To compute the sum of an integer list.

### Imperative Programming

A set of instructions

- a global variable SUM = 0
- iterate the list
  - add the value to SUM
- return SUM

---

### Declarative Programming

A definition of the result

- define the sum as the value of the first element plus the remaining integers in the list

---

### Recursion

```C++
  #include <vector>

  int func(std::vector<int>::iterator begin, std::vector<int>::iterator end, int sum)
  {
    if (begin != end)
    {
      sum += *begin;
      return func(++begin, end, sum);
    }
    return sum;
  }

  int main()
  {
    std::vector<int> myArray = {1, 2, 3, 4};
    int sum = func(myArray.begin(), myArray.end(), 0);
  }

```

---

### Object Oriented Programming

> polymorphism on *objects*

---

### Functional Programming

> polymorphism on *behavior*

---

### Javascript

```Javascript
  const myArray = [1, 2, 3, 4];
  let func = (accumulator, currentValue) => {
    return accumulator + currentValue;
  };
  let sum = myArray.reduce(func);
```

> The ```reduce()``` method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

---

### C++

```C++
  #include <vector>
  #include <algorithm>

  int main()
  {
  	std::vector<int> myArray = {1, 2, 3, 4};
  	auto func = [](int accumulator, int currentValue)
  	{
  		return accumulator + currentValue;
  	};
  	int sum = accumulate(myArray.begin(), myArray.end(), 0, func);
  }
```

---

### C++

```C++
  #include <vector>
  #include <algorithm>

  int main()
  {
  	std::vector<bool> myArray = {false, false, true, true};
  	auto func = [](bool accumulator, bool currentValue)
  	{
  		return accumulator ^ currentValue;
  	};
  	bool result = accumulate(myArray.begin(), myArray.end(), true, func);
    // result is true
  }
```

---

### C++

```C++
  #include <vector>
  #include <algorithm>

  int main()
  {
      std::vector<bool> myArray = {false, false, true, true};
      bool sum = accumulate(myArray.begin(), myArray.end(), true, [](bool accumulator, bool currentValue){
          return accumulator ^ currentValue;
      });
  }
```

---

## Requirements of Functional Programming

- stateless
- ability to create *pure functions*
- passing a *function* as parameter
- returning a *function* as result
- support *nested* functions

---

## Pure Functions

- return value only determined by its inputs
- no *side effects*

> side effects include
> - asking for inputs
> - network requests
> - writing to hard disks

---

## Declarative Programming

To just declare a function and invoke it.

```Javascript
  (function baz() {
    alert("hello world")
  })();
```

---

## Nested Functions

To declare functions inside another function.

```Javascript
  (function() {
      function baz() {
        alert("hello world")
      }
      return baz();
  })();
```

---

## Higher Order Function

To return a function as result.

```Javascript
  (function() {
      function baz() {
        alert("hello world")
      }
      return baz;
  })()();
```

> ```Javascript
  (function() {
      function baz() {
        alert("hello world")
      }
      return baz();
  })();
> ```

---

## C++11

```
  //Syntax
  [ captures ] ( params ) { body }
```

```C++
  #include <functional>

  int main()
  {
    std::function<void()> myFunc = []()
    {
      std::cout << "Hello World";
    };
    myFunc();
  }
```

---

### auto Keyword

```
  //Syntax
  [ captures ] ( params ) { body }
```

```C++
int main()
{
  auto myFunc = []()
  {
    std::cout << "Hello World";
  };
  myFunc();
}
```

---

### Capture

```
  [ captures ] ( params ) { body }
```

capture default | behavior
--- | ---
& | capture by reference
= | capture by copy

```C++
  int main()
  {
    int x = 123;
    [&](){x;}; // by reference
    [=](){x;}; // by copy
  }
```

---

### Javascript ES6

```Javascript
  let foo = function() {
    alert('hello world');
  };
```

### Lambda Expressions

```Javascript
  let foo = () => {
    alert('hello world');
  };
```

---

### Advantages

Why do we use Functional Programming?

- concise coding
  - no more iterator variables
  - no more states
- huge step to "bug-less" programming
  - no side effects
  - same inputs results in same outputs, always
- order of execution is not important
  - threading

---

### When to Functional Programming

- math
- algorithms
- anything without side effects

> C++ and Javascript

> Getting the best from both worlds
