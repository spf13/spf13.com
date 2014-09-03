+++
description = "If you’re a OO programmer, especially one with a background with dynamic languages and are curious about go then this talk is for you. We will cover everything you need to know to leverage your existing skills and quickly start coding in golang"
tags = ["go", "development"]
title = "Go for Object Oriented Programmers"
topics = ["Development", "golang"]
date = 2014-07-31T04:20:08Z
+++

This presentation was given at OSCON 2014.

{{% slideshare 37542912 %}}

Object Oriented (OO) programming has dominated software engineering for the
last two decades. The paradigm built on powerful concepts such as
Encapsulation, Inheritance, and Polymoprhism has been internalized by the
majority of software engineers. Although Go is not OO in the strict sense, we
can continue to leverage the skills we’ve honed as OO engineers to come up with
simple and solid designs.

Gopher Steve Francia, Author of
[Hugo](http://hugo.spf13.com), [Cobra](http://github.com/spf13/cobra), and many
other popular Go packages makes these difficult concepts accessible for everyone.

If you’re a OO programmer, especially one with a background with dynamic
languages and are curious about go then this talk is for you. We will cover
everything you need to know to leverage your existing skills and quickly start
coding in go including:

* How to use our Object Oriented programming fundamentals in go
* Static and pseudo dynamic typing in go
* Building fluent interfaces in go
* Using go interfaces and duck typing to simplify architecture
* Common mistakes made by those coming to go from other OO languages (Ruby, Python, Javascript, etc.),
* Principles of good design in go.

## Slide Transcript


1. Go for Object Oriented Programmers or Object Oriented Programming Without Objects
1. • Author of Hugo , Cobra , Viper & More • Chief Developer Advocate for MongoDB • Gopher @spf13
1. “Most of the appeal for me is not the features that Go has, but rather the features that have been intentionally left out.” —  txxxxd
1. “Why would you have a language that is not theoretically exciting? Because it’s very useful.” — Rob Pike
1. “Objects” in Go
1. Does Go have Objects? • Go lacks Classes • Go lacks “Objects”
1. What is an Object?
1. “An object is an abstract data type that has state (data) and behavior (code).” – Steve Francia
1. type Rect struct { width int height int }
1. Type Declaration (Struct) func (r *Rect) A rea() int { return r.width * r.height }
1. Declaring a Method func main() { r := Rect{width: 10, height: 5} fmt.Println("area: ", r.Area() ) }
1. In Action type Rect s []Rect 
1. Type Declaration (Slice) func (rs Rects) Area() int { var a int for _, r := range rs { a += r.Area() } return a }
1. Declaring a Method func main() { r  := Rect{width: 10, height: 5} x  := Rect{width: 7, height:10} rs := Rects{r, x} fmt.Println("r's area: ", r.Area()) fmt.Println("x's area: ", x.Area()) fmt.Println("total area: ", rs.Area() ) } 
1. In Action http://play.golang.org/p/G1OWXPGvc3 type Foo func() int 
1. Type Declaration (Func) func ( f Foo ) Add(x int) int { return f() + x } 
1. Declaring a Method func main() { var x Foo x = func() int { return 1 } fmt.Println(x()) fmt.Println( x.Add(3) ) } 
1. In Action http://play.golang.org/p/YGrdCG3SlI
1. Go Has “Objects”
1. “Object Oriented” Go
1. A language is usually considered object-based if it includes the basic capabilities for an object: identity, properties, and attributes .   A language is considered object-oriented if it is object-based and also has the capability of polymorphism and inheritance . – Wikipedia
1. Go is Object Based. Is it OO?
1. Inheritance • Provides reuse of objects • Classes are created in hierarchies • Inheritance lets the structure and methods in one class pass down the hierarchy 
1. Go’s approach • Go explicitly avoided inheritance • Go strictly follows the composition over inheritance principle • Composition through embedded types 
1. Composition • Provides reuse of Objects • One object is declared by including other objects • Composition lets the structure and methods in one class be pulled into another
1. Inheritance passes “knowledge” down ! Composition pulls “knowledge” up – Steve Francia
1. type Person struct { Name string Address } type Address struct { Number string Street string City   string State  string Zip    string }
1. Embedding Types 
1. Inner Type func ( a *Address ) String() string { return a.Number+" "+a.Street+"\n"+   a.City+", "+a.State+" "+a.Zip+"\n" } 
1. Declaring a Method func main() { p := Person{ Name: "Steve", Address: Address{ Number: "13", Street: "Main", City:   "Gotham", State:  "NY", Zip:    "01313", }, } } 
1. Declare using Composite Literal
1. func main() { p := Person{ Name: "Steve", Address: Address{ Number: "13", Street: "Main", City:   "Gotham", State:  "NY", Zip:    "01313", }, } fmt.Println(p.String()) 
1. In Action http://play.golang.org/p/9beVY9jNlW
1. Promotion • Promotion looks to see if a single inner type can satisify the request and “promotes” it • Embedded fields & methods are “promoted” • Promot ion only occurs during usage, not declaration • Promoted methods are considered for interface adherance 
1. Not Overloading func (a * Address) String() string { return a.Number+" "+a.Street+"\n"+   a.City+", "+a.State+" "+a.Zip+"\n" } ! func (p * Person) String() string { return p.Name + "\n" + p.Address.String() } 
1. Both Methods Available func main() { p := Person{ Name: "Steve", Address: Address{ Number: "13", Street: "Main", City:   "Gotham", State:  "NY", Zip:    "01313", }, } ! f mt.Println(p.String()) fmt.Println(p.Address.String()) } http://play.golang.org/p/Aui0nGa5Xi
1. Types Remain Distinct func isValidAddress(a *Address) bool { return a.Street != "" } ! func main() { p := Person{ Name: "Steve", Address: Address{ Number: "13", Street: "Main", City: "Gotham", State: "NY", Zip: "01313"}} ! fmt.Println(isValidAddress(p))   // cannot use p (type Person) as type Address   // in argument to isValidAddress fmt.Println(isValidAddress(p.Address)) } http://play.golang.org/p/KYjXZxNBcQ 
1. Promotion is NOT Subtyping
1. Polymorphism • “The provision of a single interface to entities of different types” • Typically implmented via Generics, Overloading and/or Subtyping 
1. Go’s approach • Go explicitly avoided subtyping & overloading • Go does not provide Generics (yet) • Go’s interface provide polymorphic capabilities 
1. Interfaces • A list of required methods • Structural vs Nominal typing • ‘‘If something can do this, then it can be used here ” • Convention is call it a Something-er 
1. Interface Declaration type Shaper interface { Area() int } 
1. Using Interface as Param Type func Describe( s Shaper ) { fmt.Println("Area is: ", s.Area()) } 
1. In Action http://play.golang.org/p/WL77LihUwi func main() { r  := &Rect{width: 10, height: 5} x  := &Rect{width: 7, height: 10} rs := &Rects{r, x} Describe(r) Describe(x) Describe(rs) } 
1. “If you could do Java over again, what would you change?” “I’d leave out classes,” he replied. After the laughter died down, he explained that the real problem wasn’t classes per se, but rather implementation inheritance (the extends relationship). Interface inheritance (the implements relationship) is preferable. You should avoid implementation inheritance whenever possible. – James Gosling (creator of Java)
1. Go Interfaces are based on implementation, not declaration 
1. The Power of Interfaces 
1. type Reader interface { Read(p []byte) (n int, err error) } io.Reader io.Reader • Interface 
1. • Read reads up to len(p) bytes into p • Returns the # of bytes read & any error • Does not dictate how Read() is implemented • Used by os.File, bytes.Buffer, net.Conn, http.Request.Body, loads more 
1. type Writer interface { Write(p []byte) (n int, err error) } io.Writer io.Writer • Interface 
1. • Write writes up to len(p) bytes into p • Returns the # of bytes written & any error • Does not dictate how Write() is implemented • Used by os.File, bytes.Buffer, net.Conn, http.Response.Body, loads more 
1. func MarshalGzippedJSON(r io.Reader,   v interface{}) error { raw , err := gzip.NewReader(r) if err != nil { return err } return json.NewDecoder(raw).Decode(&v) } io.Reader in Action
1. f, err := os.Open("myfile.json.gz") if err != nil { log.Fatalln (err) } defer f.Close() m = make(map[string]interface{}) MarshalGzippedJSON(f , &m) Reading a json.gz file 
1. Practical Interoperability • Gzip.NewReader(io.Reader) • Works on files, http requests, byte buffers, network connections,  …anything you create • Nothing special needed in gzip to be able to do this… Simply call Read(n) and leave the abstracting to the implementor 
1. func main() { resp, err := http.Get("...") if err != nil { log.Fatalln(err) } defer resp.Body.Close() out, err := os.Create("filename.ext") if err != nil { log.Fatalln(err) } defer out.Close() io.Copy(out, resp.Body)  // out io.Writer, resp.Body io.Reader } Pipe http response to file
1. Go 
1. Simple can be harder than complex: You have to work hard to get your thinking clean to make it simple. But it's worth it in the end because once you get there, you can move mountains. —  Steve Jobs
1. Go is simple, pratical & wonderful
1. Go build something great
1. Thank You
