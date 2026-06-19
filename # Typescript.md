# Typescript


### Accessing Type vs Accessing Value

Depending on the context, [''] will return either the value or the type. This is a bit confusing, same syntax returns 2 different things depending on context.


```typescript
// Runtime — gets the VALUE
const val = props['addTagCallback']; 

// Type level — gets the TYPE
type T = IOrdersVehicleDataFileGetConstructProps['addTagCallback'];
```

### Destructuring Assignment
Extracts the value on props.rolloutConfigTable and assigns it to the rolloutConfigTable constant.

```typescript
const { rolloutConfigTable } = props;
```

### Reduce
Applies a function block to each array index and keeps an accumulator object that is passed to the next index. Reduce and spread operator work really well together, because you can spread the accumulated value to add fields to the object.

```typescript
...items.reduce(
    (accumulator, currentValue, index) => ({
        ...accumulator,
        ...generateEntry(index + 1, currentValue.code, currentValue.value)
    }),
    {},
),
```

### Spread statement

The spread statement '...varName' returns all existing key-value fields into a new object.

```typescript
const myConst = {
    propA: valueA,
    propB: valueB
}

const mySpreadConst = {
	...myConst,
	propC: valueC
}

// The mySpreadConst will have the fields from myConst plus the propC field
{
    propA: valueA,
    propB: valueB,
    propC: valueC
}
```

### Computed Property Name
Tells javascript to not use the literal string, but to evaluate the var and use its value as property name.

```typescript
{ [keyName]: value }
```

### Arrow function: Implicit return vs Block body

```typescript
//Arrow function with Implicit return. Return an object or statement directly
(input) => ({ key: val })
(input) => input * 2

// Arrow function with Block body. Must explicitly return something
(input) => { 
    ...other logic...
    return { key: val }; 
}
```

### JSON.parse()

JSON.parse() returns "any". 

In typescript:
-   'any' can be assigned to a var of any type without checking
-   Any type can be assigned to a var of type 'any' without checking

So, when you do this:

```typescript
const x: number = JSON.parse('"hello"'); // no error at compile/run time
```

It doesn't give any error, because the code is converted to JS which is weakly typed. It gets compiled to this:
```typescript
const x = JSON.parse('"hello"');
```

The var continues to hold whatever valued was return by JSON.parser(), the actual error happens when you try to use the string as a number.

### Shorthand property assignment

When the property name and the variable name are the same, you can assign the value directly, omitting the colon and value.

```typescript
interface IMyInterface {
    propA: string;
}

const propA = "valueA";

// so this
const myObject: IMyInterface = { propA };

// is equivalent to this
const myObject: IMyInterface = { propA: propA };

```
