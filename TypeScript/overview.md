TypeScript adds syntax on top of JavaScript.

## how to run typescript

1. we need to install compiler with npm
   `npm install typescript --save-dev`
   `npx tsc`
2. we can handle compiler by tsconfig.json

`npx tsc --init`

3. any = disables type check

4. `unknown`
   check the types before using it.
   when we don't know the type of data being typed.
   We use it when we get data from API --> we can check it first.

```ts
async function fetchData(): Promise<unknown> {
  const res = await fetch("https://api.example/data");
  return res.json();
}

async function processData() {
  const data: unknown = await fetchData();
  if (Array.isArray(data)) {
    // action with array type
  } else if (typeof data === "object" && data !== null) {
    // handle with object
  } else {
    // other type
  }
}

function printValue(value: unknown) {
  if (typeof value === "string") {
    console.log("string");
  } else if (typeof value === "number") {
    console.log("number");
  } else {
    console.log("other type");
  }
}
```

5. null: already declared but not assign value. undefined: haven't declared yet.
6. Array: we need to declare the type of elements in array: for examples

```ts
let names: string[] = []; //only string can be pushed
// we cannot push other type like: numbers, null
```

readonly

```ts
let names: readonly string[] = ["Jane"];
// we cannot modify the value of array
```

7. Tuples

```ts
// we declare elements of an array in order
// we are free to add more item after the first 3 items declared
let ourTuple: [number, boolean, string];
ourTuple = [5, false, "hello"];
```

Same with array, we have readonly

```ts
const ourReadonlyTuple: readonly [number, boolean, string] = [5, true, "hello"];
// we cannot add more item into the array. It will be error.
```

Destructuring same like array

7. Object:
   we need to declare each property of an object:

```ts
const car: {type:string, model:string,year:number}={
  type:"honda",
  model: 'Civic'
  year: 2020
}
```

In the case, we can add more properties into the object by **Index Signatures**

```ts
const nameAgeMap: { [index: string]: number } = {};
// in this example: we will have index type string and value is number

nameAgeMap.Jack = 25;
nameAgeMap.Mark = "hello"; // ==> error
```

8. Enums:
   group of constant variables
   we can also init the default values.

9. aliases: **type**
   we just create the type first then assign it into object or type.

10. interface:

```ts
interface Rectangle {
  height: number;
  width: number;
}
```

11. the different between enum and interface:

format constant for variables while interface is structure of objects, function
cannot modify(extend) while extend
