# Metatable Type Syntax

## Summary

Add unique syntax to allow for specifying the metatable of a type.

## Motivation

There is currently no expression for metatables within the type system, with the exception of hacks using `keyof`. That isn't great, because metatables are a commonly required feature for things like object-oriented programming. `typeof` is boilerplate which can likely be eliminated by allowing the expression of metatables through special syntax.

## Design

Introduce a context-sensitive `metatable` keyword which specifies that a table has a metatable.

```lua
local class = {}
type Identity = {
	field: string,

	metatable typeof(class)
}
```

## Alternatives

`type T = { metatable {} }` could be too similar to field syntax. An argument could be made that `type T = { metatable: {} }` is too similar to metatable syntax. We could change the keyword to be `@metatable`, similar to how it is currently expressed as when converting a type to a string. However, this introduces a sigil, which increases cognitive load and harms readability.

## Drawbacks

Unique syntax always has the downside of an additional learning curve to the language. Context-sensitive keywords &sigils increase cognitive load when trying to read Luau, which isn't great.
