---
date: 2014-04-01
description: ""
draft: true
tags:
- go
- golang
- development
title: Pointer Pointers in Go
topics:
- Development
- golang
---

Pointers are a simple concept with very powerful implications. The Go language
uses pointers heavily throughout the language and standard library. In Go we
can have pointers to any type including ints, structs and even functions. It
isn’t surprising that in go we can also have pointers to pointers. In
our last post we discussed [the differences between pointers and
references](/post/go-pointers-vs-references) while providing a good introduction into what pointers are
and how they behave.

## What are pointers?

As a quick refresher, we will talk briefly about what a pointer is. If
you’d like to learn more about them I suggest reading [the differences between pointers and
references](/post/go-pointers-vs-references) before going further into
this article.

A pointer is a variable which stores the address of another variable. This is
really important to remember when working with pointer pointers.

Before getting into pointer pointers, let’s review the basics of pointers in Go.




