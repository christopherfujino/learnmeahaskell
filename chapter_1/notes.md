---
title: haskell
date: 2018-10-27
tags: haskell,programming
layout: post
---

## Haskell Is...

1. Lazy loaded, functions aren't evaluated until the results are required
1. Variables are statically typed
1. Uses type inference (e.g. `a = 1 + 2`)
1. Because it uses high-level concepts, Haskell programs tend to be shorter
than their imperative counterparts

## Setup

1. GHC - Glasgow Haskell Compiler
1. Stack
1. ghc-mod hlint hdevtools hfmt

## Numbers

1. Integers and floats can be implicitly cast to one another.

## Functions

1. `*` is an *infix* function, in that it appears between its two arguments
1. Most functions are *prefix*, in that they appear before their arguments
1. Prefix functions can be called as infix by surrounding them in backticks
1. Functions don't have to declared before invocation
1. Functions that take no parameters are called *definitions*, since they
always return the same value

## Lists
1. Strings are lists of characters; `"Hello"` is syntactic sugar for
`['H','e','l','l','o']`
1. `++` concatenates two lists; e.g. `[1,2] ++ [3] -- [1,2,3]`
1. `:` prepends a value to a list; e.g. `1:[2,3] -- [1,2,3]`
1. `[1,2,3]` is synctatic sugar for `1:2:3:[]`
1. To access a list element by index, use `!!`; e.g. `"Abc" !! 1 -- 'b'`
1. Accessing a list index out of bounds throws an exception; e.g.
`[0,1] !! 2 -- Error!`
1. Lists can be nested, but must list elements in a parent list must all be
of the same type.
1. `head` takes in a list and returns its first element; e.g.
`head [1,2] -- 1`. Will throw an exception if passed in an empty list.
1. `tail` returns everything in the last after the head; e.g.
`tail [1,2] -- [2]`
1. `last` returns the last element of input list
1. `init` returns everything except the last element of a list
1. `length` returns the length of a list
1. `null` tests if a list is empty
1. `reverse` reverses the elements in a list
1. `take` takes a number `n` and a list and returns a new list with the first
`n` elements from the input list.
1. `drop` takes a number `n` and a list and returns a copy of the list sans
the first `n` elements.
1. `elem` takes a value and a list and tests if the value appears in the list

## Ranges

1. `[1..5]` is the equivalent of `[1,2,3,4,5]`
1. Also works with characters: `['a'..'e'] == "abcde"`
1. Or steps: `[2,4..10] == [2,4,6,8,10]`, or `[10,9..1]`
1. Or an infinite list: `take 5 [1..] == [1,2,3,4,5]`
1. `cycle` takes a list and repeats it indefinitely; e.g.
`take 8 (cycle "LOL ")`
1. `repeat` take a value and produces an infinite list of that element

## List Comprehension

For the list comprehension `[x*2 | x <- [1..10]]`:

1. `[1..10]` is the input list
1. `x` is our variable, to which elements from the input list are bound
1. `x*2` is the output function

A more complex comprehension ``[x*2 | x <- [50..100], x `mod` 7 == 3]``:

1. ``x `mod` 7 == 3`` is a predicate, or filter

Even more complex

```Haskell
let xxs = [[1,3,5,2,3,1,2,4,5],[1,2,3,4,5,6,7,8,9],[1,2,4,2,1,6,3,1,3,2,3,6]]
[ [ x | x <- xs, even x ] | xs <- xxs ]
-- [[2,2,4],[2,4,6,8],[2,4,2,6,2,6]]
```

## Tuples

Tuples are similar to lists, but can be heterogenous, and its size is part of
its type. This `[(1,'2'),(3,'4')]` is valid, but this `[(1,2),(3,4,5)]` throws
exception.

Functions for pairs (tuples of size 2):

1. `fst` takes a pair and returns the first component
2. `snd` takes a pair and returns the second component

The function `zip` takes in two lists, and returns a list of pairs, matching
elements from the two input lists:

```Haskell
zip [1,2,3] ['a','b','c']
-- [(1,'a'),(2,'b'),(3,'c')]
```
