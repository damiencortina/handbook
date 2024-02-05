# TS : Narrowing
🥐 "rétrécissement" 🥐

**narrowing** : process of refining types to more specific types than declared.

add details/exemple of possible error if no narrowing is done

In many editors we can observe these types as they change

There are a couple of different constructs TypeScript understands for narrowing.

**type guard** : Within our if check, TypeScript sees `typeof padding === "number"` and understands that as a special form of code.
 🥐"garde de type"🥐

## 1. `typeof` narrowing

`typeof` might return the following values :

- `"string"`
- `"number"`
- `"bigint"`
- `"boolean"`
- `"symbol"`
- `"undefined"`
- `"object"`
- `"function"`

```typescript
function  printAll(strs: string | number | null) {
	if (typeof  strs === "string") {
		// strs is a string
	} else if (typeof  strs === "string") {
		// strs is a number
	} else {
		// strs is null
	}
```

**important :**

- `typeof array` is `"object"`
- `typeof null` is `"object"`

## Truthiness narrowing

To exclude null, we might use :

```typescript
if (strs && typeof strs === "object") {
```

In JavaScript, constructs like `if` first “coerce” their conditions to booleans to make sense of them.

The following values coerce to false, while everything else coerce to true :

- `0`
- `NaN`
- `""` (the empty string)
- `0n` (the bigint version of zero)
- `null`
- `undefined`

**important :** You can always coerce values to booleans by running them through the Boolean function, or by using the shorter double-Boolean negation. (The latter has the advantage that TypeScript infers a narrow literal boolean type true, while inferring the first as type boolean.)

**warning :** Truthiness checking on primitives can be error prone

```typescript
function  printAll(strs: string | string[] | null) {
    if (strs) { // this is filtering out "" and [], whose types are corrects, but coerce to false...
        if (typeof  strs === "object") {
            // do stuff
        } else  if (typeof  strs === "string") {
            // do other stuff
        }
    }
}
```

This case can be treated with equality narrowing.

## `===`, `!==`, `==`, and `!=` narrowing

### Checking by comparing variables

```typescript
function example(x: string | number, y: string | boolean) {
  if (x === y) { // if x === y, they both are strings, since its their only common type
    // do stuff
  }
}
```

### Checking by comparing litteral values

```typescript
function printAll(strs: string | string[] | null) {
  if (strs !== null) { // returns false if strs value is null ("" and [] are in)
  }
  // This is not the same than the following
  if (strs) { // returns false if strs coerce to false ("" and [] are out)
  }
}
```

### Use looser checks ( `==` and `!=` ) to remove both `null` and `undefined`

```typescript
interface Container {
  value: number | null | undefined;
}

function multiplyValue(container: Container, factor: number) {
  // Remove both 'null' and 'undefined' from the type.
  if (container.value != null) {
  // do stuff
  }
}
```

## `in` narrowing

```typescript
type  Fish = { swim: () =>  void };
type  Bird = { fly: () =>  void };
type  Human = { swim?: () =>  void; fly?: () =>  void };

function  move(animal: Fish | Bird | Human) {
	// Optionnal properties exists on both sides
	if ("swim"  in  animal) {
		// animal is Fish | Human since :
		//   - Fish has a swim method
		//   - Human might have a swim method
	} else {
		// animal is Bird | Human since :
		//   - Bird has no method named swim
		//   - Human might not have a swim method
	}
}
```

## `instanceof` narrowing

```typescript
function  logValue(x: Date | string) {
	// This works well with values that can be constructed with new
	if (x  instanceof  Date) {
		// x is a Date
	} else {
		// x is a string
	}
}
```

## Assignment narrowing

```typescript
let  x = Math.random() < 0.5 ? 10 : "hello world!";
// x is string | number
x = 1;
// x is number
x = "goodbye!";
// x is string (it's valid even if it was previously a number since x was DECLARED as being string | number
```

> Written with [StackEdit](https://stackedit.io/).
