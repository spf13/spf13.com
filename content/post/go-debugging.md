---
date: 2013-09-23
description: how to debug software when developing in go
draft: true
tags:
- hugo
- cobra
- go
- golang
- development
- debugging
title: Debugging Golang
topics:
- Development
- golang
---

I wrote [cobra](http://cobra.spf13.com), a commander for golang
applications which I wrote because [Hugo](http://hugo.spf13.com) required
a better interface than currently available.

In the process I encountered a particularly nasty bug which required
many hours of debugging to discover the root cause of it.

I was happy to discover that like most things with Go, debugging
is pretty easy and straightforward.

The particularities of my bug aren't important, what's important is that
it involved parsing a tree structure and values changing unexpectedly.

### Code

    Import (
        "runtime"
        "fmt"
    )

    func (c *Commander) out() io.Writer {
        for i := 1; i < 9; i++ {
            fmt.Println(runtime.Caller(i))
        }
        // ... more code here
    }

### output
    0
    251169 /Users/spf13/gopath/src/github.com/spf13/hugo/hugolib/page.go 226 true
    250828 /Users/spf13/gopath/src/github.com/spf13/hugo/hugolib/page.go 216 true
    280603 /Users/spf13/gopath/src/github.com/spf13/hugo/hugolib/site.go 266 true
    276533 /Users/spf13/gopath/src/github.com/spf13/hugo/hugolib/site.go 129 true
    275224 /Users/spf13/gopath/src/github.com/spf13/hugo/hugolib/site.go 94 true
    157727 /Users/spf13/gopath/src/github.com/spf13/hugo/commands/hugo.go 127 true
    156352 /Users/spf13/gopath/src/github.com/spf13/hugo/commands/hugo.go 89 true


