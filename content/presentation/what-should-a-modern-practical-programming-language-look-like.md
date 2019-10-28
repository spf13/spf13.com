+++
title = "What Should a Modern Practical Programming Language Look Like"
date = 2019-04-05
description = ""
tags = [
    "go",
    "development",
    "history"
]
topics = [
    "Development",
    "golang",
]
+++
Keynote delivered at [The Landing Festival – Berlin](https://landingfestival.com/). This presentation describes the many inspirations and influences of the [Go programming language](http://golang.org) and goes into detail about how we shaped and created the language.

<!--more-->

## Slides

{{% gslides "https://docs.google.com/presentation/d/e/2PACX-1vSrlNlfQpfejgT30VZMkvNf13EYzQbYdnvaXNSKCl0NtfbzbC4ojLLprT97oOxxtw6l5fEufhlf5kcL" %}}

## Recording

{{% youtube xF7RrDyUjn4 %}}

## Transcript

What should a modern, practical programming language look like
Landing Festival – Berlin – April 4, 2019
Steve Francia
Google
@spf13

David McCullough
2012
History is who we are and why we are the way we are.
We are each all shaped by the history of what came before. To understand where we are, we must understand what brought us here.





In the late 1950s people were becoming uneasy how each new computer spawned its own distinct language.
At the time, programming languages were provided by the hardware manufacturers and even differed from model to model. The first language to be consistent across models was Fortran
 but it was still limited to its manufacturer, IBM. A committee was formed to design the first truly universal, machine-independent programming language.


Arc de Triomphe , Champs-Elysées, Paris, 1960. Photo: Charles Weever Cushman (via University of Indiana)


In January 1960, 13 computer scientists met in Paris for an unprecedented meeting with the goal of developing such a language. There were 6 delegates sent from America and 7 delegates from Europe.

The meetings were exhausting, interminable, and exhilarating. One became aggravated when one’s good ideas were discarded along with the bad ones of others. Nevertheless, diligence persisted during the entire period. The chemistry of the 13 was excellent.
 Alan Perlis

Algol

Here is a language so far ahead of its time that it was not only an improvement on its predecessors but also on nearly all its successors.
Tony Hoare
Hints on Programming Language Design – 1973

Algol
Algol W
In spite of that statement, Tony Hoare along with Niklaus Wirth went on to create a successor of ALGOL 60 called ALGOL W


Algol
Algol W
Pascal
which, in turn, led Wirth to go on to create Pascal which was initially published in 1970.

Algol
Algol W
Pascal
CPL
Independently CPL was created at the University of Cambridge as the "Cambridge Programming Language"


Algol
Algol W
Pascal
CPL
BCPL
 it led to BCPL or Basic CPL, a much simpler language based on CPL.


Algol
Algol W
Pascal
CPL
BCPL
 B
At Bell Labs in the US Ken Thompson and Dennis Ritchie created B, based mainly on BCPL



Algol
Algol W
Pascal
CPL
BCPL
B  C
 and shortly after, it’s successor, C.


Algol
Algol W
Pascal
CPL
BCPL
B  C

Pascal
Modula
Oberon
The Pascal branch flourished in Europe, with many successors including Modula and Oberon.


C++
C#
  C
Java
C proliferated in the US inspiring and enabling C++, C#, Java as well as JavaScript, Python, Perl, PHP and many many more languages.

Oberon
2007
Pascal
C
C++
C#
Java
Perl
Python
PHP
JS
Obj C
AWK
Modula
Ruby
Shell
By 2007 dozens of languages existed that can all trace their roots back to the common ancestor Algol

Why Another Language
SECTION TWO

Growing at Google Scale
SECTION 2.1
To understand the answer to this question we need to look at the environment from which Go was born.

At scale everything breaks no matter what you do and you have to deal reasonably cleanly with that and try to hide it from the people actually using your system.
Urs Hölzle
Google: 'At scale, everything breaks'  –  2011
A bit more than 10 years after Google launched, it’s head of infrastructure Urs said...

In its first 10 years Google had experienced scale unlike the world had ever seen before. Growth of hundreds to 10s of thousands times.

In addition to machine scale, Google headcount also grew significantly from well under 1000 employees in 2000 to over 24k in 2010.

Urs Hölzle
Google: 'At scale, everything breaks'  –  2011
Keeping things simple and yet scalable is actually the biggest challenge.
And through all this growth, Urs identified that …

Google’s Scale brought Complexity
+  Massive codebases with many dozens of programmers
+  Very large build farms
+  45+ min builds


Google was struggling with this challenge, especially within its engineering efforts internally.

Brian Kernighan
Software Tools –  1976
Controlling complexity is the essence of computer programming.
So when faced with complexity a good computer scientist knows what to do.

During a 45 minute C++ build…
SECTION 2.2

Rob Pike
Paraphrase

Rob Pike’s words:
Back around September 2007, I was doing some minor but central work on an enormous Google C++ program, one you've all interacted with, and my compilations were taking about 45 minutes on our huge distributed compile cluster. An announcement came around that there was going to be a talk presented by a couple of Google employees serving on the C++ standards committee. They were going to tell us what was coming in C++11.

In the span of an hour at that talk we heard about something like 35 new features that were being planned. …
At this point I asked myself a question:

Did the C++ committee really believe that was wrong with C++ was that it didn't have enough features? Surely..., it would be a greater achievement to simplify the language rather than to add to it.
Rob Pike
2007
Rob returned to his desk with his office mates. This really got them thinking about…

What should a modern, practical programming language look like?
By the time that 45 minute build was done they already had a whiteboard full of ideas.

Ken Thompson
Ken comes from US and C & Unix


Robert Griesemer
Europe
Smalltalk & Pascal

Studied under Niklaus Wirth


Algol
Algol W
Pascal
CPL
BCPL
B  C
Go is the first language that can claim heritage of both the European and US branches of language design. In a very real sense it has unified these two branches as well as a third branch we’ll talk about later.

We built from scratch, borrowing [from C] only minor things like operators and brace brackets and a few common keywords. And of course we also borrowed ideas from other languages we knew. ...
Rob Pike
Less is Exponentially More –  2012
In speaking about Go’s inspiration, Rob Pike states…

Go’s Many Ancestors and Influences
Alef
Algol
APL
BCPL
B
C
C++
CLU
CSP
Java
Limbo
Modula
Newsqueak


Oberon
Occam
Pascal
Python
Simula
Smalltalk

I would claim that there has never been a set of language designers with broader or deeper language design expertise than these three. They had a
rich knowledge of what came before and they knew just what to cherry pick.



Go’s Design Principles
SECTION 2.3
Now I’d like to share with you the 4 design principles that guided the development of the Go language.

Evolution not
revolution
Most ideas come from
 previous ideas
Principle 1. The idea is that most ideas are not new at all.

Evolution not
revolution
New languages should consolidate, not invent features

Waiting for
Good design
No is temporary,
Yes is forever
Principle 2. There are many instances of this throughout Go’s history. The general idea is that when you are designing a language there is no “undo”. If you say “No” today, you can always say “Yes” tomorrow, but if you say “Yes” today you are stuck with that forever

 Joshua Bloch
Joshua Bloch: A conversation about design –  2002
When in doubt,leave it out
Author of Effective Java

Consensus
driven design
As simple as possible,
 but no simpler
Principle 3.

When the three of us got started, it was pure research. … We started off with the idea that all three of us had to be talked into every feature in the language, so there was no extraneous garbage put into the language for any reason.

Ken Thompson
Interview  –  2011
Ken brought this practice in from Bell Labs

There are two ways of constructing a software design.  One way is to make it so simple that there are obviously no deficiencies. And the other way is to make it so complicated that there are no obvious deficiencies.
C.A.R. Hoare
The emperor’s old clothes  –  1981

Go Doesn’t have
Header files
Classes
Inheritance
Constructors
Pointer Arithmetic
Uninitialized values

Annotations
Templates
Exceptions
Globals
Void
...
By design Go’s approach is minimalist. With a goal of simplicity we tried to create a language with as small a feature set as we could while keeping it productive and useful. A lot of features common in other languages were left out of Go including…

Rapid
Iteration
Expect & enable
massive changes
The last principle is that of Rapid iteration. That when you are in the design phase of a language you will need to make frequent and sometimes dramatic changes. Go forward with that expectation and build your process around it.

Russ Cox
Ian Lance Taylor
Within a few months of that 45 minute whiteboard session the team had grown to 5 with the addition of Russ Cox and Ian Lance Taylor.

At this point all the Go source that existed was in a single repo.
Whenever they made a change they would fix all 1000 or so Go files in existence and change them all at once and then commit them back to the repo.

The mechanism they used worked quite well, but they knew wouldn’t scale for long.
Russ would open all the Go files that existed in the world and made the changes with Rob, Ken & Robert looking over his shoulder.

It was a lot of regexp search and replace and then nodding that it looked right.




Over a year of refining
Months of discussion, planning, prototyping, experimenting and whiteboarding
Added one feature at a time
Built two implementations (go, gccgo)

Nearly 5 years of refinement
2007
2009
2012
Started at Google as a 20% project
2 years later, Go is open sourced
After nearly 5 years of development, Go 1.0 is released and attention shifts to using Go
Open Source
Birth
1.0

We spent 5 years developing Go



SECTION 2.3


Concurrent

Simple

Powerful

Fast

Expressive

Readable

Type-safe

Compiled


Compiled
very quickly

Dynamic feeling

Go built for the world

Go was well received especially by the open source community who first embraced Go with notable projects including Docker, Kubernetes and Hugo.

JetBrains 2018 Developer Survey
https://www.jetbrains.com/research/devecosystem-2018/

Go’s adoption has been steady since the 1.0 release. Last year Jetbrains awarded Go the title of most promising programming language.

Go Users
Worldwide 2018

1.5 – 2 Million

Gophers span the world

3 Features
of
SECTION THREE

I’d like to now turn our attention to three specific features of Go which I think you will find interesting to explore a bit deeper.

Object-OrientedProgramming
SECTION 3.1
The first is Go’s approach to Object Orientation.

C++/Java style OO is brittle
This may not be a popular opinion, but it was our experience that when you write programs as inheritance heavy subclass systems it forces you to make decisions early that are very hard to change later



If any part of a system depends on the internals of another part, then complexity increases as the square of the size of the system

Dan Ingalls
Object Oriented Programming — 1989


This should look familiar to anyone who has programmed in an semi recent OO language. The relationships lines are everywhere.
http://www.ejb3.org/jar_file_reverse/jar_file_reverse.html

Inheritance
And we see this exponential complexity in inheritance

Rich Hickey
Clojure for Java Programmers –  2012
It is my opinion that object oriented programming, as delivered by Java, etc., is not a good default way to structure your program.

OO existed long before C++/Java
However, before C++ and Java redefined Object Orientation there was…

Simulation Begin
   Class FittingRoom; Begin
      Ref (Head) door;
      Boolean inUse;
      Procedure request; Begin
         If inUse Then Begin
             Wait (door);
             door.First.Out;
         End;
         inUse:= True;
      End;
      Procedure leave; Begin
         inUse:= False;
         Activate door.First;
      End;
      door:- New Head;
   End;

   Procedure report (message); Text message; Begin
      OutFix (Time, 2, 0); OutText (": " & message); OutImage;
   End;


   Process Class Person (pname); Text pname; Begin
      While True Do Begin
         Hold (Normal (12, 4, u));
         report  (pname & " is requesting the fitting room");
         fittingroom1.request;
         report (pname & " has entered the fitting room");
         Hold (Normal (3, 1, u));
         fittingroom1.leave;
         report (pname & " has left the fitting room");
      End;
   End;

   Integer u;
   Ref (FittingRoom) fittingRoom1;

   fittingRoom1:- New FittingRoom;
   Activate New Person ("Sam");
   Activate New Person ("Sally");
   Activate New Person ("Andy");
   Hold (100);
End;


1965
Simula
Simula took Algol and added to it objects, classes, inheritance and subclasses

It is considered the first object-oriented programming language and was influential in
the development of Smalltalk and all following OO languages.


Code from – https://en.wikipedia.org/wiki/Simula

[Simula] change[d] from the procedural view, ... they flipped it around to … the object-oriented one which is that within every type of object you have all the procedures that work on it.


Dan Ingalls
Object Oriented Programming — 1989
Dan Ingalls, the implementer of Small Talk said…


Object subclass: #Philosophers
    instanceVariableNames: 'forks philosophers randy eating'
    classVariableNames: ''
    poolDictionaries: ''
    category: 'Examples-Processes'!

!Philosophers class methodsFor: 'dining'!

new
    self shouldNotImplement
!

new: quantity
    ^super new initialize: quantity
! !

!Philosophers methodsFor: 'dining'!

dine
    self dine: 15
!

dine: seconds
    (Delay forSeconds: seconds) wait.
    philosophers do: [ :each | each terminate ].
    self initialize: self size
!

leftFork: n
    ^forks at: n
!

rightFork: n
    ^n = self size
	ifTrue: [ forks at: 1 ]
	ifFalse: [ forks at: n + 1 ]
!

initialize: n
    eating := Semaphore new.
    n - 1 timesRepeat: [ eating signal ].

    randy := Random new.
    forks := (1 to: n) collect: [ :each | Semaphore forMutualExclusion ].

Smalltalk
1980
Next came Smalltalk where everything is an object and objects are only communicated with via the sending of messages


Code from : https://raw.githubusercontent.com/gnu-smalltalk/smalltalk/master/examples/Dinner.st

Alan Kay
A to Z of programming languages: Smalltalk-80 –  2010
I did make up this term [object oriented] and it was a bad choice because it under-emphasized the more important idea of message sending.

Smalltalk OO is about message sending
1980
An oversimplification, but a not inaccurate one

    ‘s OO
is patterned
after Smalltalk

Go isn’t pure OO like smalltalk, but the fundamentals are there.

Go’s OO
Methods
&
Interfaces
There are only two mechanisms in Go that provide the object oriented functionality.

Methods
(on any type)
It took the creators a while to realize the only way to do this was to focus only on methods (and not structure) and to permit methods being defined on any type.

Go Methods
type Phone []int

func (p Phone) String() string {
   text := ""
   for _, digit := range p {
		text += string('0' + digit)
   }
   return text
}


Go Methods
type Phone []int

func (p Phone) String() string {
   text := ""
   for _, digit := range p {
		text += string('0' + digit)
   }
   return text
}


Interfaces
Interface types are the mechanism to support an object-oriented programming style.

Interfaces give you a form of dynamic dispatch


Go Interfaces
type Stringer interface {
    String() string
}

Go Interfaces
type Stringer interface {
    String() string
}

Go Interfaces
type Stringer interface {
    String() string
}

func Print(s Stringer) {
   fmt.Println(s.String())
}

Go Interfaces
type Stringer interface {
    String() string
}

func Print(s Stringer) {
   fmt.Println(s.String())
}

Go Methods
type Phone []int

func (p Phone) String() string {
   text := ""
   for _, digit := range p {
		text += string('0' + digit)
   }
   return text
}

Interfaces are implicit, not explicit.
Implementation is entirely independent from each other.

Go Methods & Interfaces

func main() {
    p := Phone{8,0,0,5,5,5,1,3,1,3}
    Print(p)
}

When you try to break a complex problem down you want to try to break it down into as few parts as you can and you want them to be as independent as they can be.

Dan Ingalls
Object Oriented Programming — 1989
Go’s approach of interfaces and methods is as independent as possible. Any type can satisfy any interface as long as the right methods are added. An interface can be defined before or after the types that satisfy the interface. It just works and it works well.

Go’s OO
Methods provide message sending mechanism on any type

Interfaces provide reusability through dynamic dispatch polymorphism

Go is OO in a very real sense as defined by smalltalk even though it doesn’t include classes, objects or inheritance.

Concurrency
SECTION 3.2


Rob Pike
Concurrency is not Parallelism  –  2013
Concurrency is not parallelism. …
Concurrency is about dealing with lots of things at once. Parallelism is about doing lots of things at once.
Parallelism means running code on multiple CPUs at once.

Concurrency is about writing clear programs, so that it’s easy to explain how the program does many things at once.

If you have only one processor, your program can still be concurrent to make it easy to write, but it cannot run in parallel.
But then if you do have multiple processors, there’s an obvious way to parallelize a concurrent program.

Joe ArmstrongProgramming Erlang —  2007

The world is parallel. If we want to write programs that behave as other objects in the real world, then these programs will have a concurrent structure.
Joe Armstrong, the creator of Erlang says…

And even though we have shifted topics to concurrency, Joe is making a case here that a truly object oriented language must be concurrent.

Doug McIlroy
http://facesofopensource.com/doug-mcilroy/

Like virtually all of Go’s features, our concurrency story begins a long time ago with Doug McIlroy

Unix Pipes
1964
Who back in 1964 came up with the idea that became Unix pipes.

1964
We should have some ways of coupling programs like garden hose--screw in another segment when it becomes necessary to massage data in another way. This is the way of IO also.

Paraphrase story.

And over a period from 1970 to 1972, I'd from time to time say, "How about making something like this?", and I'd put up another proposal, another proposal, another proposal. And one day I came up with a syntax for the shell that went along with the piping, and Ken said, "I'm going to do it!" He was tired of hearing all this stuff… [and] he said, "I'm going to do it." He didn't do exactly what I had proposed for the pipe system call; he invented a slightly better one that finally got changed once more to what we have today. He put pipes into Unix [and he did it]... all in one night.



Quoting McIlroy:
There's a paper that's hanging on Brian's wall still, [which] he dredged out somewhere, where I talked about screwing together streams like garden hoses. So this idea had been banging around in my head for a long time.

At the same time that Thompson and Ritchie were on their blackboard, sketching out a file system, I was sketching out how to do data processing on this blackboard by connecting together cascades of processes and looking for a kind of prefix notation language for connecting processes together, and failing because it's very easy to say "cat into grep into ...", or "who into cat into grep", and so on; it's very easy to say that, and it was clear from the start that that was something you'd like to say. But there are all these side parameters that these commands have; they don't just have input and output arguments, but they have the options, and syntactically it was not clear how to stick the options into this chain of things written in prefix notation, cat of grep of who [i.e. cat(grep(who ...))]. Syntactic blinders: didn't see how to do it. So I had these very pretty programs written on the blackboard in a language that wasn't strong enough to cope with reality. So we didn't actually do it.



Tony Hoare
By 1978, there were many proposed methods in use for communication and synchronization in the context of programming multiprocessors. Shared memory was the most common communication mechanism.

Tony Hoare published a paper which changed everything. It was decades ahead of its time. He called his paper, communicating sequential processes.


CSP
1978
Or as it’s better know, CSP.




CSP
1978
Processes: unit of execution
Sequential: each runs as an ordinary single-thread program
Communicating: how processes coordinate
No sharing of memory
No threads, no mutexes
Hoare’s paper proposed a language with processes each running sequentially (or as an ordinary single threaded program) communicating with each other over unbuffered channels.

Hoare's communicating processes are more general than typical Unix shell pipelines, since they can be connected in arbitrary patterns.




Prime Sieve
200 BC
Hoare got the idea to include this from Doug McIlroy and included it in his paper.

In mathematics, the sieve of Eratosthenes is a simple, ancient algorithm for finding all prime numbers up to any given limit.
Doug McIlroy came up with the concurrent version of the Prime Sieve.



2
3
4
5
6
7
8
9
10
11
12
...

2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...

2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...

2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...

2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
2
3
4
5
6
7
8
9
10
11
12
...
...

CSP (from Hoare’s 1978 paper)
1978
[SIEVE(i:1..100)::
    p,mp:integer;
    SIEVE(i - 1)?p;
    print!p;
    mp := p; comment mp is a multiple of p;
*[m:integer; SIEVE(i - 1)?m →
    *[m > mp → mp := mp + p];
    [m = mp → skip
    ||m < mp → SIEVE(i + 1)!m
]   ]
||SIEVE(0)::print!2; n:integer; n := 3;
    *[n < 10000 → SIEVE(1)!n; n := n + 2]
||SIEVE(101)::*[n:integer;SIEVE(100)?n → print!n]
||print::*[(i:0..101) n:integer; SIEVE(i)?n → ...]
]

https://rosettacode.org/wiki/Sieve_of_Eratosthenes




CSP
Erlang
Go
Occam
Three branches of languages emerged from the CSP paper.

Occam in 1983 was close to CSP paper (advised by Hoare)
Erlang in late 80s focused on functional side of CSP and used mailboxes to communicate between processes


Rob Pike
Go’s story begins with Rob pike… but not this Rob Pike...

Rob Pike
This much younger one.. back in 1989

Newsqueak
1989
Rob worked on a successor to an even earlier toy language called Squeak while at Bell Labs


Newsqueak
1989
Research language
Make concurrency in Squeak practical
Syntactically like C
Like CSP, used channels as rendezvous points for processes.










Rob Pike
Newsqueak (1989) looked syntactically like C but was applicative and concurrent.

Idea: a research language to make the concurrency ideas of Squeak practical.

Newsqueak addresses the same problems but in a broader context: Squeak was for designing devices
such as menus and scroll bars; Newsqueak is for writing entire applications, and in particular a window system.

Newsqueak’s communication mechanisms are as in CSP, with channels acting as rendezvous
points for processes.

Fun for after the talk: https://swtch.com/~rsc/thread/squint.pdf.


Newsqueak — Prime Sieve pt. 1
1988
counter := prog(end: int, c: chan of int) {
    i: int;
    for(i = 2; i<end; i++)
        c<-=i;
};

filter := prog(prime: int, listen, send: chan of int) {
    i: int;
    for(;;)
        if((i=<-listen)%prime)
            send<-=i;
};

Newsqueak — Prime Sieve pt. 2
1988
sieve := prog(c: chan of int) {
    for(;;) {
        prime := <-c;
        print(prime, " ");
        newc := mk(chan of int);
        begin filter(prime, c, newc);
        c = newc;
    }
};

count := mk(chan of int);

begin counter(10000, count);
sieve(count);
Unlike in CSP and Squeak,  Newsqueak treats communications channels as first-class objects:
channels can be stored in variables, passed as arguments to functions, and sent across channels.

 Also <-c (receive) is an expression introduce here for the first time (it would later surface in Go)

Alef, Limbo
1990s





Alef & Limbo
1990s
Used for writing real systems software
Built on concurrency ideas in Newsqueak
Alef wasn’t GC’ed and it was painful
Limbo was GC’ed and it was wonderful

both languages that Rob used for writing real systems software
Alef was done for Plan 9 (Bell labs successor to UNIX)
Limbo was done for Inferno, successor to Plan 9
convinced Rob and the others at Bell Labs that CSP was a great way to write concurrent programs like network servers


.
2008


Go
2008
Goroutines
&
Channels
Go has

Goroutines
https://play.golang.org/p/IXkwo_-ruTC
func main() {
    go printer(99)
    time.Sleep(1 * time.Second)
}

func printer(n int) {
    for i := 0; i < n; i++ {
        fmt.Println(i)
        time.Sleep(5 * time.Millisecond)
    }
}
A Goroutine is a function that executes independently, launched by a go statement.

It has its own call stack, which grows and shrinks as required.
It's very cheap. It's practical to have thousands, even hundreds of thousands of goroutines.

It isn’t a thread. The Go runtime multiplexes goroutines onto threads as needed.
There might be only one thread in a program with thousands of goroutines.




Ryan Dahl
Interview with Ryan Dahl, Creator of Node.js –  2017
I like the programming model of Go. Using goroutines is so easy and fun... if you’re building a server, I can’t imagine using anything other than Go.
Goroutines are what make concurrency in Go simple.

Channels
    // Declaring and initializing
    c := make(chan int)

    // Sending a value on a channel
    c <- 1

    // Receiving a value from a channel
    x = <-c


    // Data flows the way the arrow points.
Next is channels which are going to look quite similar to the last few languages we just discussed.



Go — Prime Sieve Pt. 1
2009
func Generate(ch chan<- int) {
    for i := 2; ; i++ {
        ch <- i  // Send 'i' to channel 'ch'.
    }
}
func Filter(src <-chan int, dst chan<- int, prime int) {
    for i := range src {  // Loop over values received
        if i%prime != 0 {
            dst <- i  // Send 'i' to channel 'dst'.
        }
    }
}

Go — Prime Sieve Pt. 1
2009
func Generate(ch chan<- int) {
    for i := 2; ; i++ {
        ch <- i  // Send 'i' to channel 'ch'.
    }
}
func Filter(src <-chan int, dst chan<- int, prime int) {
    for i := range src {  // Loop over values received
        if i%prime != 0 {
            dst <- i  // Send 'i' to channel 'dst'.
        }
    }
}

Go — Prime Sieve Pt. 1
2009
func Generate(ch chan<- int) {
    for i := 2; ; i++ {
        ch <- i  // Send 'i' to channel 'ch'.
    }
}
func Filter(src <-chan int, dst chan<- int, prime int) {
    for i := range src {  // Loop over values received
        if i%prime != 0 {
            dst <- i  // Send 'i' to channel 'dst'.
        }
    }
}

Go — Prime Sieve Pt. 1
2009
func Generate(ch chan<- int) {
    for i := 2; ; i++ {
        ch <- i  // Send 'i' to channel 'ch'.
    }
}
func Filter(src <-chan int, dst chan<- int, prime int) {
    for i := range src {  // Loop over values received
        if i%prime != 0 {
            dst <- i  // Send 'i' to channel 'dst'.
        }
    }
}

Go — Prime Sieve Pt. 1
2009
func Generate(ch chan<- int) {
    for i := 2; ; i++ {
        ch <- i  // Send 'i' to channel 'ch'.
    }
}
func Filter(src <-chan int, dst chan<- int, prime int) {
    for i := range src {  // Loop over values received
        if i%prime != 0 {
            dst <- i  // Send 'i' to channel 'dst'.
        }
    }
}

Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}


// 2

Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009  – https://play.golang.org/p/s88CRWdCrOz
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for i := 0; i < 100; i++ { // Find 100 primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



Go — Prime Sieve Pt. 2
2009
func main() {
	src := make(chan int) // Create a new channel.
	go Generate(src)      // Launch Generate goroutine.
	for { // Find all primes
		prime := <-src
		println(prime)
		dst := make(chan int)
		go Filter(src, dst, prime)
		src = dst
	}
}



go fmt
   &
go fix
SECTION 3.3


go fmt

// Ext returns the file name extension used by path.
func Ext(path string) string {
	for i:=   len( path ) - 1;
	 i >= 0   &&   path[i] != '/';
	 i-- {
	if  path[ i] == '.' {
	return    path[i: ]
	}
	}
	return ""
}
Unformatted Go Code

// Ext returns the file name extension used by path.
func Ext(path string) string {
	for i := len(path) - 1; i >= 0 && path[i] != '/'; i-- {
		if path[i] == '.' {
			return path[i:]
		}
	}
	return ""
}
Formatted Go Code

go fmt
Parses Go source into syntax trees
Prints syntax trees back into source code
Uses the std lib support for these actions
Ended all style debates in Go before they even happened



// Read implements the io.Reader interface.
func (r *Reader) Read(b []byte) (n int, err error) {
	if r.i >= int64(len(r.s)) {
		return 0, io.EOF
	}
	r.prevRune = -1
	n = copy(b, r.s[r.i:])
	r.i += int64(n)
	return
}

No fingerprints left on code
It doesn’t look like generated code, but in reality all Go is machine generated code
An unforeseen and wonderful artifact of GoFmt is that there are no fingerprints on Go code. Looking through all of the source code written on our team it’s impossible to tell who’s code is whose. It’s also impossible to tell which code is generated code vs code written by hand.. And that’s because all of it is generated but in a way that looks and feels natural.

Not what you’d think as a language feature

Planned from
the beginning

Last thing we did before open sourcing Go

It turned out to be one of the best things we did

Now other languages are doing it
(C++, Rust, etc)

Russ Cox
Mailing List November 2009
Once you have gofmt, it becomes very easy to insert mechanical processing between parsing and printing.  So we have all the hard parts of a program
manipulation tool just sitting waiting to be used.

Which takes us to ...

go fix

go fix
Rewrite programs that use old APIs to use newer ones
Much more intelligent than regex rewriting
Allows API changes to be shipped along with code changes




os.Open(a, os.O_RDONLY, 0)
	os.Open(a, os.O_RDONLY, 0666)
	os.Open(a, os.O_RDWR, 0)
	os.Open(a, os.O_CREAT, 0666)
	os.Open(a, os.O_CREAT|os.O_TRUNC, 0664)
	os.Open(a, os.O_CREATE, 0666)
	os.Open(a, os.O_CREATE|os.O_TRUNC, 0664)
	os.Open(a, os.O_WRONLY|os.O_CREATE|os.O_TRUNC, 0666)
	os.Open(a, os.O_WRONLY|os.O_CREATE|os.O_APPEND, 0666)
	os.Open(a, os.O_WRONLY|os.O_CREATE|os.O_EXCL, 0666)
	os.Open(a, os.O_SURPRISE|os.O_CREATE, 0666)
	_ = os.O_CREAT


Originally there was just a multi-arg os.Open:
Originally there was just a multi-arg os.Open which exposed the UNIX api to our users.

Go Fix let us take this bad API and convert it to one that is dramatically better.



	os.Open(a)
	os.Open(a)
	os.OpenFile(a, os.O_RDWR, 0)
	os.Create(a)
	os.Create(a)
	os.Create(a)
	os.Create(a)
	os.Create(a)
	os.OpenFile(a, os.O_WRONLY|os.O_CREATE|os.O_APPEND, 0666)
	os.OpenFile(a, os.O_WRONLY|os.O_CREATE|os.O_EXCL, 0666)
	os.OpenFile(a, os.O_SURPRISE|os.O_CREATE, 0666)
	_ = os.O_CREATE


Go Fix let us take an API and convert it to a better one
No regEx could have made these changes. They required a deep knowledge of the internal structure. It was easy with Go Fix.

Later we used it to make more significant changes to reflect
Too many words


Russ Cox
Introducing Gofix  –  2011
The recent reflect changes would have been unpalatable without automated conversion, and the reflect API badly needed to be redone. Gofix gives us the ability to fix mistakes or completely rethink package APIs without worrying about the cost of converting existing code.

We’ve only scratched the surface
Go upgrades
Look for patterns that are problematic and fix it.
Lots more ways for computer to help you write and maintain your programs.


Go 1.11 (Aug 18) introduced package versioning

Go 1.13 (Aug 19) modules become default
Beyond this we are looking into incorporating go fix or similar into the package release process..
Meaning you can release a new version of a package with a new API and a corresponding “go fix” to automatically upgrade users to this new API.
There’s a lot of details to figure out still but the foundation is there.

The Legacy
of Go
SECTION FIVE


Confucius

Study the past if you would define the future.

Martin Heidegger

The great thinker is one who can hear what is greatest in the work of other "greats" and who can transform it in an original manner.

What should a modern, practical programming language look like?

Go’s Many Ancestors and Influences
Alef
Algol
APL
BCPL
B
C
C++
CLU
CSP
Java
Limbo
Modula
Newsqueak


Oberon
Occam
Pascal
Python
Simula
Smalltalk

Through combining and simplifying the very best ideas from the past 60 years Go simultaneously feels new and original yet also like a familiar reflection of the past.



Thank You
Landing Festival – Berlin – April 4, 2019
Steve Francia
Google
@spf13


Marie Antoinette

There is nothing new except what has been forgotten.

Abraham Lincoln

Books serve to show a man that those original thoughts of his aren't very new after all.
