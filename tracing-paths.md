# Tracing Paths

Tracing is when you can point to the lines of code that were executed in the order they were executed, tracking values as you go for understanding and debugging.  These exercises ask you to refactor and log conditional statements for a dynamic trace of what happened as the code was executed.

Learn this well, your debugging & problem solving future self will thank you!

PS.  In these exercises and examples you will be dealing with some difficult expressions. Don't worry about understanding them perfectly, one of the goals for these exercises is to learn how to work with code you don't fully understand!  Don't hesitate using some trial and error to find your tracing values.

### Index
* tracings to study
    * [if else](#if-else)
    * [if else if else](#if-else-if-else)
    * [nested if else](#nested-if-else)
* tracing exercises
    * [one](#one)
    * [two](#two)
    * [three](#three)
    * [four](#four)
    * [five](#five)
    * [six](#six)
    * [seven](#seven)

---

## if else

[on pytut](http://www.pythontutor.com/live.html#code=const%20x%20%3D%20,%20y%20%3D%20%3B%20//%20test%20out%20a%20bunch%20of%20values%0A%0Aconst%20expression%20%3D%20!x%20%26%26%20y%3B%0Alet%20truthiness%20%3D%20Boolean%28expression%29%3B%0A%0Alet%20path%3B%0A%0Aif%20%28%20truthiness%20%29%20%7B%0A%20%20path%20%3D%20%22if%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22else%22%3B%0A%7D%0A%0Atruthiness%20%2B%3D%20%22y%22%3B&cumulative=false&curInstr=7&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)

__original code__
```js
{
  const x = , y = ; // test out different values

  if (!x && y) {
    // if body
  } else {
    // else body
  }

}
```

__refactored and traced__
```js
{
  const x = , y = ; // test out a bunch of values

  const expression = !x && y;
  const truthiness = Boolean(expression);

  let path;

  if ( truthiness ) {
    path = "if";
  } else {
    path = "else";
  }

  console.log("x: " + typeof x + ", " + x);
  console.log("y: " + typeof y + ", " + y);
  console.log("EXP: ", expression+", "+truthiness+"y");
  console.log("PATH: ", path);
}
```


__some tracings__
```js
x: 1, y: 1, path: "else"
x: 0, y: 1, path: "if"
x: 1, y: 0, path: "else"
x: 0, y: 0, path: "else"
x: null, y: true, path: "if"
x: NaN, y: Infinity, path: "if"
x: undefined, y: "", path: "else"
```



[TOP](#conditional-exercises)

---

## if else if else

[on pytut](http://www.pythontutor.com/live.html#code=const%20x%20%3D%20,%20y%20%3D%20%3B%20//%20test%20out%20a%20bunch%20of%20values%0A%0Aconst%20first_expression%20%3D%20x%20%7C%7C%20y%3B%0Alet%20first_truthiness%20%3D%20Boolean%28first_expression%29%3B%0A%0Aconst%20second_expression%20%3D%20x%20!%3D%20y%3B%0Alet%20second_truthiness%20%3D%20Boolean%28second_expression%29%3B%0A%0Alet%20path%3B%0A%0Aif%20%28%20first_truthiness%20%29%20%7B%0A%20%20path%20%3D%20%22first%20if%22%3B%0A%7D%20else%20if%20%28%20second_truthiness%20%29%20%7B%0A%20%20path%20%3D%20%22second%20if%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22else%22%3B%0A%7D%0A%0Afirst_truthiness%20%2B%3D%20%22y%22%3B%0Asecond_truthiness%20%2B%3D%20%22y%22%3B&cumulative=false&curInstr=11&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)

__original code__
```js
{
  const x = , y = ; // test out different values

  if (x || y) {
    // first if body
  } else if (x != y) {
    // second if body
  } else {
    // else body
  }

}
```

__refactored and traced__
```js
{
  const x = , y = ; // test out a bunch of values

  const first_expression = x || y;
  const first_truthiness = Boolean(first_expression);

  const second_expression = x != y;
  const second_truthiness = Boolean(second_expression);

  let path;

  if ( first_truthiness ) {
    path = "first if";
  } else if ( second_truthiness ) {
    path = "second if";
  } else {
    path = "else";
  }

  console.log("x: " + typeof x + ", " + x);
  console.log("y: " + typeof y + ", " + y);
  console.log("FIRST EXP: ", first_expression+", "+first_truthiness+"y");
  console.log("SECOND EXP: ", second_expression+", "+second_truthiness+"y");
  console.log("PATH: ", path);
}
```

__some tracings__
```js
x: true, y: true, path: "first if"
x: true, y: false, path: "first if"
x: false, y: true, path: "first if"
x: false, y: false, path: "else"
x: null, y: undefined, path: "else"
x: NaN, y: undefined, path: "second if"
x: NaN, y: null, path: "second if"
```


[TOP](#conditional-exercises)

---


## nested if else

[on pytut](http://www.pythontutor.com/live.html#code=const%20x%20%3D%20,%20y%20%3D%20%3B%20//%20test%20out%20a%20bunch%20of%20values%0A%0Aconst%20first_expression%20%3D%20!x%20%26%26%20y%3B%0Alet%20first_truthiness%20%3D%20Boolean%28first_expression%29%3B%0A%0Aconst%20second_expression%20%3D%20!!y%20%7C%7C%20%2Bx%3B%0Alet%20second_truthiness%20%3D%20Boolean%28second_expression%29%3B%0A%0Aconst%20third_expression%20%3D%20x%20-%20y%20%7C%7C%20y%20-%20x%3B%0Alet%20third_truthiness%20%3D%20Boolean%28third_expression%29%3B%0A%0Alet%20path%3B%0A%0Aif%20%28%20first_truthiness%20%29%20%7B%0A%20%20if%20%28%20second_truthiness%20%29%20%7B%0A%20%20%20%20path%20%3D%20%22if%20if%22%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20path%20%3D%20%22if%20else%22%3B%0A%20%20%7D%0A%7D%20else%20%7B%0A%20%20if%20%28%20third_truthiness%20%29%20%7B%0A%20%20%20%20path%20%3D%20%22else%20if%22%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20path%20%3D%20%22else%20else%22%3B%0A%20%20%7D%0A%7D%0A%0Afirst_truthiness%20%2B%3D%20%22y%22%3B%0Asecond_truthiness%20%2B%3D%20%22y%22%3B%0Athird_truthiness%20%2B%3D%20%22y%22%3B&cumulative=false&curInstr=1&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)

__original code__
```js
{
  const x = , y = ; // test out different values

  if (!x && y) {
    if (!!y || +x) {
      // if if body
    } else {
      // if else body
    }
  } else {
    if (x - y || y - x) {
      // else if body
    } else {
      // else else body
    }
  }

}
```

__refactored and traced__
```js
{
  const x = , y = ; // test out a bunch of values

  const first_expression = !x && y;
  const first_truthiness = Boolean(first_expression);

  const second_expression = !!y || +x;
  const second_truthiness = Boolean(second_expression);

  const third_expression = x - y || y - x;
  const third_truthiness = Boolean(third_expression);

  let path;

  if ( first_truthiness ) {
    if ( second_truthiness ) {
      path = "if if";
    } else {
      path = "if else";
    }
  } else {
    if ( third_truthiness ) {
      path = "else if";
    } else {
      path = "else else";
    }
  }

  console.log("x: " + typeof x + ", " + x);
  console.log("y: " + typeof y + ", " + y);
  console.log("FIRST EXP: ", first_expression+", "+first_truthiness+"y");
  console.log("SECOND EXP: ", second_expression+", "+second_truthiness+"y");
  console.log("THIRD EXP: ", third_expression+", "+third_truthiness+"y");
  console.log("PATH: ", path);
}
```


__some tracings__
```js
x: null, y: null, path: "else else"
x: false, y: null, path: "else else"
x: false, y: true, path: "if if"
x: NaN, y: 1, path: "if if"
x: Infinity, y: "", path: "else if"
x: 1, y: "", path: "else if"
// I think "if else" is unreachable!
```



[TOP](#conditional-exercises)

---
---

## One

[on pytut]()

__original code__
```js
{
  const x = ; // try a bunch of values!

  if (x === +x || x === !x) {

  } else {

  }

}
```

__refactored and traced__
```js
{

}
```

__some tracings__
```js
// find 6+ tracing values
// try to find at least 1 for each path
// or can you? some paths are unreachable!
```


[TOP](#tracing-paths)

---

## Two

[TOP](#tracing-paths)

---

## Three

[TOP](#tracing-paths)

---

## Four

[TOP](#tracing-paths)

---

## Five

[TOP](#tracing-paths)

---

## Six

[TOP](#tracing-paths)

---

## Seven

[TOP](#tracing-paths)




___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
