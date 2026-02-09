# Destructuring

It is an ESX feature that allows us to unpack values from an array or an object into separate variables in one step.

### Destructuring Arrays

###### Traditional Method
```js
const arr = [1, 2, 3];
const a = arr[0];
const b = arr[1];
const c = arr[2];
```

###### Destructuring Method
```js
const arr = [1, 2, 3];
const [a, b, c] = arr; // 1 2 3

// We don't have to take all of the elements
const [x, y] = arr; // 1 2

// We can skip elements using empty commas
const [xx, , yy] = arr; // 1 3

// We can set default values
const [aa=10, bb=10, cc=10, dd=10] = arr; // 1 2 3 10
```

```js
// Destructuring Nested Arrays
const arr = [1, 2, [3, 4]];

const [a, b, [c, d]] = arr; // 1, 2, 3, 4
const [x, y, z] = arr;      // 1, 2, [3, 4] 
```

**Note:** Default values are useful when we are destructuring an array without knowing its length especially when the array is shorter than the variables number.

#### Applications
1. Switching variables.
```js
const a = 1;
const b = 2;

// Normal Way
const temp = a;
a = b;
b = temp;

// With Destructuring
[b, a] = [a, b];
```

2. Return multiple values from a function by returning an array and destruct it.
```js
function weekends() {
    return ["Friday", "Saturday"];
}
const [firstDay, secondDay] = weekends();
```

-----------------------------------
### Destructuring Objects
- We use `{}` to destruct objects, not `[]` like arrays.
- The variable names must exactly match the property names that we want to retrieve.
- If we want to set different variable names.
- We can set default values.
- We can take what we want with any order.
- If we didn't set a default value, it will return `undefined`.
 
```js
const person = {
    name: "John",
    age: 30,
    city: "New York"
    family: ["mama", "baba"]
};

// variable names exactly match property names
const {name, age, family} = person;

// use different variable names
const {name: a, age: b} = person;

// set default values
const {name: c, family: c = []} = person;
```

```js
// Destructuring Nested Objects
const person = {
    name: "John",
    age: 30,
    city: "New York",
    family: {
        mama: "mama",
        baba: "baba"
    }
};

const {name, family: {mama: mom, baba: dad}} = person;
```

Note: If we already defined variables and tried to destruct an object to them, Javascript gives a syntax error, so we must surround them in parantheses.
```js
let a = 1;
let b = 2;

({a, b} = {a: 1, b: 2});
```


We can pass an object to a function and destruct it inside the function instead of receiving many parameters. The order of passing parameters doesn't have to be the order of the object properties.
```js
function person({name, age}) {
    console.log(name, age);
}

person({name: "John", age: 30});
```
```js
function person(obj) {
    console.log(obj);
}

person({name: "John", age: 30});
```
