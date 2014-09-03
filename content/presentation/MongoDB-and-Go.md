+++
description = "This presentation will give developers an introduction and practical experience of using MongoDB with the Go language. MongoDB Chief Developer Advocate & Gopher Steve Francia presents plainly what you need to know about using MongoDB with Go."
tags = ["go", "development", "mongodb", "mgo"]
title = "Using MongoDB with Go and mgo"
topics = ["Development", "golang", "mongodb"]
date = 2014-07-23T09:48:46Z
+++

This presentation was given at OSCON 2014.

{{% slideshare 37542643 %}}

This presentation will give developers an introduction and practical experience
of using MongoDB with the Go language. MongoDB Chief Developer Advocate &
Gopher Steve Francia presents plainly what you need to know about using MongoDB
with Go.

As an emerging language Go is able to start fresh without years of relational database dependencies. Application and library developers are able to build applications using the excellent Mgo MongoDB driver and the reliable go sql package for relational database. Find out why some people claim Go and MongoDB are a “pair made in heaven” and “the best database driver they’ve ever used” in this talk by Gustavo Niemeyer, the author of the mgo driver, and Steve Francia, the drivers team lead at MongoDB Inc. 

We will cover: 

* Connecting to MongoDB in various configurations 
* Performing basic operations in Mgo 
* Marshaling data to and from MongoDB 
* Asynchronous & Concurrent operations 
* Pre-fetching batches for seamless performance 
* Using GridFS 
* How MongoDB uses Mgo internally

## Presentation Transcript

1. Painless Data Storage with MongoDB & Go
1. • Author of Hugo, Cobra, Viper & More • Chief Developer Advocate for MongoDB • Gopher @spf13
1. Why Go?
1. Why Another Language? • Software is slow • Sofware is hard to write • Software doesn’t scale well
1. Go is Fast • Go execution speed is close to C • Go compile time rivals dynamic interpretation
1. Go is Friendly • Feels like a dynamic language in many ways • Very small core language, easy to remember all of it • Single binary installation, no dependencies • Extensive Tooling & StdLib
1. Go is Concurrent • Concurrency is part of the language • Any function can become a goroutine • Goroutines run concurrently, communicate through channels • Select waits for communication on any of a set of channels
1. MongoDB
1. Why Another Database? • Databases are slow • Relational structures don’t ﬁt well with modern programming (ORMs) • Databases don’t scale well
1. MongoDB is Fast • Written in C++ • Extensive use of memory-mapped ﬁles   i.e. read-through write-through memory caching. • Runs nearly everywhere • Data serialized as BSON (fast parsing) • Full support for primary & secondary indexes • Document model = less work
1. MongoDB is Friendly • Ad Hoc queries • Real time aggregation • Rich query capabilities • Traditionally consistent • Geospatial features • Support for most programming languages • Flexible schema
1. MongoDB is “Web Scale” • Built in sharding support distributes data across many nodes • MongoS intelligently routes to the correct nodes • Aggregation done in parallel across nodes
1. Document Database • Not for .PDF & .DOC ﬁles • A document is essentially an associative array • Document == JSON object • Document == PHP Array • Document == Python Dict • Document == Ruby Hash • etc
1. Data Serialization • Applications need persistant data • The process of translating data structures into a format that can be stored • Ideal format accessible from many languages
1. BSON • Inspired by JSON • Cross language binary serialization format • Optimized for scanning • Support for richer types
1. MongoDB & Go
1. Go’s Data Types • Go uses strict & static typing • 2 Types are similar to a BSON document • Struct • Map
1. bob := &Person{ Name: "Bob", Birthday: time.Now(), } ! data, err := bson.Marshal(bob) if err != nil { return err } fmt.Printf("Data: %qn", data)  ! var person Person err = bson.Unmarshal(data, &person) if err != nil { return err } fmt.Printf("Person: %vn", person) Serializing with BSON
1. bob := &Person{ Name: "Bob", Birthday: time.Now(), } ! data, err := bson.Marshal(bob) if err != nil { return err } fmt.Printf("Data: %qn", data)  ! var person Person err = bson.Unmarshal(data, &person) if err != nil { return err } fmt.Printf("Person: %vn", person) Serializing with BSON
1. bob := &Person{ Name: "Bob", Birthday: time.Now(), } ! data, err := bson.Marshal(bob) if err != nil { return err } fmt.Printf("Data: %qn", data)  ! var person Person err = bson.Unmarshal(data, &person) if err != nil { return err } fmt.Printf("Person: %vn", person) Serializing with BSON
1. bob := &Person{ Name: "Bob", Birthday: time.Now(), } ! data, err := bson.Marshal(bob) if err != nil { return err } fmt.Printf("Data: %qn", data)  ! var person Person err = bson.Unmarshal(data, &person) if err != nil { return err } fmt.Printf("Person: %vn", person) Serializing with BSON
1. bob := &Person{ Name: "Bob", Birthday: time.Now(), } ! data, err := bson.Marshal(bob) if err != nil { return err } fmt.Printf("Data: %qn", data)  ! var person Person err = bson.Unmarshal(data, &person) if err != nil { return err } fmt.Printf("Person: %vn", person) Serializing with BSON
1. bob := &Person{ Name: "Bob", Birthday: time.Now(), } ! data, err := bson.Marshal(bob) if err != nil { return err } fmt.Printf("Data: %qn", data)  ! var person Person err = bson.Unmarshal(data, &person) if err != nil { return err } fmt.Printf("Person: %vn", person) Serializing with BSON Data: "%x00x00x00x02name x00x04x00x00x00Bob x00tbirthdayx00x80rx97| ^x00x00x00x00"  ! Person: {Bob 2014-07-21 18:00:00 -0500 EST}
1. ! type Project struct { Name string `bson:"name"` ImportPath string `bson:"importPath"` } project := Project{name, path} ! ! ! project := map[string]string{"name": name, "importPath": path} ! ! ! project := bson.D{{"name", name}, {"importPath", path}} Equal After Marshaling Struct Custom Map Document Slice
1. mgo (mango) • Pure Go • Created in late 2010   ("Where do I put my Go data?") • Adopted by Canonical and MongoDB Inc. itself • Sponsored by MongoDB Inc. from late 2011
1. Connecting
1. • Same interface for server, replica set, or shard • Driver discovers and maintains topology • Server added/removed, failovers, response times, etc Connecting session, err := mgo.Dial("localhost") if err != nil { return err }
1. • Sessions are lightweight • Sessions are copied (settings preserved) • Single management goroutine for all copied sessions Sessions func (s *Server) handle(w http.ResponseWriter, r *http.Request) { session := s.session.Copy() defer session.Close() // ... handle request ... }
1. • Saves typing • Uses the same session over and over Convenient Access projects := session.DB("OSCON").C("projects")
1. Writing
1. type Project struct { Name string `bson:"name,omitempty"` ImportPath string `bson:"importPath,omitempty"` } Deﬁning Our Own Type
1. var projectList = []Project{ {"gocheck", "gopkg.in/check.v1"}, {"qml", "gopkg.in/qml.v0"}, {"pipe", "gopkg.in/pipe.v2"}, {"yaml", "gopkg.in/yaml.v1"}, } ! for _, project := range projectList { err := projects.Insert(project) if err != nil { return err } } fmt.Println("Okay!") Insert Okay!
1. type M map[string]interface{} ! change := M{"$set": Project{ImportPath: "gopkg.in/ qml.v1"}} ! err = projects.Update(Project{Name: "qml"}, change) if err != nil { return err } ! fmt.Println("Done!") Update Done!
1. Querying
1. var project Project ! err = projects.Find(Project{Name: "qml"}).One(&project) if err != nil { return err } ! fmt.Printf("Project: %vn", project) Find Project:   {qml gopkg.in/qml.v0}
1. iter := projects.Find(nil).Iter() ! var project Project for iter.Next(&project) { fmt.Printf("Project: %vn", project) } ! return iter.Err() Iterate Project: {gocheck gopkg.in/check.v1} Project: {qml gopkg.in/qml.v0} Project: {pipe gopkg.in/pipe.v2} Project: {yaml gopkg.in/yaml.v1}
1. m := map[string]interface{}{ "name": "godep", "tags": []string{"tool", "dependency"}, "contact": bson.M{ "name": "Keith Rarick", "email": "kr@nospam.com", }, } ! err = projects.Insert(m) if err != nil { return err } fmt.Println("Okay!") Nesting Okay!
1. type Contact struct { Name string Email string } ! type Project struct { Name string Tags []string `bson:",omitempty"` Contact Contact `bson:",omitempty"` } ! err = projects.Find(Project{Name: "godep"}).One(&project) if err != nil { return err } ! pretty.Println("Project:", project) Nesting II Project: main.Project{ Name: "godep", Tags: {"tool", "dependency"}, Contact: {Name:"Keith Rarick", Email:"kr@XZY.com"}, }
1. • Compound • List indexing (think tag lists) • Geospatial • Dense or sparse • Full-text searching Indexing // Root field err = projects.EnsureIndexKey("name") ... ! // Nested field err = projects.EnsureIndexKey("author.email") ...
1. Concurrency
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent
1. func f(projects *mgo.Collection, name string, done chan error) { var project Project err := projects.Find(Project{Name: name}).One(&project) if err == nil { fmt.Printf("Project: %vn", project) } done <- err } ! done := make(chan error) ! go f(projects, "qml", done) go f(projects, "gocheck", done) ! if err = firstError(2, done); err != nil { return err } Concurrent Project: {qml gopkg.in/qml.v1} Project: {gocheck gopkg.in/ check.v1}
1. • Find 1 issued  • Doc 1 returned • Find 2 issued  • Doc 2 returned A Common Approach Find 1 Find 2 DB } }
1. • Find 1 issued • Find 2 issued  • Doc 1 returned • Doc 2 returned Concurrent Queries Find 1 Find 2 DB } }
1. • Loads 200 results at a time • Loads next batch with (0.25 * 200) results left to process Concurrent Loading session.SetBatch(200) session.SetPrefetch(0.25) ! for iter.Next(&result) { ... }
1. • Each Copy uses a different connection • Closing session returns socket to the pool • defer runs at end of function Handler With Session Copy func (s *Server) handle(w http.ResponseWriter, r *http.Request) { session := s.session.Copy() defer session.Close() ! // ... handle request ... }
1. • Shares a single connection • Still quite efﬁcient thanks to concurrent capabilities of go + mgo Handler With Single Session func (s *Server) handle(w http.ResponseWriter, r *http.Request) { session := s.session ! // ... handle request ... }
1. GridFS
1. GridFS • Not quite a ﬁle system • Really useful for local ﬁle storage • A convention, not a feature • Supported by all drivers • Fully replicated, sharded ﬁle storage
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS
1. gridfs := session.DB("OSCON").GridFS("fs") ! file, err := gridfs.Create("cd.iso") if err != nil { return err } defer file.Close() ! started := time.Now() ! _, err = io.Copy(file, iso) if err != nil { return err } ! fmt.Printf("Wrote %d bytes in %sn", file.Size(), time.Since(started)) GridFS ! Wrote 470386961 bytes in 7.0s
1. Full Featured
1. Features • Transactions (mgo/txn experiment) • Aggregation pipelines • Full-text search • Geospatial support • Hadoop
1. In Conclusion
1. Getting Started • 1. Install MongoDB • 2. go get gopkg.in/mgo.v2 • 3. Start small • 4. Build something great
1. Learning More • MongoDB Manual • Effective Go • labix.org/mgo
1. Workshop Using mgo on spf13.com
1. on spf13.com
1. • @spf13 • Author of Hugo, Cobra, Viper & More • Chief Developer Advocate for MongoDB • Gopher Thank You
