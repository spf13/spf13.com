---
date: 2014-04-01
description: ""
draft: true
tags:
- go
- golang
- php
- ruby
- python
- perl
- C
- C++
- development
title: Pointers vs References
topics:
- Development
- golang
- php
- ruby
- python
---

Some languages including C, C++ support pointers. Other languages
including C++, Java, Python, Ruby, Perl and PHP all support references.
On the surface both references and pointers are very similar, both are
used to have one variable provide access to another one. With both
providing a lot of the same capabilities, it’s often unclear what is
different between these different implementations. In this article I
will illustrate the difference between pointers and references.

## Why does this matter

This matters because pointers are at the very core of effective Go. Most
programmers are learning Go with a foundation in one of the languages
mentioned above. Consequently understanding the difference between
pointers and references is critical to understanding Go. Even if you are
coming from a language that uses pointers, Go’s implementation of
pointers differs from C and C++ in that it retains some of the nice
properties of references while retaining the power of pointers.

The remainder of this article is written with the intent of speaking
broadly about the concept of references rather than about a specific
implementation. We will be using Go as the reference implementation for
pointers.

## What is the difference?

A pointer is a variable which stores the address of another variable.

A reference is a variable which refers to another variable.

To illustrate our point, use the following example in C++ which supports
both pointers and references.

    int i = 3;
    int *ptr = &i;
    int &ref = i;

The first line simply defines a variable. The second defines a pointer
to that variable’s memory address. The third defines a reference to the
first variable.

Not only are the operators different, but you use the differently as
well. With pointers must use the * operator to dereference it. With a
reference no operator is required. It is understood that you are
intending to work with the referred variable.

Continuing with our example, the following two lines will both change
the value of i to 13.

    *ptr = 13;
    ref = 13;

You may be asking, what happens if I try to access the ptr directly
without dereferencing first. This takes us to our second critical
difference between pointers and references. Pointers can be reassigned
while references cannot. In other words, a pointer can be assigned to a
different address.

Consider the following example in Go:

    package main

    import "fmt"

    var pointer *int

    func main() {
        a := 1          // define int
        b := 2          // define int

        pointer = &a
         // set pointer to address of a (&a)
         //   pointer address: 0x2101f1018
         //   pointer value  : 1

        *pointer = 3
         // change the value at address &a to 3
         //   pointer address: 0x2101f1018
         //   pointer value  : 3

        a = 4
         // change the value of a to 4
         //   pointer address: 0x2101f1018
         //   pointer value  : 4

        pointer = &b
         // set pointer to the address of b (&b)
         //   pointer address: 0x2101f1020
         //   pointer value  : 2
    }


So far you could do all of the above in a reasonably similar manner
using references, and often with a simpler syntax.

Stay with me, the following example will illustrate why pointers are
more powerful than references.

Extending the function above:

        ...

        pointer2 = pointer
         // set pointer2 to the address in pointer
         //   pointer  address: 0x2101f1020
         //   pointer  value  : 2
         //   pointer2 address: 0x2101f1020
         //   pointer2 value  : 2

        *pointer = 5
         // change the value at the address &b to 5
         //   pointer  address: 0x2101f1020
         //   pointer  value  : 5
         //   pointer2 address: 0x2101f1020
         //   pointer2 value  : 5
        // If this was a reference pointer & pointer2 would now
        // have different values

        pointer = &a
         // change pointer to address of a (&a)
         //   pointer  address: 0x2101f1018
         //   pointer  value  : 4
         //   pointer2 address: 0x2101f1020
         //   pointer2 value  : 5
        // Since we've changed the address of pointer, it now
        // has a different value then pointer2
    }

The key to understanding the difference is in the second example. 

If we were working with references we would not be able to change the
value of b through *pointer and have that relected in *pointer2. This is
because once you make a copy of a reference they are now independent.
While they may be referring to the same variable, when you manipulate
the reference it will change what it refers to, rather than the
referring value.

The final example demonstrates the behavior when you change the
assignment of one of the pointers to point to a new address. Due to the
limitations of references this is the only operation available.

Next post will feature another property exclusively available to
pointers, the [pointer pointer](/post/pointer-pointers-in-go)

For more information on pointers I’ve found the following resources helpful

* [understanding pointers and memory allocation](http://www.goinggo.net/2013/07/understanding-pointers-and-memory.html)
* [Pointers in Go](http://dave.cheney.net/2014/03/17/pointers-in-go)
* [Pointers](http://www.golang-book.com/8)
