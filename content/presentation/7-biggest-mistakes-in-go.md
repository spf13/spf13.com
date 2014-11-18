---
date: 2014-11-18T14:06:00-05:00
description: ""
tags:
- go
- development
title: 7 Common mistakes in Go and when to avoid them 
topics:
- Development
- golang
---


Not a generic list of programming mistakes, these are the lessons I wish I
learned earlier while developing Go. I've spent the past two years developing
some of the most popular libraries and applications written in Go. I've also
made a lot of mistakes along the way. Recognizing that "The only real mistake
is the one from which we learn nothing. -John Powell", I would like to share
with you the mistakes that I have made over my journey with Go and when you can
avoid them.

Originally given in NYC Nov 14 at [GothamGo](http://gothamgo.com).

{{% slideshare 41716887 %}}

## Transcript

1. 7 Common Mistakes In Go and when to avoid them
2. @Spf13 Author of Hugo, Cobra, Afero, Viper & more
3. “As long as the world is turning and spinning, we're gonna be dizzy and we're gonna make mistakes.” –Mel Brooks
4. “Appreciate your mistakes for what they are: precious life lessons that can only be learned the hard way. “ –Al Franken
5. “If I had to live my life again, I'd make the same mistakes, only sooner.” – Tallulah Bankhead
6. 7 Lessons I Wish I Learned Sooner
7. Mistake 1: Not Accepting Interfaces
8. State & Behavior •Types can express state & behavior •State = data structure •Behavior = methods
9. Interfaces •One of Go’s most powerful features •Permits extensibility •Defined by methods •Adherance is only satisfied by behavior
10. Example : []Byte type Source struct { Frontmatter []byte Content []byte }
11. Func Restricted To String func StripHTML(s string) string { output := "" // Shortcut strings with no tags in them if !strings.ContainsAny(s, "<>") { output = s } else { s = strings.Replace(s, "n", " ", -1) s = strings.Replace(s, "</p>", "n", -1) s = strings.Replace(s, "<br>", "n", -1) s = strings.Replace(s, "<br />", "n", -1) …
12. Passes Implementation Details Down The Stack func (p *Page) Plain() string { return helpers.StripHTML(string(p.Content)) }
13. Any Read() Works func StripHTML(r Reader) string { buf := new(bytes.Buffer) buf.ReadFrom(r) by := buf.Bytes() if bytes.ContainsAny(s, []byte("<>")) { by = bytes.Replace(by, []byte("n"), " ", -1) by = bytes.Replace(by, []byte("</p>"), "n", -1) by = bytes.Replace(by, []byte("<br>"), "n", -1) by = bytes.Replace(by, []byte("<br />"), "n", -1) …
14. type Source struct { Frontmatter []byte content []byte } type Reader interface { Read(p []byte) (n int, err error) } func (s *Source) Content() (Reader) { return bytes.NewReader(content) } Example : Read
15. type Source struct { Frontmatter []byte content []byte } type Reader interface { Read(p []byte) (n int, err error) } func (s *Source) Content() (Reader) { return bytes.NewReader(content) } Example : Read
16. type Source struct { Frontmatter []byte content []byte } type Reader interface { Read(p []byte) (n int, err error) } func (s *Source) Content() (Reader) { return bytes.NewReader(content) } Example : Read
17. func (p *Page) Plain() string { return helpers.StripHTML(p.Content()) } Implementation Details Abstracted With A Method
18. Mistake 2: Thinking Of Errors As Strings
19. Error Is An Interface type error interface { Error() string }
20. Standard Errors •errors.New(“error here”) is usually sufficient •Exported Error Variables can be easily checked
21. Custom Errors •Can provide context to guarantee consistent feedback •Provide a type which can be different from the error value •Can provide dynamic values (based on internal error state)
22. func NewPage(name string) (p *Page, err error) { if len(name) == 0 { return nil, errors.New("Zero length page name") } Standard Error
23. Exported Error Var var ErrNoName = errors.New("Zero length page name") func NewPage(name string) (*Page, error) { if len(name) == 0 { return nil, ErrNoName }
24. Exported Error Var var ErrNoName = errors.New("Zero length page name") func Foo(name string) (error) { err := NewPage("bar") if err == ErrNoName { newPage("default") } else { log.FatalF(err) } }
25. Custom Errors : Os // Portable analogs of some common system call errors. var ErrInvalid = errors.New("invalid argument") var ErrPermission = errors.New("permission denied") // PathError records an error and // the operation and file path that caused it. type PathError struct { Op string Path string Err error } func (e *PathError) Error() string { return e.Op + " " + e.Path + ": " + e.Err.Error() }
26. Custom Errors : Os // Portable analogs of some common system call errors. var ErrInvalid = errors.New("invalid argument") var ErrPermission = errors.New("permission denied") // PathError records an error and // the operation and file path that caused it. type PathError struct { Op string Path string Err error } func (e *PathError) Error() string { return e.Op + " " + e.Path + ": " + e.Err.Error() }
27. Custom Errors : Os func (f *File) WriteAt(b []byte, off int64) (n int, err error) { if f == nil { return 0, ErrInvalid } for len(b) > 0 { m, e := f.pwrite(b, off) if e != nil { err = &PathError{"write", f.name, e} break } n += m b = b[m:] off += int64(m) } return }
28. Custom Errors : Os func (f *File) WriteAt(b []byte, off int64) (n int, err error) { if f == nil { return 0, ErrInvalid } for len(b) > 0 { m, e := f.pwrite(b, off) if e != nil { err = &PathError{"write", f.name, e} break } n += m b = b[m:] off += int64(m) } return }
29. Custom Errors : Os func (f *File) WriteAt(b []byte, off int64) (n int, err error) { if f == nil { return 0, ErrInvalid } for len(b) > 0 { m, e := f.pwrite(b, off) if e != nil { err = &PathError{"write", f.name, e} break } n += m b = b[m:] off += int64(m) } return }
30. Custom Errors : Os func baa(f *file) error { … n, err := f.WriteAt(x, 3) if _, ok := err.(*PathError) { … } else { log.Fatalf(err) } }
31. Custom Errors : Os … if serr != nil { if serr, ok := serr.(*PathError); ok && serr.Err == syscall.ENOTDIR { return nil } return serr …
32. Custom Errors : Os … if serr != nil { if serr, ok := serr.(*PathError); ok && serr.Err == syscall.ENOTDIR { return nil } return serr …
33. Mistake 3: Requring Broad Interfaces
34. Interfaces Are Composable •Functions should only accept interfaces that require the methods they need •Functions should not accept a broad interface when a narrow one would work •Compose broad interfaces made from narrower ones
35. Composing Interfaces type File interface { io.Closer io.Reader io.ReaderAt io.Seeker io.Writer io.WriterAt }
36. Requiring Broad Interfaces func ReadIn(f File) { b := []byte{} n, err := f.Read(b) ... }
37. Composing Interfaces type File interface { io.Closer io.Reader io.ReaderAt io.Seeker io.Writer io.WriterAt }
38. Requiring Narrow Interfaces func ReadIn(r Reader) { b := []byte{} n, err := r.Read(b) ... }
39. Mistake 4: Methods Vs Functions
40. Too Many Methods •A lot of people from OO backgrounds overuse methods •Natural draw to define everything via structs and methods
41. What Is A Function? •Operations performed on N1 inputs that results in N2 outputs •The same inputs will always result in the same outputs •Functions should not depend on state
42. What Is A Method? •Defines the behavior of a type •A function that operates against a value •Should use state •Logically connected
43. Functions Can Be Used With Interfaces •Methods, by definition, are bound to a specific type •Functions can accept interfaces as input
44. Example From Hugo func extractShortcodes(s string, p *Page, t Template) (string, map[string]shortcode, error) { ... for { switch currItem.typ { ... case tError: err := fmt.Errorf("%s:%d: %s", p.BaseFileName(), (p.lineNumRawContentStart() + pt.lexer.lineNum() - 1), currItem) } } ... }
45. Example From Hugo func extractShortcodes(s string, p *Page, t Template) (string, map[string]shortcode, error) { ... for { switch currItem.typ { ... case tError: err := fmt.Errorf("%s:%d: %s", p.BaseFileName(), (p.lineNumRawContentStart() + pt.lexer.lineNum() - 1), currItem) } } ... }
46. Mistake 5: Pointers Vs Values
47. Pointers Vs Values •It’s not a question of performance (generally), but one of shared access •If you want to share the value with a function or method, then use a pointer •If you don’t want to share it, then use a value (copy)
48. Pointer Receivers •If you want to share a value with it’s method, use a pointer receiver •Since methods commonly manage state, this is the common usage •Not safe for concurrent access
49. Value Receivers •If you want the value copied (not shared), use values •If the type is an empty struct (stateless, just behavior)… then just use value •Safe for concurrent access
50. Afero File type InMemoryFile struct { at int64 name string data []byte closed bool } func (f *InMemoryFile) Close() error { atomic.StoreInt64(&f.at, 0) f.closed = true return nil }
51. type Time struct { sec int64 nsec uintptr loc *Location } func (t Time) IsZero() bool { return t.sec == 0 && t.nsec == 0 } Time
52. Mistake 6: Not Using Io.Reader & Io.Writer
53. Io.Reader & Io.Writer •Simple & flexible interfaces for many operations around input and output •Provides access to a huge wealth of functionality •Keeps operations extensible
54. Io.Reader & Io.Writer type Reader interface { Read(p []byte) (n int, err error) } type Writer interface { Write(p []byte) (n int, err error) }
55. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b.Bytes(), path) } func (page *Page) saveSource(by []byte, inpath string) { WriteToDisk(inpath, bytes.NewReader(by)) } Stop Doing This!!
56. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b.Bytes(), path) } func (page *Page) saveSource(by []byte, inpath string) { WriteToDisk(inpath, bytes.NewReader(by)) } Stop Doing This!!
57. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b.Bytes(), path) } func (page *Page) saveSource(by []byte, inpath string) { WriteToDisk(inpath, bytes.NewReader(by)) } Stop Doing This!! https://github.com/spf13/hugo/blob/master/hugolib/page.go#L582
58. func (page *Page) saveSourceAs(path string) { b := new(bytes.Buffer) b.Write(page.Source.Content) page.saveSource(b, path) } func (page *Page) saveSource(b io.Reader, inpath string) { WriteToDisk(inpath, b) } Instead
59. Mistake 7: Ignoring Concurrent Access
60. Consider Concurrency •If you provide a library someone will use it concurrently •Data structures are not safe for concurrent access •Values aren’t safe, you need to create safe behavior around them
61. Making It Safe •Sync package provides behavior to make a value safe (Atomic/ Mutex) •Channels cordinate values across go routines by permitting one go routine to access at a time
62. Maps Are Not Safe func (m *MMFs) Create(name string) (File, error) { m.getData()[name] = MemFileCreate(name) m.registerDirs(m.getData()[name]) return m.getData()[name], nil }
63. Maps Are Not Safe func (m *MMFS) Create(name string) (File, error) { m.getData()[name] = MemFileCreate(name) m.registerDirs(m.getData()[name]) return m.getData()[name], nil }
64. Maps Are Not Safe panic: runtime error: invalid memory address or nil pointer dereference [signal 0xb code=0x1 addr=0x28 pc=0x1691a7] goroutine 90 [running]: runtime.panic(0x501ea0, 0x86b104) /usr/local/Cellar/go/1.3.3/libexec/src/pkg/runtime/ panic.c:279 +0xf5 github.com/spf13/afero. (*MemMapFs).registerDirs(0xc208000860, 0x0, 0x0) /Users/spf13/gopath/src/github.com/spf13/afero/ memmap.go:88 +0x27
65. Maps Can Be Used Safely func (m *MMFS) Create(name string) (File, error) { m.lock() m.getData()[name] = MemFileCreate(name) m.unlock() m.registerDirs(m.getData()[name]) return m.getData()[name], nil }
66. Biggsest Mistake: Not Makimg Mistakes
67. @Spf13 Author of Hugo, Cobra, Afero, Viper & more
