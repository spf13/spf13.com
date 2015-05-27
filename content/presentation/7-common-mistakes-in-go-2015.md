---
date: 2015-05-27T12:28:12-07:00
description: ""
tags:
- go
- development
title: 7 common mistakes in Go (2015)
topics:
- Development
- golang
---

Given at [GopherFest 2015](http://www.meetup.com/golangsf/events/220935959/). This is an updated version of the talk I gave in NYC
Nov 14 at GothamGo.

“We need to think about failure differently. Most people think mistakes are a
necessary evil. Mistakes aren't a necessary evil, they aren't evil at all. They
are an inevitable consequence of doing something new and as such should be seen
as valuable. “ - Ed Catmull 

As Go is a "new" programming language we are all experimenting and learning how
to write better Go. While most presentations focus on the destination, this
presentation focuses on the journey of learning Go and the mistakes I
personally made while developing Hugo, Cobra, Viper, Afero & Docker.

{{% slideshare 48640688 %}}

## Transcript

1. 7 and when to avoid them Common  Mistakes   In Go
2. @Spf13 Docker   Chief Operator  & Author of Hugo, Cobra, Afero, Viper 
3. image of “F” on a paper
4. “Do you want to know the difference between a master and a beginner? The master has failed more times than the beginner has tried.”
5. –Ed Catmull “We need to think about failure differently. Most people think mistakes are a necessary evil. Mistakes aren't a necessary evil, they aren't evil at all. They are an inevitable consequence of doing something new and as such should be seen as valuable. “
6. Mistake .     Not Accepting Interfaces 1
7. State & Behavior •Types can express state & behavior •State = data structure •Behavior = methods
8. Interfaces •One of Go’s most powerful features •Permits extensibility •Deﬁned by methods •Adherence is only satisﬁed by behavior
9. •Fastest static site generator •Native Go •35+ themes •Flexible •100s of contributors •Powers GopherAcademy gohugo.io
10. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b.Bytes(), path) } func (page *Page) saveSource(by []byte, inpath string) { WriteToDisk(inpath, bytes.NewReader(by)) } Stop Doing This!!
11. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b.Bytes(), path) } func (page *Page) saveSource(by []byte, inpath string) { WriteToDisk(inpath, bytes.NewReader(by)) } Stop Doing This!!
12. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b.Bytes(), path) } func (page *Page) saveSource(by []byte, inpath string) { WriteToDisk(inpath, bytes.NewReader(by)) } Stop Doing This!! https://github.com/spf13/hugo/blob/master/hugolib/page.go#L582
13. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b, path) } func (page *Page) saveSource(b io.Reader, inpath string) { WriteToDisk(inpath, b) } Instead
14. Mistake .     Not Using Io.Reader & Io.Writer 2
15. Io.Reader & Io.Writer •Simple & ﬂexible interfaces for many operations around input and output •Provides access to a huge wealth of functionality •Keeps operations extensible
16. type Reader interface { Read(p []byte) (n int, err error) } type Writer interface { Write(p []byte) (n int, err error) } Io.Reader & Io.Writer
17. Cobra Cli Commander •Fast and ﬂexible •Powers   Kubernetes & Hugo •Provides subcommands, help, man pages, bash autocomplete github.com/spf13/cobra
18. // SetOutput sets the destination for usage and error messages. // If output is nil, os.Stderr is used. func (c *Command) SetOutput(o io.Writer) { c.output = o } Cobra Apps Enabled
19. Viper •Conﬁguration management •Supports json, yaml, toml, defaults, ﬂags, env vars & remote key value •Supports nesting, cascading & aliases github.com/spf13/viper
20. func (v *Viper) ReadBufConfig(buf *bytes.Buffer) error { v.config = make(map[string]interface{}) v.marshalReader(buf, v.config) return nil } Really Stop Doing This!!
21. func (v *Viper) ReadConfig(in io.Reader) error { v.config = make(map[string]interface{}) v.marshalReader(in, v.config) return nil } Instead
22. Mistake .    Requiring Broad Interfaces 3
23. Interfaces Are Composable •Functions should only accept interfaces that require the methods they need •Functions should not accept a broad interface when a narrow one would work •Compose broad interfaces made from narrower ones
24. Afero Fs •File system abstraction •Uses standard OS interfaces •Drop in replacement for OS •Great for testing & mocking •Cross platform memory backed ﬁlesystem github.com/spf13/afero
25. type File interface { io.Closer io.Reader io.ReaderAt io.Seeker io.Writer io.WriterAt } Composing Interfaces
26. func ReadIn(f File) { b := []byte{} n, err := f.Read(b) ... } Requiring Broad Interfaces
27. func ReadIn(r Reader) { b := []byte{} n, err := r.Read(b) ... } Requiring Narrow Interfaces
28. Mistake .    Methods Vs Functions 4
29. Too Many Methods •A lot of people from OO backgrounds overuse methods •Natural draw to deﬁne everything via structs and methods
30. What Is A Function? •Operations performed on N1 inputs that results in N2 outputs •The same inputs will always result in the same outputs •Functions should not depend on state
31. What Is A Method? •Deﬁnes the behavior of a type •A function that operates against a value •Should use state •Logically connected
32. Functions Can Be Used With Interfaces •Methods, by deﬁnition, are bound to a speciﬁc type •Functions can accept interfaces as input
33. func extractShortcodes(s string, p *Page, t Template) (string, map[string]shortcode, error) { ... for { switch currItem.typ { ... case tError: err := fmt.Errorf("%s:%d: %s", p.BaseFileName(), (p.lineNumRawContentStart() + pt.lexer.lineNum() - 1), currItem) } } ... } Example From Hugo
34. func extractShortcodes(s string, p *Page, t Template) (string, map[string]shortcode, error) { ... for { switch currItem.typ { ... case tError: err := fmt.Errorf("%s:%d: %s", p.BaseFileName(), (p.lineNumRawContentStart() + pt.lexer.lineNum() - 1), currItem) } } ... } Example From Hugo
35. Mistake .     Pointers Vs Values 5
36. Pointers Vs Values •It’s not a question of performance (generally), but one of shared access •If you want to share the value with a function or method, then use a pointer •If you don’t want to share it, then use a value (copy)
37. func (page *Page) saveSource(b io.Reader)  func (page Page) saveSource(b io.Reader) Pointer Vs Value Receivers
38. Pointer Receivers •If you want to share a value with it’s method, use a pointer receiver •Since methods commonly manage state, this is the common usage •Not safe for concurrent access
39. Value Receivers •If you want the value copied (not shared), use values •If the type is an empty struct (stateless, just behavior)… then just use value •Safe for concurrent access
40. type InMemoryFile struct { at int64 name string data []byte closed bool } func (f *InMemoryFile) Close() error { atomic.StoreInt64(&f.at, 0) f.closed = true return nil } Afero File
41. type Time struct { sec int64 nsec uintptr loc *Location } func (t Time) IsZero() bool { return t.sec == 0 && t.nsec == 0 } Time
42. Mistake .     Thinking Of Errors As Strings 6
43. type error interface { Error() string } Error Is An Interface
44. Standard Errors •errors.New(“error here”) is usually sufﬁcient •Exported Error Variables can be easily checked
45. func NewPage(name string) (p *Page, err error) { if len(name) == 0 { return nil,   errors.New("Zero length page name") }    Standard Error
46. var ErrNoName = errors.New("Zero length page name")    func NewPage(name string) (*Page, error) { if len(name) == 0 { return nil, ErrNoName }    Exported Error Var
47. var ErrNoName = errors.New("Zero length page name")    func Foo(name string) (error) { err := NewPage("bar") if err == ErrNoName { newPage("default") } else { log.FatalF(err) } }  Exported Error Var
48. Custom Errors •Can provide context to guarantee consistent feedback •Provide a type which can be different from the error value •Can provide dynamic values   (based on internal error state)
49. •Container runtime & image format •Native Go •22k stars •1000+ contributors docker.com
50. type Error struct { Code ErrorCode Message string Detail interface{} } // Error returns a human readable representation of the error. func (e Error) Error() string { return fmt.Sprintf("%s: %s", strings.ToLower(strings.Replace(e.Code.String(), "_", " ", -1)), e.Message) } Internationalization Of Errors
51. Go StdLib •Standard Go   Libraries •Comprehensive and   powerful •Great examples of “good” Go http://golang.org/pkg/
52. // Portable analogs of some common system call errors. var ErrInvalid = errors.New("invalid argument") var ErrPermission = errors.New("permission denied") // PathError records an error and // the operation and file path that caused it. type PathError struct { Op string Path string Err error } func (e *PathError) Error() string { return e.Op + " " + e.Path + ": " + e.Err.Error() } Custom Errors : Os
53. // Portable analogs of some common system call errors. var ErrInvalid = errors.New("invalid argument") var ErrPermission = errors.New("permission denied") // PathError records an error and // the operation and file path that caused it. type PathError struct { Op string Path string Err error } func (e *PathError) Error() string { return e.Op + " " + e.Path + ": " + e.Err.Error() } Custom Errors : Os
54. func (f *File) WriteAt(b []byte, off int64) (n int, err error) { if f == nil { return 0, ErrInvalid } for len(b) > 0 { m, e := f.pwrite(b, off) if e != nil { err = &PathError{"write", f.name, e} break } n += m b = b[m:] off += int64(m) } return } Custom Errors : Os
55. func (f *File) WriteAt(b []byte, off int64) (n int, err error) { if f == nil { return 0, ErrInvalid } for len(b) > 0 { m, e := f.pwrite(b, off) if e != nil { err = &PathError{"write", f.name, e} break } n += m b = b[m:] off += int64(m) } return } Custom Errors : Os
56. func (f *File) WriteAt(b []byte, off int64) (n int, err error) { if f == nil { return 0, ErrInvalid } for len(b) > 0 { m, e := f.pwrite(b, off) if e != nil { err = &PathError{"write", f.name, e} break } n += m b = b[m:] off += int64(m) } return } Custom Errors : Os
57. func baa(f *file) error { … n, err := f.WriteAt(x, 3) if _, ok := err.(*PathError) { …  } else { log.Fatalf(err) } } Custom Errors : Os
58. … if serr != nil { if serr, ok := serr.(*PathError); ok && serr.Err == syscall.ENOTDIR { return nil } return serr … Custom Errors : Os
59. … if serr != nil { if serr, ok := serr.(*PathError); ok && serr.Err == syscall.ENOTDIR { return nil } return serr … Custom Errors : Os
60. Mistake .     To Be Safe Or Not To Be 7
61. You Can’t Make Everyone Happy  You Aren’t A Jar Of Nutella
62. Consider Concurrency •If you provide a library someone will use it concurrently •Data structures are not safe for concurrent access •Values aren’t safe, you need to create safe behavior around them
63. Making It Safe •Sync package provides behavior to make a value safe (Atomic/ Mutex) •Channels coordinate values across go routines by permitting one go routine to access at a time
64. func (m *MMFS) Create(name string) (File, error) { m.getData()[name] = MemFileCreate(name) m.registerDirs(m.getData()[name]) return m.getData()[name], nil } Maps Are Not Safe
65. func (m *MMFS) Create(name string) (File, error) { m.getData()[name] = MemFileCreate(name) m.registerDirs(m.getData()[name]) return m.getData()[name], nil } Maps Are Not Safe
66. panic: runtime error: invalid memory address or nil pointer dereference [signal 0xb code=0x1 addr=0x28 pc=0x1691a7] goroutine 90 [running]: runtime.panic(0x501ea0, 0x86b104) /usr/local/Cellar/go/1.3.3/libexec/src/pkg/runtime/ panic.c:279 +0xf5 github.com/spf13/afero. (*MemMapFs).registerDirs(0xc208000860, 0x0, 0x0) /Users/spf13/gopath/src/github.com/spf13/afero/ memmap.go:88 +0x27 Maps Are Not Safe
67. func (m *MMFS) Create(name string) (File, error) { m.lock() m.getData()[name] = MemFileCreate(name) m.unlock() m.registerDirs(m.getData()[name]) return m.getData()[name], nil } Safe Maps With Mutex
68. Keeping It Unsafe •Safety comes at a cost •Imposes behaviors on consumer •Proper API allows consumers to add safety as needed •Consumers can use channels or mutexes
69. func (m *MMFS) Create(name string) (File, error) { m.lock() m.getData()[name] = MemFileCreate(name) m.unlock() m.registerDirs(m.getData()[name]) return m.getData()[name], nil } Safe Maps With Mutex
70. Maps Are Unsafe By Design •Often safety is unnecessary •Enables consumers to implement safety as needed •Enables consumers to implement safety as desired
71. Biggsest Mistake; Not Makimg Mistakes
72. –Ed Catmull Failure is a manifestation of learning and exploration.     If you aren't experiencing failure than you are making a far worse mistake.     You are being driven by the desire to avoid it.
73. @Spf13 Docker   Chief of Operations  & Author of Hugo, Cobra, Afero, Viper 
