# 内置类型

> 文档： <https://www.typescriptlang.org/docs/handbook/utility-types.html>

```ts
// 所有例子以这个为模板
interface UserProps {
  name: string;
  age: number;
}
```

## Pick

> Pick<Type, Keys>  
> 取 keys 值

```ts
type NewProp = Pick<UserProps, "name | age">;
// {
//  name: string;
//  age: number;
// }
```

## Omit

> Omit<Type, Keys>  
> 排除 keys 以外的值

```ts
type NewProps = Omit<UserProps, "name">;
// {
//   age: number;
// }
```

## Readonly

```ts
const user: Readonly<UserProps> = {
  name: 'name',
  age: 10,
}

// 无法分配到 "name" ，因为它是只读属性。
// user.name = 'name2'
```

## ReadonlyArray

```ts
const foo: number[] = [1, 2, 3, 4]
const bar = ReadonlyArray<number> = foo

// bar[0] = 10 // error!
// bar.push(10) // error!
// bar.length = 3 // error!
```

## Required

```ts
interface UserProps {
  name: string
  age?: number
}
const user: Required<UserProps> = {
  name: 'haha',
  age: 100,
}
```

## Record

> Record<Keys, Type>  
> 将一个类型属性映射到另一个类型时

```ts
interface User {
  name: string
}
const users: Record<string, User> = {
  info: {
    name: 'haha',
  },
  info2: {
    name: 'haha2',
  },
}
```

## Partial

```ts
const user: Partial<UserProps> = {
  name: 'haha',
}
```

## ReturnType

> ReturnType 取函数返回值类型

```ts
function func() {
  return {
    a: 1,
    b: 'haha',
  }
}
// type typeA = ReturnType<() => number> // number
// type typeB = ReturnType<typeof func>
// {
//   a: number
//   b: string
// }
```

## Parameters

> 取函数的参数类型

```ts
type TypeA = Parameters<(options: { a: string }) => any>
// [options: { a: string }]
```

## Extract

> 取交集

```ts
type Width = string | number
type WidthType = Extract<Width, string>
// string
```

## Exclude

> 取差集

```ts
type Width = string | number
type WidthType = Exclude<Width, string>
// number
```

## as const

> 不可修改

```ts
const foo = { bar: 'baz' } as const
foo.bar = 123 // Error!
```

## keyof

> 获取接口的 key 的联合类型

```ts
type keys = keyof UserProps
// 'name' | 'nickname' | 'age'
```

## extends

> 类型约束

```ts
interface length {
  length: number
}
function identity<T extends length>(arg: T): T {
  console.log(arg.length)
  return arg
}
```

## 条件类型

> U ? X : Y

```ts
type Extract<T, U> = T extends U ? T : never
```

## in

> 类型映射

```ts
type Readonly<T> = {
  readonly [P in keyof T]: T[p]
}
```
