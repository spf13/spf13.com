+++
description = "This presentation will walk you through the steps needed to get started with Go."
tags = ["go", "development", "mongodb"]
title = "Getting Started with Go"
topics = ["Development", "golang", "mongodb"]
date = 2014-07-20T08:51:33Z
+++

This presentation was given as a Workshop at OSCON 2014.

{{% slideshare 37166206 %}}


## Description

New to Go? This tutorial will give developers an introduction and practical
experience in building applications with the Go language. Gopher Steve Francia,
Author of [Hugo](http://hugo.spf13.com),
[Cobra](http://github.com/spf13/cobra), and many other popular Go packages
breaks it down step by step as you build your own full featured Go application.

Starting with an introduction to the Go language. He then reviews the fantastic
go tools available. With our environment ready we will learn by doing. The
rest of the time is dedicated building a working go web and cli
application. Through our application development experience we will introduce
key features, libraries and best practices of using Go. 

This tutorial is designed with developers in mind. Prior experience with any of the
following languages: ruby, perl, java, c#, javascript, php, node.js, or python
is preferred. We will be using the MongoDB database as a backend for our
application.

We will be using/learning a variety of libraries including:

* bytes and strings
* templates
* net/http
* io, fmt, errors
* cobra
* mgo
* Gin
* Go.Rice
* Cobra
* Viper


## Slide Transcript:

1. Building   your  first   Go  App 1 Go mascot designed by Ren&#233;e French and copyrighted under the Creative Commons Attribution 3.0 license.
1. @spf13 •Author of Hugo, Cobra, Viper &amp; More •Chief Developer Advocate for MongoDB •Gopher 2
1. My  Go  Story •I write a medium size blog •Frustrated with Wordpress performance &amp; maintenance •Existing Static Site Generators had complicated installations &amp; were very slow •Began writing a S.S.G. in Go called Hugo 1.5 years ago 4
1. hugo.spf13.com
1. Hugo •Hugo is 2nd fastest growing Static Site Generator (40-50 * a week on github) •Hugo is one of the fastest Static Site Generators. 1000x faster than Jekyll •Easiest Installation of any SSG. Download and run •2nd most contributors of any Go project (Docker 1st)6
1. Plan •Introduce Go Language •Introduce Tools &amp; Libraries •Build our application •Tell the world how awesome we are 8
1. Ground  Rules •Workshops are hard, everyone works at a different pace •We will move on when about 50% are ready •Slides are online, feel free to work ahead or catch up 9
1. http:// spf13.com/ presentation/ first-go-app/ 10
1. Installing  Go •You should already have Go installed •If you don’t, do it NOW •Installation Guide 11
1. Installing  MongoDB •You should already have MongoDB installed •If you don’t, do it NOW •Installation Guide 12
1. Git  &amp;  Mercurial •Lastly we need Git &amp; Mercurial •http://git-scm.com/downloads •http://mercurial.selenic.com/wiki/Download 13
1. Introduction     to  Go 14
1. Why  Another  Language? • Software is slow • Sofware is hard to write • Software doesn’t scale well 15
1. Go  is  Fast • Go execution speed is close to C • Go compile time rivals dynamic interpretation 16
1. Go  is  Friendly • Feels like a dynamic language in many ways • Very small core language, easy to remember all of it • Single binary installation, no dependencies • Extensive Tooling &amp; StdLib 17
1. Go  is  Concurrent • Concurrency is part of the language • Any function can become a goroutine • Goroutines run concurrently, communicate through channels • Select waits for communication on any of a set of channels 18
1. Go’s  Inspiration •C: statement and expression syntax •Pascal: declaration syntax •Modula 2, Oberon 2: packages •CSP, Occam, Newsqueak, Limbo, Alef: concurrency •BCPL: the semicolon rule •Smalltalk: methods •Newsqueak: &lt;-, := •APL: iota 19 … AND lessons good and bad from all those plus: C++, C#, Java, JavaScript, LISP, Python, Scala, ...
1. — txxxxd “Most  of  the  appeal   for  me  is  not  the   features  that  Go  has,   but  rather  the   features  that  have   been  intentionally  left   out.” 20
1. — Rob Pike “Why  would  you  have   a  language  that  is   not  theoretically   exciting?  Because  it’s   very  useful.” 21
1. package main ! import &quot;fmt&quot; ! func main() { fmt.Println(“Hello, 世界&quot;) } Hello  World 22
1. Package •Not classes or objects •No subpackages •Fundamental building block in Go •Visibility is package-level, not type-level •Programs run “main” package 23 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. import •Provides access to a package •Package consists of types, functions, etc… •No circular dependencies 24 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. “fmt&quot; •Package path is just   a string •Standard library sits at the root (no path) •Core language is very small •Most functionality is in Stdlibs 25 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. func •Declaring a function •Same syntax for methods, anonymous functions &amp; closures •main.main() is the function run when the program is executed 26 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. Main •No void •No return value •No function args   (command line is in os package) 27 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. { } •Braces not spaces •Feels like C ( &amp; most languages ) •Newline must be after brace   (semicolons are inserted during compiliation) 28 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. fmt •Accessing the package   imported above •Everything visible in the package will be accessible through the name (or alias if provided) 29 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1.  Println • Println, not println • Println, not print_ln •Capital for export •Variadic function using reflection 30 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. “Hello,  世界” •UTF-8 input source •Strings are immutable •Strings are UTF-8 encoded •String is a built-in type 31 package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello, 世界&quot;) }
1. Rob  Pike  did  it  better http://confreaks.com/videos/3419- gophercon2014-opening-day-keynote 32
1. Tons  more… •types •constants •methods •interfaces •pointers •control flow •conditionals •tools •packages •concurrency 33
1. Effective  Go 34
1. Lets  write   some  code   ! Introduce  the     go  tools 35
1. package main ! import &quot;fmt&quot; ! func main() { fmt.Println(&quot;Hello,World&quot;) } Hello  World 36 hello.go
1. ❯ go run hello.go    Hello,World Go  Run 37
1. ❯ go build hello.go ! ❯ls -lh  1.7M Jun 17 22:44 hello  72B Jun 17 22:43 hello.go ! ❯ ./hello  Hello, World Go  Build 38
1. Go  Fmt •Automatically formats Go source code •Ends stylistic debates •Integration with editors (vim, emacs, others) •Can also refactor code   (see http://spf13.com/post/go-fmt ) 39
1. go  Test   •Enables easy testing of application •Integrates with the testing package •Supports benchmark, functional &amp; unit style testing •Combine with ‘looper’ to have realtime feedback 40
1. package main ! import &quot;testing&quot; ! func TestOne(t *testing.T) { one := false if !one { t.Errorf(“Test Failed”) } } Hello  Test 41 hello_test.go
1. ❯ go test ./... --- FAIL: TestOne (0.00 seconds) hello_test.go:8: Test failed FAIL FAIL_/Code/firstApp0.012s ! ! ❯ go test ./... ok _/Code/firstApp0.012s Go  Test 42
1. Go   Planet 43The planet logo is based on the Go mascot designed by Ren&#233;e French and copyrighted under the Creative Commons Attribution 3.0 license.
1. Why  Planet? •CLI application •Web application •Good introduction •Right sized •Database (MongoDB) •Concurrency 45
1. Steps 0. Env Setup 1. Commands 2. Configuration 3. Working with Feeds 4. DB as Storage 5-6. Web Server 7-8. DB -&gt; Templates 9. &amp; 10. Add Polish 46
1. Step  0     Setting  up  our   environment 47
1. Go  PAth   ! $GOPATH 48
1. Go  path •The GOPATH environment variable specifies the location of your workspace (and dependencies) •It must not be the same path as your Go installation 49
1. ❯ mkdir $HOME/go  ! ❯ export   GOPATH=$HOME/go Setting  up 50
1. export GOPATH=$USER/go export GOROOT=`go env GOROOT` PATH=$PATH:$GOPATH/bin Linux  &amp;  Mac 51 Add this to your ~/.bashrc (or equivalent)
1. Windows •Control panel &gt; System 52
1. Go  PAth •/home/user/gocode/ ($GOPATH) • src/ (put your source code here) • bin/ (binaries installed here) • pkg/ (installed package objects) 53
1. Creating  our   project 54
1. Project  Dir •Make a directory inside of $GOPATH/src •I like mine to be in   $GOPATH/src/github.com/spf13/PROJECTNAME •It can not be a symlink •We will call this our working directory or $wd 55
1. package main ! import &quot;fmt&quot; ! func main() { fmt.Println(“My Project&quot;) } main.go 56
1. ❯ go run main.go    My Project Run  it 57
1. 58 I’m on the #gopath with @spf13 at #OSCON  http://j.mp/onGoPath Tweet  Break
1. Step  1     Creating  the   Command(s) 59
1. Defining    our  first   command 60
1. Structs •Short for structure •Objectish … blend of data &amp; methods, but no inheritance •Really cheap. Struct{} is free (0 bytes). 61
1. Functions •Can have multiple return values •No overloading •No optional parameters (but variadic) 62
1. First  class  Functions •Function literals are anonymous functions in Go •Can assign to a variable or field •Can use as function parameters or return values •Can be created as a goroutine 63
1. pointers •Function calls copy arguments into the function •Pointers reference a location in memory where a value is stored rather than the value itself •In Go a pointer is represented using the * •The &amp; operator gives us the address of a variable •Go automatically dereferences pointers when using “.” 64
1. cobra •A CLI Commander •Easy management of commands &amp; flags •Used by bitbucket, openshift &amp; lots more 65 http://fav.me/d5gkby7
1. go get -u   github.com/spf13/cobra Getting  Cobra 66
1. ❯ mkdir $wd/commands Commands  Dir 67
1. // Copyright &#169; 2014 Steve Francia &lt;spf@spf13.com&gt;. // // Use of this source code is governed by an Apache2 // license that can be found in the LICENSE file. ! package commands ! import ( &quot;fmt&quot; &quot;os&quot; ! &quot;github.com/spf13/cobra&quot; ) planet.go  (1) 68
1. Path  =  Url go get uses it to install 69
1. var RootCmd = &amp;cobra.Command{ Use: &quot;dagobah&quot;, Short: `Dagobah is an awesome planet style RSS aggregator`, Long: `Dagobah provides planet style RSS aggregation. It is inspired by python planet. It has a simple YAML configuration and provides it&#39;s own webserver.`, Run: func(cmd *cobra.Command, args []string) { fmt.Println(&quot;Dagobah runs&quot;) }, } planet.go  (2) 70
1. executing   cobra’s   command 71
1. Variable  Assignment •‘:=‘ is the short variable declaration operator  Declares, creates &amp; assigns simultaneously while infering type •Assignment via ‘=‘ requires prior declaration •var foo int = 10 is the same as foo := 10 72
1. Error  Handling •Errors are not exceptional. Should be part of the language •Typically one of the return values •No exceptions in Go fd, err := os.Open(&quot;test.go&quot;)  if err != nil {  log.Fatal(err)  } 73
1. (  Don’t)  Panic •Should rarely be used if ever •Performs a full stack trace dump for end users •Use only in the most dire circumstances (like package can’t find FileSystem) •Can use ‘recover’, but only inside deferred functions 74
1. func Execute() { err := RootCmd.Execute() if err != nil { fmt.Println(err) os.Exit(-1) } } planet.go  (3) 75
1. // Copyright &#169; 2014 Steve Francia &lt;spf@spf13.com&gt;. // // Use of this source code is governed by an Apache2 // license that can be found in the LICENSE file. ! package main ! import &quot;github.com/spf13/firstGoApp-Planet/commands&quot; ! func main() { commands.Execute() } main.go 76 Make sure to use your path
1. ❯ go run main.go  Dagobah runs ! ❯ go run main.go help Running  it 77
1. Getting  Help •https://godoc.org/github.com/spf13/cobra •https://github.com/spf13/firstGoApp-Planet/ tree/step1 78
1. Creating #CobraCommands with @spf13 at #OSCON http://j.mp/cobracmd Tweet  Break
1. Step  2     Easy  Configuration 80
1. Handing   Config  files 81
1. Package  Identifiers •Export with Capital name •No automatic getters &amp; setters •var field … func Field() … func SetField()   are appropriate names 82
1. init() •Each source file can have one (or multiple) •Niladic function to setup state   (function without return value) •Called after all variable declarations in the package 83
1. Scoping •Very granular scoping. •Variables declared inside { } only survive in that cotrol structure (for, if, etc) •The := trap  if := is used to declare x and x already exists in an outer scope a new variable x will be created (shadowing) 84
1. package main ! import ( &quot;errors&quot; &quot;fmt&quot; ) ! var Foo int ! func Zero() (int, error) { return 0, errors.New(&quot;yo&quot;) } ! ! func main() { ! Foo = 10 ! fmt.Println(&quot;outer:&quot;, Foo) // 10 ! if Foo, err := Zero(); err != nil { fmt.Println(&quot;inner:&quot;, Foo) // 0 } ! fmt.Println(&quot;outer again:&quot;, Foo) // still 10 } :=  Trap 85http://play.golang.org/p/i4L9Ao1P65
1. Viper •A configuration manager •Easy loading of config files •Registry for application settings •Designed to work well with (or without) Cobra 86
1. go get -u   github.com/spf13/viper Getting  Viper 87
1. // Copyright &#169; 2014 Steve Francia &lt;spf@spf13.com&gt;. // // Use of this source code is governed by an Apache2 // license that can be found in the LICENSE file. ! package commands ! import ( &quot;fmt&quot; &quot;os&quot; ! &quot;github.com/spf13/cobra&quot; &quot;github.com/spf13/viper&quot; ) planet.go  (1) 88
1. var CfgFile string ! func init() { cobra.OnInitialize(initConfig)  RootCmd.PersistentFlags().StringVar(&amp;CfgFile, &quot;config&quot;, &quot;&quot;, &quot;config file (default is $HOME/dagobah/config.yaml)&quot;) } ! func initConfig() { if CfgFile != &quot;&quot; { viper.SetConfigFile(CfgFile) } viper.SetConfigName(&quot;config&quot;) viper.AddConfigPath(&quot;/etc/dagobah/&quot;) viper.AddConfigPath(&quot;$HOME/.dagobah/&quot;) viper.ReadInConfig() } planet.go  (2) 89
1. Creating  our   config  file 90
1. appname: &quot;Dagobah&quot; feeds: - &quot;http://spf13.com/index.xml&quot; - &quot;http://dave.cheney.net/feed&quot; - &quot;http://www.goinggo.net/feeds/posts/default&quot; - &quot;http://blog.labix.org/feed&quot; - &quot;http://blog.golang.org/feed.atom&quot; ! $HOME/.dagobah/config.yaml 91
1. trying  it  out 92
1. var RootCmd = &amp;cobra.Command{ Use: &quot;...&quot;, Short: `...`, Long: `...`, Run: rootRun, } ! func rootRun(cmd *cobra.Command, args []string) { fmt.Println(viper.Get(&quot;feeds&quot;)) fmt.Println(viper.GetString(&quot;appname&quot;)) } planet.go  (3) 93
1. ❯ go run main.go  [http://spf13.com/index.xml http:// dave.cheney.net/feed http:// www.goinggo.net/feeds/posts/default http://blog.labix.org/feed http:// blog.golang.org/feed.atom]    Dagobah Running  it 94
1. I got bit by the #goviper at #OSCON   http://j.mp/go-viper Tweet  Break
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step2 96
1. Step  3     Working  with  Feeds 97
1. Finding   Libraries 98
1. Go-Search.org 99
1. Go  wiki 100
1. go-pkg-rss •Fetch Rss and Atom feeds from the internet •Supports RSS .92, 1.0, 2.0 &amp; Atom 1.0 •Respects TTL, SkipDays, CacheTimeout, etc in the feeds 101
1. go get -u   github.com/jteeuwen/go- pkg-rss Getting  Go-PKG-RSS 102
1. boilerplate    stuff 103
1. import ( &quot;time&quot; ... ) ! func addCommands() { RootCmd.AddCommand(fetchCmd) } ! func Execute() { addCommands() ... } planet.go 104
1. // Copyright &#169; 2014 Steve Francia &lt;spf@spf13.com&gt;. // // Use of this source code is governed by an Apache2 // license that can be found in the LICENSE file. ! package commands ! import ( &quot;fmt&quot; &quot;os&quot; &quot;time&quot; ! rss &quot;github.com/jteeuwen/go-pkg-rss&quot; &quot;github.com/spf13/cobra&quot; &quot;github.com/spf13/viper&quot; ) Fetch.Go  (1) 105
1. Creating  our   own  type 106
1. Named  Types •Can be any known type (struct, string, int, slice, a new type you’ve declared, etc) •Can have methods declared on it •Not an alias. Explicit type. 107
1. Slices  &amp;  arrays •Array is fixed in length •Slice can be viewed as a dynamic array (can grow) •Slice is a view of an array •Slice is the core data structure in Go for lists of data 108
1. type Config struct { Feeds []string Port int } Fetch.Go  (2) 109
1. Defining  the   fetch   command 110
1. New(    ) •new(T) Does 2 things at once: •Allocates new zeroed value of type T •Returns a pointer to the new value ( *T) •Used for all non-reference types 111
1. Make(  ) •Creates slices, maps, and channels only •These types are special “reference” types •Makes a initialized (not zeroed) value of type T •Does not return a pointer 112
1. Composite  Literals •An expression that creates a new value each time it is evaluated •We’ve already used these quite a bit •Can also be create values of arrays, slices, and maps •Pseudo Constructor •eg File{fd: fd, name: name} 113
1. Constructors •Not built into Go •Use Composite Literals when possible •If initialization is needed use a factory •Convention is to use New___() •… or New() when only one type is exported in the package 114
1. var fetchCmd = &amp;cobra.Command{ Use: &quot;fetch&quot;, Short: &quot;Fetch feeds&quot;, Long: `Dagobah will fetch all feeds listed in the config file.`, Run: fetchRun  } ! func init() { fetchCmd.Flags().Int(&quot;rsstimeout&quot;, 5, &quot;Timeout (in min) for RSS retrival&quot;) viper.BindPFlag(&quot;rsstimeout&quot;, fetchCmd.Flags().Lookup(&quot;rsstimeout&quot;)) } Fetch.go  (3) 115
1. Fetching  in  a   goroutine 116
1. GoRoutines •A function executing concurrently with other goroutines in the same address space •Lightweight •Not threads, coroutines, or processes 117
1. Channels •Channels are lightweight •Synchronize goroutines by communication rather than locking shared memory •Channel &lt;- Sender —- Writes block when channel is full •&lt;- Channel —- Reads blocks waiting for something to be read •Great talk on channels given at GopherCon  http://confreaks.com/videos/3422-gophercon2014-a-channel-compendium 118
1. Marshaling  into •We can’t return a T (no generics) •We can reflect on any value of any type •Marshal accepts the address of the value so it can manipulate the value directly 119
1. func fetchRun(cmd *cobra.Command, args []string) {   Fetcher() ! sigChan := make(chan os.Signal, 1) signal.Notify(sigChan, os.Interrupt) &lt;-sigChan } Fetch.go  (4) 120
1. func Fetcher() { var config Config if err := viper.Marshal(&amp;config); err != nil { fmt.Println(err) } ! for _, feed := range config.Feeds { go PollFeed(feed.Url) } } Fetch.go  (5) 121
1. Building  our   fetcher 122
1. Learning  about  go-pkg-rss •How do we learn how to use the package? 123
1. Learning  about  go-pkg-rss •github.com/jteeuwen/go-pkg-rss •Readme is pretty lacking •godoc.org/github.com/jteeuwen/go-pkg-rss 124
1. godoc.org/github.com/jteeuwen/go-pkg-rss 125
1. Go  Search 126
1. For •For, Foreach &amp; While are all spelled ‘for’ in Go for init; condition; post { }   // Like a C for for condition { }   // Like a C while for { }   // Like a C for(;;) 127
1. func PollFeed(uri string) { timeout := viper.GetInt(&quot;RSSTimeout&quot;) if timeout &lt; 1 { timeout = 1 } feed := rss.New(timeout, true, chanHandler, itemHandler) ! for { if err := feed.Fetch(uri, nil); err != nil { fmt.Fprintf(os.Stderr, &quot;[e] %s: %s&quot;, uri, err) return } ! fmt.Printf(&quot;Sleeping for %d seconds on %sn&quot;, feed.SecondsTillUpdate(), uri) time.Sleep(time.Duration(feed.SecondsTillUpdate() * 1e9)) } } Fetch.GO  (6) 128
1. func chanHandler(feed *rss.Feed, newchannels []*rss.Channel) { fmt.Printf(&quot;%d new channel(s) in %sn&quot;, len(newchannels), feed.Url) } ! func itemHandler(feed *rss.Feed, ch *rss.Channel, newitems []*rss.Item) { fmt.Printf(&quot;%d new item(s) in %sn&quot;, len(newitems), feed.Url) } Fetch.go  (7) 129
1. ❯ go run dagobah.go fetch --rsstimeout=1    15 new item(s) in http://spf13.com/index.xml  1 new channel(s) in http://spf13.com/index.xml  Sleeping for 300 seconds on http://spf13.com/index.xml  25 new item(s) in http://www.goinggo.net/feeds/posts/default  1 new channel(s) in http://www.goinggo.net/feeds/posts/default  Sleeping for 300 seconds on http://www.goinggo.net/feeds/posts/ default  10 new item(s) in http://dave.cheney.net/feed  1 new channel(s) in http://dave.cheney.net/feed  Sleeping for 299 seconds on http://dave.cheney.net/feed  Running  it 130
1. Tweet  Break I wrote my first goroutine at #OSCON with @spf13
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step3 132
1. Step  4     Storing  in    the  Database 133
1. Pretty •github.com/kr/pretty •pretty.Println(X,Y,Z) 134
1. MongoDB •Open Source •Document Database •Document == Struct or Document == Map •Works seamlessly with Go (and other languages) 135
1. MongoDB •Fast &amp; Scalable •Used by Disney, IBM, Metlife, eBay, Forbes, Craigslist, Cisco, Stripe 136
1. Mgo •Developed by the open source community •Heavily used throughout Go community •&quot;mgo is the best database driver I&#39;ve ever used.&quot;  — Patrick Crosby, Founder of StatHat •&quot;mgo and Go are a pair made in heaven.  — Brian Ketelsen, Author of GopherTimes.com137
1. go get -u gopkg.in/mgo.v2 Getting  mgo 138
1. boilerplate  stuff 139
1. // Copyright &#169; 2014 Steve Francia &lt;spf@spf13.com&gt;. // // Use of this source code is governed by an Apache2 // license that can be found in the LICENSE file. ! package commands ! import ( &quot;fmt&quot; &quot;os&quot; ! &quot;github.com/spf13/viper&quot; &quot;gopkg.in/mgo.v2&quot; ) ! var mongodbSession *mgo.Session ! func init() { RootCmd.PersistentFlags().String(&quot;mongodb_uri&quot;, &quot;localhost&quot;, &quot;host where mongoDB is&quot;) viper.BindPFlag(&quot;mongodb_uri&quot;, RootCmd.PersistentFlags().Lookup(“mongodb_uri&quot;)) CreateUniqueIndexes() } MongoDB.go  (1) 140
1. Setting  up  a   DB  session 141
1. func DBSession() *mgo.Session { if mongodbSession == nil { uri := os.Getenv(&quot;MONGODB_URI&quot;) if uri == &quot;&quot; { uri = viper.GetString(&quot;mongodb_uri&quot;) ! if uri == &quot;&quot; { log.Fatalln(&quot;No connection uri for MongoDB provided&quot;) } } ! var err error mongodbSession, err = mgo.Dial(uri) if mongodbSession == nil || err != nil { log.Fatalf(&quot;Can&#39;t connect to mongo, go error %vn&quot;, err) } ! mongodbSession.SetSafe(&amp;mgo.Safe{}) } return mongodbSession } MongoDB.go  (2) 142
1. setting  up   some   shortcuts 143
1. ! func DB() *mgo.Database { return DBSession().DB(viper.GetString(&quot;dbname&quot;)) } ! func Items() *mgo.Collection { return DB().C(&quot;items&quot;) } ! func Channels() *mgo.Collection { return DB().C(&quot;channels&quot;) } MongoDB.go  (3) 144
1. Setting  up   indexes 145
1. func CreateUniqueIndexes() { idx := mgo.Index{ Key: []string{&quot;key&quot;}, Unique: true, DropDups: true, Background: true, Sparse: true, } ! if err := Items().EnsureIndex(idx); err != nil { fmt.Println(err) } ! if err := Channels().EnsureIndex(idx); err != nil { fmt.Println(err) } } MongoDB.go  (4) 146
1. Preparing   the  data 147
1. Data  Prep •Feeds are dirty •Go doesn’t allow “patching” of structs (not how structs work) •MongoDB works with native types &amp; named types 148
1. Tags  (Annotations) •String literal following a field declaration •Provides additional information during reflection •Used by JSON, BSON, YAML, etc 149
1. for  x,y  :=  range •Provides a way to iterate over an array, slice, string, map, or channel. •Like Foreach or Each in other languages •x is key, y is value… can ignore by setting to _ 150
1. Append •Append is really awesome, feels like push, but does a lot more. •Append will grow a slice (both length &amp; capacity) •… and copy the underlying array if needed 151
1. type Itm struct { Date time.Time Key string ChannelKey string Title string FullContent string Links []*rss.Link Description string Author rss.Author Categories []*rss.Category Comments string Enclosures []*rss.Enclosure Guid *string `bson:&quot;,omitempty&quot;` Source *rss.Source PubDate string Id string `bson:&quot;,omitempty&quot;` Generator *rss.Generator Contributors []string Content *rss.Content Extensions map[string]map[string][]rss.Extension } fetch.go 152
1. func itmify(o *rss.Item, ch *rss.Channel) Itm { var x Itm x.Title = o.Title x.Links = o.Links x.ChannelKey = ch.Key() x.Description = o.Description x.Author = o.Author x.Categories = o.Categories x.Comments = o.Comments x.Enclosures = o.Enclosures x.Guid = o.Guid x.PubDate = o.PubDate x.Id = o.Id x.Key = o.Key() x.Generator = o.Generator x.Contributors = o.Contributors x.Content = o.Content x.Extensions = o.Extensions x.Date, _ = o.ParsedPubDate() ! if o.Content != nil &amp;&amp; o.Content.Text != &quot;&quot; { x.FullContent = o.Content.Text } else { x.FullContent = o.Description } ! return x } fetch.go 153
1. type Chnl struct { Key string Title string Links []rss.Link Description string Language string Copyright string ManagingEditor string WebMaster string PubDate string LastBuildDate string Docs string Categories []*rss.Category Generator rss.Generator TTL int Rating string SkipHours []int SkipDays []int Image rss.Image ItemKeys []string Cloud rss.Cloud TextInput rss.Input Extensions map[string]map[string] []rss.Extension Id string Rights string Author rss.Author SubTitle rss.SubTitle } fetch.go 154
1. func chnlify(o *rss.Channel) Chnl { var x Chnl x.Key = o.Key() x.Title = o.Title x.Links = o.Links x.Description = o.Description x.Language = o.Language x.Copyright = o.Copyright x.ManagingEditor = o.ManagingEditor x.WebMaster = o.WebMaster x.PubDate = o.PubDate x.LastBuildDate = o.LastBuildDate x.Docs = o.Docs x.Categories = o.Categories x.Generator = o.Generator x.TTL = o.TTL x.Rating = o.Rating x.SkipHours = o.SkipHours x.SkipDays = o.SkipDays x.Image = o.Image x.Cloud = o.Cloud x.TextInput = o.TextInput x.Extensions = o.Extensions x.Id = o.Id x.Rights = o.Rights x.Author = o.Author x.SubTitle = o.SubTitle ! ... ! return x } fetch.go 155
1. ... ! ! var keys []string for _, y := range o.Items { keys = append(keys, y.Key()) } x.ItemKeys = keys ! ... fetch.go 156
1. Storing   Feeds  &amp;   Items 157
1. The  Blank  Identifier  ‘_’ •Used to ignore return values from a function •Used with imports as an alias • Allows import of unused packages so init functions can be executed 158
1. func chanHandler(feed *rss.Feed, newchannels []*rss.Channel) { fmt.Printf(&quot;%d new channel(s) in %sn&quot;, len(newchannels), feed.Url) for _, ch := range newchannels { chnl := chnlify(ch) if err := Channels().Insert(chnl); err != nil { if !strings.Contains(err.Error(), &quot;E11000&quot;) { fmt.Printf(&quot;Database error. Err: %v&quot;, err) } } } } fetch.go 159
1. func itemHandler(feed *rss.Feed, ch *rss.Channel, newitems []*rss.Item) { fmt.Printf(&quot;%d new item(s) in %sn&quot;, len(newitems), feed.Url) for _, item := range newitems { itm := itmify(item, ch) if err := Items().Insert(itm); err != nil { if !strings.Contains(err.Error(), &quot;E11000&quot;) { fmt.Printf(&quot;Database error. Err: %v&quot;, err) } } } } fetch.go 160
1. Running   MongoDB 161
1. ❯ mongod    MongoDB starting : pid=51054 port=27017 dbpath=/data/db Running  MongoDB 162
1. ❯ mongo        Mongo  Shell 163
1. ❯ go run dagobah.go fetch --rsstimeout=1    15 new item(s) in http://spf13.com/index.xml  1 new channel(s) in http://spf13.com/index.xml  Sleeping for 300 seconds on http://spf13.com/index.xml  25 new item(s) in http://www.goinggo.net/feeds/posts/default  1 new channel(s) in http://www.goinggo.net/feeds/posts/default  Sleeping for 300 seconds on http://www.goinggo.net/feeds/posts/ default  10 new item(s) in http://dave.cheney.net/feed  1 new channel(s) in http://dave.cheney.net/feed  Sleeping for 299 seconds on http://dave.cheney.net/feed  Running  planet 164
1. &gt; use dagobah &gt; db.items.findOne() { &quot;_id&quot; : ObjectId(&quot;53b4c08bddbc460a933cf3ed&quot;), &quot;date&quot; : ISODate(&quot;2014-07-01T00:00:00Z&quot;), &quot;key&quot; : &quot;http://spf13.com/post/go-pointers-vs-references&quot;, &quot;channelkey&quot; : &quot;Recent Content on Hacking Management&quot;, &quot;title&quot; : &quot;Pointers vs References&quot;, &quot;links&quot; : [ { &quot;href&quot; : &quot;http://spf13.com/post/go-pointers-vs-references&quot;, &quot;rel&quot; : &quot;&quot;, &quot;type&quot; : &quot;&quot;, &quot;hreflang&quot; : &quot;&quot; Looking  at  the  Data 165
1. _ID •MongoDB’s primary key •Default is to use an “object_id” •Object_id guaranteed to be unique across your entire cluster •MongoDB will create it for you on insert 166
1. Tweet  Break Feeding mgo at #OSCON with @spf13 http://j.mp/mongomgo
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step4 168
1. Step  5     Building  a    web  Server 169
1. Lots  of  choices •Beego  High-performance web framework •Gin  Martini like with better performance •Goji  A minimalistic web framework •Gorilla   A web toolkit •httprouter  A high performance router •Mango   modular web-app framework like Rack •Martini   modular web apps &amp; services •net/http  Standard library web package •pat  Sinatra style, by the author of Sinatra. •Revel  A high-productivity web framework •tigertonic  framework for JSON web services •traffic  Sinatra inspired web framework for Go •web.go  A simple framework to write webapps in Go. 170
1. Gin •Compatible with net/http •Uses Httprouter (really fast) •Familiar/Friendly Interface •Works well with JSON •Had to pick something 171
1. go get -u  github.com/gin-gonic/gin Getting  Gin 172
1. boilerplate    stuff 173
1. // Copyright &#169; 2014 Steve Francia. // // Use of this source code is governed by an Apache2 // license that can be found in the LICENSE file. ! package commands ! import ( &quot;github.com/gin-gonic/gin&quot; &quot;github.com/spf13/cobra&quot; &quot;github.com/spf13/viper&quot; ) Server.Go  (1) 174
1. Defining  the   Server   command 175
1. var serverCmd = &amp;cobra.Command{ Use: &quot;server&quot;, Short: &quot;Server for feeds&quot;, Long: `Dagobah will serve all feeds listed in the config file.`, Run: serverRun, } ! func init() { serverCmd.Flags().Int(&quot;port&quot;, 1138, &quot;Port to run Dagobah server on&quot;) viper.BindPFlag(&quot;port&quot;, serverCmd.Flags().Lookup(&quot;port&quot;)) } server.go  (2) 176
1. func addCommands() { RootCmd.AddCommand(fetchCmd) RootCmd.AddCommand(serverCmd) } planet.go 177
1. Defining  our   first  route 178
1. func serverRun(cmd *cobra.Command, args []string) { r := gin.Default() ! r.GET(&quot;/ping&quot;, func(c *gin.Context) { c.String(200, &quot;pong&quot;) }) ! port := viper.GetString(&quot;port&quot;) fmt.Println(&quot;Running on port:&quot;, port) r.Run(&quot;:&quot; + port) } server.go  (3) 179
1. ❯ go run dagobah.go server Running  it 180
1. Check  it  out http://localhost:1138 181
1. Tweet  Break I wrote a webserver in go using Gin   with @spf13 at #OSCON http://j.mp/gin-go
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step5 183
1. Step  6     Building  a    Dynamic  Server 184
1. Binary  Problem? •Go ships as a single binary •Need to load files from within the binary •Don’t want to embed by hand 185
1. go.rice •Nicely allows local loads in dev, and embedded loads when executing binary •Stable, but not very mature yet •Best option I know of 186
1. go get -u   github.com/GeertJohan/ go.rice Getting  Go.Rice 187
1. Serving   Static  Files 188
1. Get  your   static  &amp;   templates  on c.spf13.com/OSCON/step6-static.zip 189
1. import ( &quot;fmt&quot; &quot;html/template&quot; &quot;log&quot; &quot;net/http&quot; ! &quot;github.com/GeertJohan/go.rice&quot; &quot;github.com/gin-gonic/gin&quot; &quot;github.com/spf13/cobra&quot; &quot;github.com/spf13/viper&quot; ) server.go 190
1. func serverRun(cmd *cobra.Command, args []string) { ...  r.GET(&quot;/static/*filepath&quot;, staticServe) ! port := viper.GetString(&quot;port&quot;) fmt.Println(&quot;Running on port:&quot;, port) r.Run(&quot;:&quot; + port) } server.go 191
1. func staticServe(c *gin.Context) { static, err := rice.FindBox(&quot;static&quot;) if err != nil { log.Fatal(err) } ! original := c.Request.URL.Path c.Request.URL.Path = c.Params.ByName(&quot;filepath&quot;) fmt.Println(c.Params.ByName(&quot;filepath&quot;)) http.FileServer(static.HTTPBox()).ServeHTTP(c.Writer, c.Request) c.Request.URL.Path = original } server.go 192
1. Loading  &amp;   Serving     Templates 193
1. func loadTemplates(list ...string) *template.Template { templateBox, err := rice.FindBox(&quot;templates&quot;) if err != nil { log.Fatal(err) } templates := template.New(&quot;&quot;) ! for _, x := range list { templateString, err := templateBox.String(x) if err != nil { log.Fatal(err) } ! // get file contents as string _, err = templates.New(x).Parse(templateString) if err != nil { log.Fatal(err) } } return templates } server.go 194
1. func serverRun(cmd *cobra.Command, args []string) { r := gin.Default() templates := loadTemplates(&quot;full.html&quot;) r.SetHTMLTemplate(templates) ! r.GET(&quot;/ping&quot;, func(c *gin.Context) { c.String(200, &quot;pong&quot;) }) ! r.GET(&quot;/&quot;, homeRoute) r.GET(&quot;/static/*filepath&quot;, staticServe)  ! port := viper.GetString(&quot;port&quot;) fmt.Println(&quot;Running on port:&quot;, port) r.Run(&quot;:&quot; + port) } server.go 195
1. func homeRoute(c *gin.Context) { obj := gin.H{&quot;title&quot;: &quot;Go Rules&quot;} c.HTML(200, “full.html&quot;, obj) } server.go 196
1. ❯ go run dagobah.go server Running  it 197
1. Check  it  out http://localhost:1138 198
1. Tweet  Break No more mr rice guy   with @spf13 at #OSCON http://j.mp/go-rice
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step6 200
1. Step  7     Connecting  the  Data   to  The  templates 201
1. Go  Templates •Really nice to work with •Very simple, yet very powerful •Safe •Go Template Primer 202
1. Understanding    the  data 203
1. &gt; db.items.find().sort({ &quot;date&quot; : -1 }).limit(1).pretty() { &quot;_id&quot; : ObjectId(&quot;53b4c08bddbc460a933cf3ed&quot;), &quot;date&quot; : ISODate(&quot;2014-07-01T00:00:00Z&quot;), &quot;key&quot; : &quot;http://spf13.com/post/go-pointers-vs-references&quot;, &quot;channelkey&quot; : &quot;Recent Content on Hacking Management&quot;, &quot;title&quot; : &quot;Pointers vs References&quot;, &quot;links&quot; : [ { &quot;href&quot; : &quot;http://spf13.com/post/go-pointers-vs-references&quot;, &quot;rel&quot; : &quot;&quot;, &quot;type&quot; : &quot;&quot;, &quot;hreflang&quot; : &quot;&quot; } Looking  at  the  Schema 204
1. Listing  POsts 205
1. passing  data     into  the  template •Go’s templates accept a variety of data types •Gin’s default is ‘H’ : map[string]interface{} •Feels natural •All (exported) methods bound to values in the map are accessible inside the template 206
1. func homeRoute(c *gin.Context) { var posts []Itm results := Items().Find(bson.M{}).Sort(&quot;-date&quot;).Limit(20) results.All(&amp;posts) ! obj := gin.H{&quot;title&quot;: &quot;Go Rules&quot;, &quot;posts&quot;: posts} c.HTML(200, &quot;full.html&quot;, obj) } server.go 207
1. ... &lt;section id=&quot;latest-list&quot; class=&quot;ui divided inbox selection list active tab&quot; data-tab=&quot;recent&quot;&gt; {{ range $item := .posts }} {{ if $item.WorthShowing }} &lt;a class=&quot;item&quot; href=“#{{$item.Key | urlquery }}&quot;&gt; &lt;div class=&quot;description&quot;&gt;{{ $item.Title }}&lt;/div&gt; &lt;div class=&quot;right floated ui label small&quot;&gt;{{ $item.Date.Format &quot;Jan 2, 2006&quot; }}&lt;/div&gt; &lt;/a&gt; {{ end }} {{ end }} &lt;/section&gt; ... Full.html 208
1. Adding  Helpers    to  itm 209
1. func (i Itm) FirstLink() (link rss.Link) { if len(i.Links) == 0 || i.Links[0] == nil { return } return *i.Links[0] } ! func (i Itm) WorthShowing() bool { if len(i.FullContent) &gt; 100 { return true } return false } fetch.go 210
1. displaying  POsts 211
1. ... &lt;main&gt; {{ with .message}}! &lt;h1 class=&quot;ui header large&quot;&gt; {{.}} &lt;/h1&gt;! {{ end }}! ! {{ range $item := .posts }}! {{ if $item.WorthShowing }}! &lt;article data-key=&quot;{{$item.Key}}&quot;&gt;! &lt;header&gt;! &lt;a name=&quot;{{$item.Key}}&quot;&gt;! &lt;h1 class=&quot;ui header&quot;&gt;{{$item.Title}}&lt;/h1&gt;! &lt;section class=&quot;meta-tags&quot;&gt;! &lt;a class=&quot;ui label large blue author&quot; href=&quot;/channel/{{$item.ChannelKey}}&quot;&gt;{{$item.Author.Name}}&lt;/a&gt;! &lt;span class=&quot;large ui label date&quot;&gt;{{ $item.Date.Format &quot;Jan 2, 2006&quot; }}&lt;/span&gt;! &lt;/section&gt;! &lt;/header&gt;! &lt;section class=&quot;main-content&quot;&gt;! {{$item.FullContent | html }}! &lt;/section&gt;! &lt;footer&gt;! {{with $item.FirstLink}}! &lt;a class=&quot;ui basic button&quot; href=&quot;{{.Href}}&quot;&gt;Source&lt;/a&gt;! {{end}}! &lt;div class=&quot;ui divider&quot;&gt;&lt;/div&gt;! &lt;/footer&gt;! &lt;/article&gt;! {{ end }}! {{ else }}! No Articles! {{ end }}! &lt;/main&gt; ... full.html 212
1. Adding  Template   Functions 213
1. func loadTemplates(list ...string) *template.Template { templateBox, err := rice.FindBox(&quot;templates&quot;) if err != nil { log.Fatal(err) } ! templates := template.New(&quot;&quot;) ! for _, x := range list { templateString, err := templateBox.String(x) if err != nil { log.Fatal(err) } ! // get file contents as string _, err = templates.New(x).Parse(templateString) if err != nil { log.Fatal(err) } } ! funcMap := template.FuncMap{ &quot;html&quot;: ProperHtml, &quot;title&quot;: func(a string) string { return strings.Title(a) }, } ! templates.Funcs(funcMap) ! return templates } server.go 214
1. func ProperHtml(text string) template.HTML { if strings.Contains(text, &quot;content:encoded&gt;&quot;) || strings.Contains(text, &quot;content/:encoded&gt;&quot;) { text = html.UnescapeString(text) } return template.HTML(html.UnescapeString(template.HTMLEscapeString(text))) } server.go 215
1. Looking  Good http://localhost:1138 216
1. Tweet  Break Conquering Go Templates   with @spf13 at #OSCON
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step7 218
1. Step  8     More  Routes 219
1. Adding  Helpers 220
1. func (c Chnl) HomePage() string { if len(c.Links) == 0 { return &quot;&quot; } ! url, err := url.Parse(c.Links[0].Href) if err != nil { log.Println(err) } return url.Scheme + &quot;://&quot; + url.Host } fetch.go 221
1. ! func four04(c *gin.Context, message string) { c.HTML(404, &quot;full.html&quot;, gin.H{&quot;message&quot;: message, &quot;title&quot;: message}) } server.go 222
1. func AllChannels() []Chnl { var channels []Chnl r := Channels().Find(bson.M{}).Sort(&quot;-lastbuilddate&quot;) r.All(&amp;channels) return channels } MongoDB.go 223
1. Listing  channels 224
1. func homeRoute(c *gin.Context) { var posts []Itm results := Items().Find(bson.M{}).Sort(&quot;-date&quot;).Limit(20) results.All(&amp;posts) ! obj := gin.H{&quot;title&quot;: &quot;Go Rules&quot;,   &quot;posts&quot;: posts, &quot;channels&quot;: AllChannels()} c.HTML(200, &quot;full.html&quot;, obj) } server.go 225
1. ... &lt;section id=&quot;channel-list&quot;   class=&quot;ui large inverted vertical menu tab&quot; data-tab=“channels&quot;&gt; &lt;a class=&quot;item js-navigate&quot; href=&quot;/&quot; &gt;! &lt;i class=&quot;external home icon&quot;&gt;&lt;/i&gt;! &lt;span class=&quot;ui name&quot; href=&quot;&quot;&gt; All &lt;/span&gt;! &lt;/a&gt;! {{ range $channel := .channels }}! &lt;div class=&quot;item js-navigate-channel&quot; data-href=&quot;/channel/{{$channel.Key}}&quot;   data-key=&quot;{{$channel.Key}}&quot; style=&quot;cursor:pointer;&quot;&gt;! &lt;a href=&quot;{{$channel.HomePage}}&quot; class=&quot;ui float right&quot;&gt;&lt;i class=&quot;external url sign icon&quot;&gt;&lt;/i&gt;&lt;/a&gt;! &lt;span class=&quot;ui name&quot; href=&quot;&quot;&gt; {{$channel.Title}} &lt;/span&gt;! &lt;span class=&quot;ui label&quot;&gt;{{ len $channel.Links }}&lt;/span&gt;! &lt;/div&gt;! {{end}}! &lt;/section&gt; ... full.html 226
1. displaying   channels 227
1. func serverRun(cmd *cobra.Command, args []string) { ... r.GET(&quot;/channel/*key&quot;, channelRoute) r.Run(&quot;:&quot; + port) } server.go 228
1. func channelRoute(c *gin.Context) { key := c.Params.ByName(&quot;key&quot;) if len(key) &lt; 2 { four04(c, &quot;Channel Not Found&quot;) return } ! key = key[1:] ! fmt.Println(key) ! var posts []Itm results := Items().Find(bson.M{&quot;channelkey&quot;: key}).Sort(&quot;-date&quot;).Limit(20) results.All(&amp;posts) ! if len(posts) == 0 { four04(c, &quot;No Articles&quot;) return } ... server.go  -  pt  1 229
1. ...  var currentChannel Chnl err := Channels().Find(bson.M{&quot;key&quot;: key}).One(&amp;currentChannel) if err != nil { if string(err.Error()) == &quot;not found&quot; { four04(c, &quot;Channel not found&quot;) return } else { fmt.Println(err) } } ! obj := gin.H{&quot;title&quot;: currentChannel.Title, &quot;header&quot;: currentChannel.Title, &quot;posts&quot;: posts, &quot;channels&quot;: AllChannels()} ! c.HTML(200, &quot;full.html&quot;, obj) } server.go  -  pt  2 230
1. displaying    A  post 231
1. func serverRun(cmd *cobra.Command, args []string) { ... r.GET(&quot;/post/*key&quot;, channelRoute) r.Run(&quot;:&quot; + port) } server.go 232
1. func postRoute(c *gin.Context) { key := c.Params.ByName(&quot;key&quot;) ! if len(key) &lt; 2 { four04(c, &quot;Invalid Post&quot;) return } ! key = key[1:] ! var ps []Itm r := Items().Find(bson.M{&quot;key&quot;: key}).Sort(&quot;-date&quot;).Limit(1) r.All(&amp;ps) ! if len(ps) == 0 { four04(c, &quot;Post not found&quot;) return } ... server.go  -  Pt  1 233
1. ...  ! var posts []Itm results := Items().Find(bson.M{&quot;date&quot;: bson.M{&quot;$lte&quot;: ps[0].Date}}).Sort(&quot;-date&quot;).Limit(20) results.All(&amp;posts) ! obj := gin.H{&quot;title&quot;: ps[0].Title, &quot;posts&quot;: posts, &quot;channels&quot;: AllChannels()} ! c.HTML(200, &quot;full.html&quot;, obj) } server.go  -  Pt  2 234
1. Looking  Good http://localhost:1138 235
1. Tweet  Break Making my own planet in #go with @spf13  at #OSCON http://j.mp/go-planet
1. https:// github.com/spf13/ firstGoApp- Planet/tree/ step8 237
1. Step  9     Advanced  Routes 238
1. Congrats •You’ve made it really far •Now the training wheels are off •Let’s try to add pagination &amp; search 240
1. Hints •You will need a new index •We’re talking full text here •You will also need a new route 241
1. ... r.GET(&quot;/&quot;, homeRoute) r.GET(&quot;/post/*key&quot;, postRoute) r.GET(&quot;/search/*query&quot;, searchRoute) r.GET(&quot;/static/*filepath&quot;, staticServe) r.GET(&quot;/channel/*key&quot;, channelRoute) ... server.go 242
1. Step  10   ! Add  Polish 243
1. What’s  next  ? •Add ‘truncate’ command to remove old posts and channels •Change root command to run fetcher &amp; server •Add infinite scroll capabilities 244
1. What’s  next  ? •Make it so users can provide their own static files &amp; templates •Documentation •Blog posts 245
1. In  Conclusion 246 Go mascot designed by Ren&#233;e French and copyrighted under the Creative Commons Attribution 3.0 license.
1. Thank  yOU 247
1. What  have  we  done  ? •Written our first lines of Go •Written our first Go package •Written our own web server •Written our first Go application •Learned a lot &amp; had fun doing it 248
1. @spf13 •Author of Hugo, Cobra, Viper &amp; More •Chief Developer Advocate for MongoDB •Gopher 249

