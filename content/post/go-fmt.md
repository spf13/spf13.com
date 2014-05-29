---
date: 2013-10-07
description: using go fmt to quickly refactor your code
draft: false
tags:
- go
- golang
- development
title: Refactoring with go fmt
topics:
- Development
- golang
---

I've recently been getting into go. I've built a [few
packages](http://hugo.spf13.com) [and](/post/announcing-cobra) [libraries](http://spf13.com/project/nitro).

For this post, let's explore the 'gofmt' or 'go fmt' tool further. 

<!--more-->

Go ships with a basic set of tools common to most languages and
development environments. Like most things with go, the tools are simple
in design, but powerful in function.

   * go build – compile the code
   * go install – install (and build) a package
   * go get – download and install packages including dependencies
   * go test – run test suites and benchmarks
   * go doc – generate and view documentation
   * go fmt – format and refactor your code
   * go run – build and run an app

First thing to note, 'go fmt' is just an alias for 'gofmt -l -w'. When
following along, please take note as the two accept different parameters.

## Using gofmt to format code

We've had decades of endless argument and debate about the correct
format of software. Each language has it's own different idioms and
changes and many have multiple differing standards. Golang has done away
with these endless debates once and for all by shipping a formatter
that ensures that all go code follows the exact same format.

Go fmt isn't without it's detractors. People complain that go fmt isn't
customizable and that it puts braces where they don't want them. A standard
isn't customizable, and it's this thinking that has caused so much controversy
in every other language. Go fmt is great. Not only does it know the correct
format, but it understands go code. It properly lines up definitions, properly
wraps if statements when they grow to long and ensures that your code
completely conforms to the standard. 

The best part of this is that all my code complies with the format
standard perfectly and I've never read the go format policy. I just
write code and run go fmt on that code and immediately my code
conforms.


### Preview which changes gofmt will make

The following command will show you all the changes gofmt will make in
diff format.

    $ gofmt -d path-to-code

Given a file, it operates on that file; given a directory, it operates
on all .go files in that directory, recursively.

### Format your code

The following command will make changes directly to your source files.

    $ gofmt path-to-code
    or
    $go fmt -l -w -s path-to-code

Here is an example of the kind of changes gofmt would make

     func (f *Filesystem) Files() []*File {
    -	if len(f.files)<1 {f.captureFiles()}
    +	if len(f.files) < 1 {
    +		f.captureFiles()
    +	}
        return f.files
     }

Given a file, it operates on that file; given a directory, it operates
on all .go files in that directory, recursively.

### Simplify mode
'gofmt' can also simplify code where appropriate with the additional -s
flag. I have found that simplify is safe to use and only will modify
code when it's obvious and clear.

Here is an example of the kind of changes simplify would make.

    -			final = append(final, first[start:len(first)]...)
    +			final = append(final, first[start:]...)

## Using gofmt to refactor code

gofmt is much more powerful than simply eliminating arguments about code
formatting. It can also restructure your code. Unlike using traditional
unix tools like awk and grep, gofmt understands go code and can be used
to restructure your code easily.

gofmt uses patterns to identify changes to make to your code. Patterns
are established in the first half the expression followed by a '->' then
used by the second half of the expression.

Use the flag -d instead of -w to check what gofmt will do prior to
running it.

### Examples

To check files for unnecessary parentheses (example from the docs):

	gofmt -r '(a) -> a' -l *.go

    diff hugolib/summary.go gofmt/hugolib/summary.go
        for i, line := range rstLines {
            if strings.HasPrefix(line, "<body>") {
    -			rstLines = (rstLines[i+1 : len(rstLines)-3])
    +			rstLines = rstLines[i+1 : len(rstLines)-3]
            }
        }

    diff parser/parse_frontmatter_test.go gofmt/parser/parse_frontmatter_test.go
    -		if (err == nil) != test.errIsNil {
    +		if err == nil != test.errIsNil {

Rename a field in a struct. Notice how it not only changes the
definition, but every place that the value is set or referenced.

    gofmt -r 'a.Info -> a.Information' -d ./

    diff hugolib/site.go gofmt/hugolib/site.go

     func (s *Site) initializeSiteInfo() {
    -	s.Info = SiteInfo{
    +	s.Information = SiteInfo{

    -	page.Site = s.Info
    +	page.Site = s.Information

    -	s.Info.Indexes = s.Indexes.BuildOrderedIndexList()
    +	s.Information.Indexes = s.Indexes.BuildOrderedIndexList()

    -	s.Info.LastChange = s.Pages[0].Date
    +	s.Information.LastChange = s.Pages[0].Date

        for _, p := range s.Pages {
    -		p.Site = s.Info
    +		p.Site = s.Information
        }

    -			n.Data["OrderedIndex"] = s.Info.Indexes[plural]
    +			n.Data["OrderedIndex"] = s.Information.Indexes[plural]

        return &Node{
            Data: make(map[string]interface{}),
    -		Site: s.Info,
    +		Site: s.Information,
        }

