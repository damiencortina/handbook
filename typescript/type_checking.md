# TS : Narrowing
🥐 "rétrécissement" 🥐

**narrowing** : process of refining types to more specific types than declared.

add details/exemple of possible error if no narrowing is done

In many editors we can observe these types as they change

There are a couple of different constructs TypeScript understands for narrowing.

## 1. Type guard
 🥐"garde de type"🥐

**type guard** : Within our if check, TypeScript sees `typeof padding === "number"` and understands that as a special form of code

`typeof` might return the following values :

- `"string"`
- `"number"`
- `"bigint"`
- `"boolean"`
- `"symbol"`
- `"undefined"`
- `"object"`
- `"function"`

**important :**

- `typeof array` is object
- In JavaScript, `typeof null` is actually `"object"`, to filter this out we might need truthiness narrowing

## Truthiness narrowing

To exclure null, we might use :

```
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

```javascript
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

## Equality narrowing

TypeScript also uses switch statements and equality checks like ===, !==, ==, and != to narrow types.

### Checking by comparing variables

```javascript
function example(x: string | number, y: string | boolean) {
  if (x === y) { // if x === y, they both are strings, since its their only common type
    // do stuff
  }
}
```

### Checking by comparing litteral values

```javascript
function printAll(strs: string | string[] | null) {
  if (strs !== null) { // returns false if strs value is null ("" and [] are in)
  }
  // This is not the same than the following
  if (strs) { // returns false if strs coerce to false ("" and [] are out)
  }
}
```

### Use looser checks to remove both `null` and `undefined`

**looser checks :** == and !=

```javascript
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

> Written with [StackEdit](https://stackedit.io/).
