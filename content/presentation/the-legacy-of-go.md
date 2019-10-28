+++
title = "The Legacy of Go"
date = 2019-10-22
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


<!--more-->

## Slides

{{% gslides "https://docs.google.com/presentation/d/e/2PACX-1vRITJJ3iSVn2KUVoCIVAR5mFGDMm73Pc574y3tXkK6EZi-m1W8cqD5VR5t04oNB1ONeqDFUg2ULQOO5" %}}

## Praise
People in attendance called this presentation [beautiful](https://twitter.com/croloris/status/1186672814700544000), [inspirational](https://twitter.com/geototti21/status/1186678981627731969), and [awesome](https://twitter.com/fedepaol/status/1186706415227936768)

## Recording

Coming Soon

## Transcript

The Legacy of Go
Go Lab — Florence — Oct 22, 2019
Steve Francia
Google @spf13
Photo by Steve Francia


It is up to us to live the legacy that was left for us, and to leave a legacy that is worthy of our children and of future generations. 
Christine Gregoire

The Time Before Go

https://pixabay.com/illustrations/time-machine-time-travel-hollywood-2730490/

1950

In the late 1950s people were becoming uneasy how each new computer spawned its own distinct language.
At the time, programming languages were provided by the hardware manufacturers and differed from model to model. The first language to be consistent across models was Fortran but it was still only uniform for its manufacturer, IBM. A committee was formed to design the first truly universal, machine-independent programming language. Image credit: Programming language history Tower of Babel, CACM cover, Jan. 1961


1960

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
There was a continental split between languages as a result 

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
Algol
By 2007 dozens of languages existed that can all trace their roots back to the common ancestor Algol

1964

Doug McIlroy
http://facesofopensource.com/doug-mcilroy/

Our Concurrency story begins with Doug McIlroy

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



1978

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




CSP
Erlang
Alef
Occam
Newsqueak
Limbo
Three branches of languages emerged from the CSP paper. 

Occam in 1983 was close to CSP paper (advised by Hoare)
Erlang in late 80s focused on functional side of CSP and used mailboxes to communicate between processes Rob chased the concurrency white whale for 2 decades 


Algol
Algol W
Pascal
CPL
BCPL
B   C
CSP
Alef
Newsqueak
Limbo
Go is the first language that can claim heritage of both the European and US branches of language design. In a very real sense it has unified these three branches

Go is a language stuck in the 70’s.
Hacker News
Comment written in 2016
This has caused some to criticise Go calling it … 

https://news.ycombinator.com/item?id=11454563

This restorative or revival nature has led some to claim… 

Read QUOTE

What is Old 
is New Again


Proliferation of languages

Tower of Babel


Wave 1. A long time ago there was a lot of diversity of languages. Diversity in thought, approach and opinion. 


Proliferation of languages

Tower of Babel


Standardization

C++, C#, Java
Fast    Complex
Dev Unfriendly

Wave 2. Standardization of languages occurred over decades. By the 2000s things had started to stagnate. They converged into two camps..  Java/JVM.. C# & CLR languages. C++, Java/C#/C++ are all very similar.

Proliferation of languages

Tower of Babel

Standardization

C++, C#, Java
Fast    Complex
Dev Unfriendly
Scripting langs

PHP, Ruby, JS…
Slow   Unsafe Dev Friendly

Wave 3. Scripting languages emerged in prominence as a reaction to the complexity and pain of these languages. Fast and loose. Developer friendly, but lacking performance and safety. 

Proliferation of languages

Tower of Babel

Standardization

C++, C#, Java
Fast    Complex
Dev Unfriendly
Scripting langs

PHP, Ruby, JS…
Slow   Unsafe Dev Friendly
Restorative

Go

Fast    Safe Dev Friendly

Wave 4.  Go is a reaction to the complexity and pain of these languages, and a reaction to the fast and loose nature of the scripting languages. 

Go restored the simplicity and brilliance of early languages, with the added safety and dev friendliness of modern languages. In a very real way Go revived many great ideas whose time was finally ready.





Go feels like a language from the 60s, 70s, 80s, 90s, 00s, 10s, … 
Steve Francia
2019
Go feels like this because it’s composed of many great ideas from the past 60 years. 

Algol
Oberon
C
CSP
Newsqueak
Pascal
Simula
Smalltalk
Now I’d like to talk about 3 specific features in Go and the 4 languages these ideas originated in. Many of these ideas which were forgotten until Go restored them.

https://commons.wikimedia.org/wiki/File:TeamTimeCar.com-BTTF_DeLorean_Time_Machine-OtoGodfrey.com-JMortonPhoto.com-07.jpg

1988

Simple, readable structure & syntax

Oberon & C

Niklaus Wirth
Niklaus Wirth was responsible for Algol-W, Pascal, Modula and now in 1988, his latest language, Oberon. 
https://www.computerhistory.org/fellowawards/hall/niklaus-wirth/


Oberon’s Program Structure
MODULE hello;

IMPORT Out;

BEGIN
    Out.String("Hello, World");
    Out.Ln
END hello.


Oberon was designed around a motto attributed to Albert Einstein: “Make things as simple as possible, but not simpler.” 

The program structure is very simple. 

https://github.com/vishaps/oberonbyexample


Oberon’s Program Structure
MODULE hello;

IMPORT Out;

BEGIN
    Out.String("Hello, World");
    Out.Ln
END hello.


package main

import "fmt"

func main() {
    fmt.Println("hello world")
}

It also should look very familiar. Go directly adopted Oberon’s structure. 

https://github.com/vishaps/oberonbyexample


Oberon’s Declaration Structure
CONST n = 42;

TYPE mystring = ARRAY 32 OF CHAR;

VAR s : mystring;

PROCEDURE squared(x : INTEGER): INTEGER;
BEGIN
    RETURN x * x
END squared;

VAR b, c : INTEGER = 1,2;



const n = 42

type mystring string

var s mystring

func squared(x int) int {
  return x*x
}


var b, c int = 1, 2


In Go and Oberon, declarations are left to right (name always first, type, optional value) as opposed to C where the type comes first, or is inside out.

A lot of people look at Go and ask why we flipped the C syntax, mistakenly thinking that our structure came from C. It didn’t, it came from Oberon. 

https://github.com/vishaps/oberonbyexample/blob/master/variables/Variables.Mod

Go is Oberon shape using C’s tokens
{ } instead of BEGIN END
++, -- instead of (built-ins) INC, DEC
!= instead of #
% instead of MOD
|| instead of OR
[] instead of ARRAY
struct instead of RECORD
\* instead of POINTER TO

While the structure came from Oberon, the tokens Go uses came from C. 

There’s not a lot to this, and that’s the point. The syntax and structure are simple. 

There’s no inheritance, no levels. There’s not a complex scope system. 

They are as simple as possible, but not simpler. 

You can see how Go took the nice simple structure of Oberon, but removed the clunky syntax and replaced it with C’s much more elegant and familiar syntax. 

The result is a very readable language. 

1989

Concurrency

Newsqueak
Russ’ history on Newsqueak: https://swtch.com/~rsc/thread/

Rob Pike
Who worked at Bell Labs in 1989.

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
Unlike its predecessors, CSP and Squeak, Newsqueak treats communications channels as first-class objects: 
channels can be stored in variables, passed as arguments to functions, and sent across channels. 

Also <-c (receive) is an expression introduce here for the first time

Channels & Routines
Go										Newsqueak


c := make(chan int)			c := mk(chan of int);

c <- 1								c <- = 1;

x = <-c								x = <-c;

go f(x) 							begin f(x);

Go’s concurrency approach is pretty much exactly that of Newsqueak. The way you work with channels and “goroutines” is the same. 



Select
Newsqueak


   select {
        case msg1 = <-c1:
            print("received", msg1, "\n");
        case msg2 = <-c2:
            print("received", msg2, "\n");
   }



Newsqueak also used select which looks quite similar to the Go’s select statement. 

You can see clearly how the fundamentals of Go concurrency were established in Newqueak over 25 years ago. 

Go took these ideas and improved on them making them production ready. 




Ryan Dahl
Interview with Ryan Dahl, Creator of Node.js –  2017
I like the programming model of Go. Using goroutines is so easy and fun... if you’re building a server, I can’t imagine using anything other than Go.
Goroutines are what make concurrency in Go simple. 

1965

Fundamental 
Object Orientation

Smalltalk

OO existed long before C++/Java
However, before C++ and Java redefined Object Orientation there was… 

What is Object Orientation?
Procedures attached to data objects

Reusability of procedures


Procedures + Data

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

1980


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

Procedural Reuse

1989
Two publications written this year that we will talk about. 

If any part of a system depends on the internals of another part, then complexity increases as the square of the size of the system

Dan Ingalls
Object Oriented Programming — 1989

Inheritance
And we see this exponential complexity in inheritance 

  
This should look familar to anyone who has programmed in an semi recent OO language. The relationships lines are everywhere. 
http://www.ejb3.org/jar_file_reverse/jar_file_reverse.htmlTHE BIRTH OF SPAGHETTI CODE

  
1989
https://www.cs.utexas.edu/~wcook/papers/OOPSLA89/interfaces.pdf


The system provides the benefits of module interfaces found in languages
like Ada and Modula-2 while preserving the expressiveness that gives untyped object-oriented languages like
Smalltalk their flexibility. 


Canning, Cook, Hill, Olthoff
Interfaces for Strongly-Typed Object-Oriented Programming — 1989

Go Interfaces
type Point interface {
    X() int
    Y() int
    Move(int,int) Point
    Equal(Point) bool
}
The Go team was unaware of this paper at the time they implemented interfaces. The paper was shared with them later due to the clear similarity of the two approaches. 

Go takes a very similar approach, but improves on the idea in the paper in that Go interfaces are implicit, which decouples Go applications and gives immense flexibility. 


When you try to try to break a complex problem down you want to try to break it down into as few parts as you can and you want them to be as independent as they can be.

Dan Ingalls
Object Oriented Programming — 1989
Go’s approach of interfaces and methods is as independent as possible. Any type can satisfy any interface as long as the right methods are added. An interface can be defined before or after the types that satisfy the interface. It just works and it works well. 

Go’s OO
Methods provide message sending mechanism on any type

Interfaces provide reusability through dynamic dispatch polymorphism 

Go is OO in a very real sense as defined by smalltalk even though it doesn’t include classes, objects or inheritance. 

Smalltalk OO is about message sending
1980

Go’s interfaces permit methods to be used as freely as Smalltalk’s messages, but from within a typed language




Go’s Design Philosophy


https://en.wikipedia.org/wiki/TARDIS#/media/File:Tardis_BBC_Television_Center.jpg

2007
Principle 3. 

.

During a 45 minute C++ build… 

Rob Pike
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

Robert Griesemer
Europe
Smalltalk & Pascal

Studied under Niklaus Wirth, one of authors of modula 2, understood oberon 
 

Ken Thompson
Ken comes from US and C & Unix


Evolutionary Process of Language Design

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
rich knowledge of what came before and they knew just what to cherry pick.They also had the advantage of hindsight.  Here was a chance to fix the things that they felt they could do better on. 



Evolution not 
revolution
Most ideas come from
 previous ideas
Principle 1. The idea is that most ideas are not new at all.


https://pixabay.com/illustrations/numbers-one-1-drop-shadow-1487222/ 

Evolution not 
revolution
New languages should consolidate, not invent features

Waiting for
Good design
No is temporary,
Yes is forever
Principle 2. There are many instances of this throughout Go’s history. The general idea is that when you are designing a language there is no “undo”. If you say “No” today, you can always say “Yes” tomorrow, but if you say “Yes” today you are stuck with that forever…. Or for a long time. 

 Joshua Bloch  
Joshua Bloch: A conversation about design –  2002
When in doubt,leave it out
Author of Effective Java

Consensus 
driven design
Everything should be made as simple as possible, but no simpler.
- Einstein 
Principle 3. 

When the three of us got started, it was pure research. … We started off with the idea that all three of us had to be talked into every feature in the language, so there was no extraneous garbage put into the language for any reason.

Ken Thompson
Interview  –  2011
Ken brought this practice in from Bell Labs

There are two ways of constructing a software design.  One way is to make it so simple that there are obviously no deficiencies. And the other way is to make it so complicated that there are no obvious deficiencies.
Tony Hoare
The emperor’s old clothes  –  1981
Go took one approach. Most other languages take the other approach.

Rapid 
Iteration
Expect & enable
massive changes
 
The last principle is that of Rapid iteration. That when you are in the design phase of a language you will need to make frequent and sometimes dramatic changes. Go forward with that expectation and build your process around it. Go fix - to make changes until Go 1.0 

Go Today
How this has evolved 


2019

How Go continues to make changes
These 4 principles worked well at the beginning of the language, before we had a stable release and before we had any adoption. 

Our situation now is very different. We no longer can fit all of our contributors around a whiteboard… or even in a room this size. 

I’d like to share with you now, how the Go project makes changes today. 

Waiting for
Good design
No is temporary,
Yes is forever
Our principle is “waiting for Good design”, which seems to imply that it’s a passive activity, but this is far from the truth. Really what it means is that until we are very confident we have the correct approach, we don’t accept changes. 

What this means is that the default answer is “No” to everything. The cost of “Yes” is very high so there needs to be an overwhelming reason to do it. 

“Yes” to one thing means “No” to everything else


A primary cause of software complexity is that vendors uncritically adopt almost any feature that users want. People seem to misinterpret complexity as sophistication. The incomprehensible should cause suspicion rather than admiration.
Niklaus Wirth
A Plea for Lean Software –  1995
We’re taking a long term view of Go. Designing it for the next decade or 2 or more. Most projects operate on a much shorter timeframe and as a result, typically accept the first passable solution. 

Over time, this has trained people that if an idea is good it will be accepted, or the inverse, that only bad ideas are rejected. 

As a result of our longer term view, it is not uncommon for people to struggle when contributing to the Go project. Many feel personally rejected when their ideas are not accepted. 

Or perhaps worse, people feel unqualified. I remember feeling this way. 

Several years ago, I created Hugo, a website engine, which over time became the #1 user of Go templates, and through the process found several issues. In spite of this I felt very unqualified to even report these issues as I thought that the “experts” who created the libraries clearly knew more than I did and that I couldn’t add to anything they did. At the first or second Gophercon I happened to be standing next to Russ Cox in the lunch line and we began talking. He strongly encouraged me to report these issues and let me know how much they needed feedback like this. 

Fast forward a few years and I joined the Go team and have learned a lot from the experience. One thing I’ve observed is that there is one thing the long term members of the Go team do better than most others, and it’s probably not what you think. The long standing members of the Go team have grown very accustomed to hearing “No”. Proposals from members of our team have a very high rejection rate, even higher than proposals from outside of the Go team. We have learned that each “no” is just one step closer to having the right “yes”. 

Because we hear “no” often we are sympathetic of anyone feeling rejected. 

My message to you today is you are valued and needed. Keep trying. You are a critical part of creating Go for the next decade or 2 or more. 


Go Development Process
https://blog.golang.org/experiment
Experiment
Simplify
Earlier this year, Russ Cox gave an excellent talk about the process we use to make changes to Go and how it’s evolved. 
In his talk he discusses the two steps of experiment and simplify that we iterate over. 

Our process is not built for speed, but correctness. We spend a lot of time experimenting and simplifying, refining our ideas until they are right. 

You are all part of the great experiment that is Go and you are a critical part of the process of continuing to build Go

I’d like to share with you 3 ways in which each of you can contribute to Go. 

Proposal Process
 
Write your experience
You use Go
Identify a problem
You experience something and write about it.



Proposal Process
 
Incorporate feedback
You have an idea
Write a proposal
You have an idea and write up a proposal.



Proposal Process
 
Add your voice
You read proposals
Read comments
You read existing proposals and comment on them. 



Go Development Process
Experiment
Simplify
Ship
Eventually through this refining process the ideas will be ready and we will ship them. I’d like to give additional insights into this part of the process and how it works. 

Consensus 
driven design
Everything should be made as simple as possible, but no simpler.
- Einstein 

MYTH:
There is a small group of “deciders” at Google

TRUTH:
Consensus happens among commenters

Proposal Process Facts
Most proposals are very small 
Nearly all proposal discussions reach a consensus among participants (commenters)

Proposal review committee mostly does “gardening”

https://github.com/golang/go/issues/33502
We’ve started publishing the minutes from our meetings. You can see that it’s not very glamorous work. Most of the issues we comment asking clarifying questions or do nothing and let the conversation continue. We also think about who is missing from the conversation and invite them into it. 

We close a small number of them when the discussion seems to have settled (pro or con). 

Let’s look at a recent proposal. This is just a random one from the pool of recent proposals. 

It has a few interesting properties:
Good amount of participation, 25 comments from 9 participants
Referencing user issues (anchored to experience)
Early on there isn’t consensus (determined by the thumbs). 

After the idea was discussed and refined, it became clear that there was general consensus. 

It was marked as “likely accept” and a sufficient window will be left open for anyone to provide reasons why we shouldn’t accept. 


Here’s a set of recently reviewed proposals. You’ll notice that each of them reference earlier comments and suggest an outcome based on those comments.  

In the proposal review committee typically one person has the role of leaving comments, but is typing on behalf of all in attendance. Russ usually volunteers for this which is why all of these have his name on them. 
Most of the time this window goes by without an additional comments. We feel this window, while rarely used, is essential to the process of establishing consensus.

https://github.com/golang/go/issues/33974


I wanted to share a recent example of when that window was used. The issue looked similar to the others we’ve seen. 

https://github.com/golang/go/issues/33974


However in this case, we misunderstood the situation. Bryan commented as such. 

https://github.com/golang/go/issues/33974


And the issue was revived. In this case the discussion is ongoing. 

This is an interesting one. It started as a fairly broad proposal. Factory methodGood reason to do so

In review, it became clear that there was one narrow use that was very impactful to common operations like JSON encoding. A separate, narrower proposal was filed for that. The broader one was eventually closed, but the more focused one has a lot of discussion on it and is still being discussed. 

Changes happen slowly
And that is by design.
It is slow, slow careful and methodical to ensure that we end up where we want to. 

Major Milestones
Over the Past 
10 Years

While Go changes slow, it is growing quickly. I’d like to walk through some of the major milestones of the past 10 years.

’09
Open sourced
Gopher born
Go moves out of experimental at Google

’10
Open sourced
Gopher born
Go moves out of experimental at Google
Gccgo merged into GCC
Gofix introduced
YouTube adopts Go in production

’11
TIOBE language of the year, Bossie award
Append introduced
Go tour

’12
Go 1.0 released!
Compatibility promise
1st Go production service at Google
TIOBE language of the year, Bossie award
Append introduced
Go tour

’13
Packer, Docker, Hugo written in Go
6-month release cycle
1st Go conference held (Tokyo Japan)

’14
Packer, Docker, Hugo written in Go
6-month release cycle
1st Go conference held (Tokyo Japan)
Kubernetes
Mercurial → Git
1st US & European conferences
500 contributors

’15
Kubernetes
Mercurial → Git
1st US & European conferences
500 contributors
2013
Packer, Docker written in Go
Hugo written in Go
6th month release cycle
1st Go conference held (Tokyo Japan)

’16
Kubernetes
Mercurial → Git
1st US & European conferences
500 contributors
2013
Packer, Docker written in Go
Hugo written in Go
6th month release cycle
1st Go conference held (Tokyo Japan)

’17
GC < ms pauses
Type aliases
#1 language developers want to use (1st time)
13 conferences
1st contributor summit

’18
GC < ms pauses
Type aliases
#1 language developers want to use (1st time)
13 conferences
1st contributor summit

’19
Go modules introduced
More contributions from outside the Go team (1st time)
19 Go conferences 
Go new brand & logo
Go #4 language by PR on github
#1 lang devs intend to learn

Go Worldwide

JetBrains 2019 Developer Survey
https://www.jetbrains.com/lp/devecosystem-2019/


reddit.com/r/golang
 

Go Developer Network

Members
82,921


Groups
152

Countries
46


What’s next for Go

TBD
Down the Road

Modules adoption and polish
Generics (in progress)
More user research
Improved tooling
Gopls 

Q4 ‘19
#GoTurns10 November 10, 2019
Go User Survey

Themes I’m hearing
Big companies want to know:
Who else is using Go?
What is Go good for?
Go is a “modernizer”
Java → Go (microservices)
Cost reduction in microservicesThis is especially important for cloud

Go’s Legacy
5


There is no time machine to the future. The future arrives slowly and unexpectedly. We don’t know what will happen to Go or in the world. But we do know what mark we would like to leave. 

https://pixabay.com/photos/clock-time-arrows-dial-pointer-4307958/

Innovation
We would like Go to be leaving a legacy of innovation. 

Go’s brought innovative ideas like goroutines, channels, simple interfaces to a mainstream audience. These ideas are now showing up in other languages and we are excited for that trend to continue. 

Go fmt was quite controversial when it was introduced in 2009. Now most languages have adopted a similar approach. 

Perhaps our most impactful legacy will be that we’ve inspired people to challenge established norms and look for inspiration everywhere as Go has.



Empowerment
We would like Go to be leaving a legacy of empowerment. 

Go has made it possible for developers to be able to write production server software without the added expertise required by C and C++, without the complexity of modern Java, and without the performance cost of interpreted languages. 

More than any other language, Go empowers people to take their ideas and make it into reality. I personally felt this when I first started writing Hugo and it is what attracted me most to Go. 

Others felt similarly empowered and many have spoken at this conference about their creative uses of Go including Florin’s workshop on Go home automation, Ron’s robots, Elias’s GUI, etc. 

Go changes lives. I have had the privilege of traveling around the world and in every place I've met men and women who often, without CS backgrounds or degrees, have been able to learn Go and use that to start companies, get better jobs, and improve their and their families lives dramatically.




2018
Legacy is not leaving something for people. It’s leaving something in people. 
Peter Strople


We are each all shaped by the history of what came before.  We are the legacy. And we get to be shaped and shape in turn. 

Thank You
Go Lab -- Florence -- Oct 22, 2019
Steve Francia
Google
@spf13