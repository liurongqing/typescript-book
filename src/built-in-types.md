# 内置类型

```typescript
// 所有例子以这个为模板
interface UserProps {
  name: string;
  age: number;
}
```

## Pick

> Pick<Type, Keys> 取 keys 值

```ts
type NewProp = Pick<UserProps, 'name | age'
// {
//  name: string;
//  age: number;
// }
```

## Omit

## Readonly

## ReadonlyArray

## Required

## Record

## Partial

## ReturnType

## Parameters

## Extract

## Exclude

## as const

## keyof

## extends

## 条件类型

## in
