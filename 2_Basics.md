1. Data types in Typescript
    - number - same as in Javascript (1, 5,2, -10)
    - string - same as in Javascript
    - boolean - same as in Javascript
    - object - enhanced version of Javascript objects
    - Arrays - enhanced version of Javascript arrays
    - Tuple - Not present in Javascript - Immutable array
    - Enums - Not present in Javascript
    - any - Not present in Javascript

2. Core primitive types in typescript are all lowercase like number, string, boolean and not Number, String and Boolean

3. Typescript has type inference means it tries to compute the datatype of variable using all the available information like
        - Here we are not defining the type of result variable but if we check the typeof result then we will find it as number
```
function add(n1: number, n2: number) {
    const result = n1 + n2;


    result = 'abc' // error
}
```

4. Setting the exact type of an object

```
    const person: {
        name: string;
        age: number;
    } = {
        name: 'Rohan',
        age: 31
    }

    console.log(person.name);

    console.log(person.nickname);   // compilation error

```

5. Arrays in typescript

```
let activities: string[] = ['Coding', 'Sports'];

activities.push('Reading');     // works fine
activities.push(123);           // error

```

6. Tuple
    - fixed array
    - let say we want a role named array to have exactly 2 values with first as a number and second as a string
    - So the syntax to mark a variable tuple becomes [number, string]
    - There is an issue with Typescript tuples that we can still push a new element
```
    const person: {
        name: string;
        age: number;
        role: [number, string];
    }= {
        name: 'Rohan',
        age: 31,
        role: [2, 'admin]

    }

    person.role[1] = 10;        // compilaation error
    person.role.push('admin')   // works but not good
    person.role = [3, 'developer']  // works

```

7. Enums

```
    enum Role { ADMIN, READ_ONLY, AUTHOR};

    OR
    enum Role { ADMIN=1, READ_ONY=10, AUTHOR=23};  // values can be of any type like numbers, string, etc

    const person: {
        name: string;
        age: number;
        role: Role;
    }= {
        name: 'Rohan',
        age: 31,
        role: Role.ADMIN

    }

```

8. Any type
    - can set any type to a variable
```
    const arr: any[] = [];

    arr.push(1);
    arr.push('test');

```

9. Union types
    - Setting more than 1 data type for a variable

```
    let a : string | number;
    a = 10;     // works
    a = 'test'  // works

```

10. Literal types
    - When we exactly know what are the possible values of a variable
    - not data types but possible values

```
    let a: 'value1' | 'value2';
```

11. Type aliases or custom types
    - If we have to use union types or literal types at several places
    - Then we can use type aliases to store them 
    - then we can use those aliases in place of union or literal types

```
    type Combinable = number | string;
    type User = { name: string; age: number };

```

12. Return type of a function
    - Typescript use type inference to calculate the return type of a function
    - void and undefined are also valid return type
    - If there is no specific reason then there is no need to add the return type on a function
    - But just for understanding the syntax looks like:

```
function add(n1: number, n2: number): number {
    return n1 + n2;
}
```

13. Function as type
    - defined the return type as function with the return type of that function

```
    function add(n1:number, n2: number) {
        return n1 + n2;
    }

    let combine: (a: number, b: number) => number = add;

    combine(8,8);       // 16

```

14. Unknown type
    - It is little more restrictive than the 'any'
    - we can assign any value to a variable of type 'unknown' just like 'any' typed variable
    - The difference is we cannot assign the 'unknown' typed variable to any other variable without the type check where as we can
      assing any type variable

```
    let a : unknown = 10;
    a = 'Max';

    let b: any = 10;
    b = 'max';

    let c: string;

    // c = a; Compilation error
    c = b;  // works

    if(typeof a === 'string') {
        c = a;          // works
    }
```


15. Never type
    - Used for function that does not return anything

```
    function print(value: string): never {
        console.log(value);
    }

```

