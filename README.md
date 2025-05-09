//What are some differences between interfaces and types in TypeScript?

As new learner im facing the same confusion about interfaces and types in typescript. In TypeScript, both interface and type are used to define the structure of objects, but they differ in flexibility and usage.

First differnce i found is Interfaces support declaration merging, which means that you can define multiple interfaces with the same name, and TypeScript will merge them into a single interface with the combined properties and methods.

Example code :
interface T {
a: string;
}
interface T {
b: string;
}
const J: T= {
a: 'xx',
b: 'yy',
};

here we can see that we can change or merge value with same name inteface

On the other hand, types do not support declaration merging. This can be helpful when you want to add extra functionality or customize existing types without modifying the original definitions or patching missing or incorrect types.

Second difference is both types and interfaces can extend other types/interfaces, but the syntax is different. With interfaces, you use the extends keyword to inherit properties and methods from other interfaces. However, an interface cannot extend a complex type like a union type.

Example code :
interface T {
a: string;
b: number;
}
interface J extends T{
i: string;
}
const car: J = {
a: 'x',
b: 123,
i: 'y',
};

Another major difference is Types are more flexible when it comes to defining Union and Intersection Types. With the type keyword, you can easily create union types using the "|" operator and intersection types using the "&" operator. While interfaces can also represent union types indirectly, they don’t have built-in support for intersection types.

Exmaple with type:

type Department = 'dep-x' | 'dep-y'; // Union

type Person = {
name: string;
age: number;
};

type Employee = {
id: number;
department: Department;
};

type EmployeeInfo = Person & Employee; // Intersection

Example with interfeace :

    interface A {
    x: 'x';

}
interface B {
y: 'y';
}

type C = A | B; // Union of interfaces

these all the major difference of type and intercace , but wihout these there are also have some differeces.

/////What is the use of enums in TypeScript? Provide an example of a numeric and string enum.

Enums (short for enumerations) are one of the few features TypeScript has which is not a type-level extension of JavaScript.Enums allow a developer to define a set of named constants. Using enums can make it easier to document intent, or create a set of distinct cases. TypeScript provides both numeric and string-based enums. Enums improve code readability and help reduce errors from using magic strings or arbitrary numbers.It is defined using enum keyword.

Typescript has three types of enums:

Numeric Enums
String Enums
Heterogeneous Enums

Numeric Enums :
enum Numeric {
First,
Second,
Third,
Fourth
}
console.log(Numeric.Second); // 1

A numeric enum's first member is not initialized then it starts from 0 and Second becomes 1.

String Enums:
enum StringEnum {
A = "a",
B = "b",
C = "c",
D = "d",
}

Heterogeneous Enums --> Mix of numeric and string enums.

enum HeterogeneousEnum {
No = 0,
Yes = 'YES'
}
