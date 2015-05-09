---
date: 2015-03-20T18:00:02-04:00
description: ""
tags:
- go
- open source
- development
title: What Every Open Source Project Needs
topics:
- Development
- golang
- Open Source
---

In the last few years open source has transformed the software industry. From
Android to Wikipedia, open source is everywhere, but how does one succeed in
it? While open source projects come in all shapes and sizes and all forms of
governance, no matter what kind of project you’re a part of, there are a set of
fundamentals that lead to success. I’d like to share some of the lessons I’ve
learned from running two of the largest commercial open source projects,
[Docker](http://docker.com) & [MongoDB](http://mongodb.org) , as well as some
very successful community based projects ([Hugo](http://gohugo.io),
[spf13-vim](http://vim.spf13.com), [Cobra](http://github.com/spf13/cobra),
[Viper](http://github.com/spf13/viper), Zoop).

This presentation was delivered at [sinfo.org](http://sinfo.org) in Feb 2015.

*Due to time constraints we only focused on 4 of the 6 principles.*

{{% slideshare 46098031 %}}

## Transcript

1. What Every Successful Open Source Project Needs
2. @spf13 Chief Operator @ Docker    Former Chief Developer Advocate @ MongoDB,   Author of Hugo, spf13- vim, Cobra, Afero, Viper & more
3. Mainframe Era :   60s & 70s • Computer companies sold hardware • Software was free • Software was colloborative • IBM dominates
4. The Software Era:   80s - 90s • Software as a business emerged • Software companies sold “bits” • Software was private and proprietary • Microsoft dominates
5. The Internet Era: 00s • Internet changes everything • Open source movement gains traction (Linux, Apache, MySQL, PHP) • Tech selling ads, bits, hardware & services • Google Dominates
6. The Free Source Era: 10s • Technology companies sell Hardware & Services • Software is becoming free ($$) (Windows 10, OS X, Android, IOS) • Game companies still sell bits • Virtually all software companies are now participating in open source
7. Open Source Companies • Redhat $13B • Cloudera $3B • MongoDB $1.6B • Docker $.5B • Hortonworks $1B • Wordpress $1B
8. Open Source Companies • Google (Android, Chrome, Docker, Linux) • Apple (Webkit, LLVM) • Facebook (Cassandra, HipHop, Hive, PHP) • IBM (Linux, Eclipse, Docker) • Yahoo (Hadoop, Linux, YUI) • Oracle (Linux, MySQL, Java) • Microsoft (Linux, .net, Docker) • Intel (Linux)
9. Open Source is taking over the world
10. Successful Open Source Projects Need Purpose Values Communication Users Contributors Leadership
11. Today we are focusing on Purpose Communication Users Contributors
12. Successful Open Source Projects Need Purpose
13. Why Start a Project ?
14. To scratch   an itch
15. Hugo Static Site Generator in Go   (200+ already existed, but none in Go)
16. Missing tool or library
17. Cobra & Viper CLI commander & Configuration management
18. You wrote something others find useful
19. spf13-vim My Personal Vim Configuration…   now 100+ contributors
20. You’ve thought of a better way to do something
21. MongoDB & Docker Changing the way software is built and run
22. Successful Open Source Projects Need Communication
23. What is Communication • What you say • What you write • What you do • What you build
24. Great Communication = Great writing
25. Great Writing • Requires time • Requires editing • Requires effort • Requires practice
26. Users will have questions • Need to establish a place for them to ask questions • Public is ideal: • Others can respond • Others benefit from the response
27. Forums & mailing lists • Google groups ok, but hard to search • Stack Overflow will happen, but not focused • Forums work best, Discourse is pretty good • IRC also works well, but realtime and without integrated search.
28. README • Your single most important file • First thing everyone sees • Most projects don’t spend enough time on a readme • Where you convey your purpose & values
29. A Good README Vision, concrete examples, installation instructions, etc
30. Challenging Communication
31. One day at MongoDB a couple years ago we received a nasty bug report...
32. Best way to read, leave only the facts
33. Only respond to the facts
34. Now it’s a definitive example on how to respond to trolls
35. Successful Open Source Projects Need Users
36. You need users • No matter how good a project is, it can’t succeed without users • Unless you tell the world about your project, people will not come • Unnatural behavior for most engineers
37. To: Newsgroups: comp.os.inix  Subject: What would you like to see most in minix?  Summary: small poll for my new operating system  Message-ID: <mailto: 1991Aug25.205708.9541@klaava.Helsinki.Fi Hello everybody out there using minix — I’m doing a (free) operating system (just a hobby, won’t be big and professional like gnu) for 386 (486) AT clones. This has been brewing since april, and is starting to get ready. I’d like any feedback on things people like/dislike in minix, as my OS resembles it somewhat (same physical layout of the file-system (due to practical reasons) among other things). I’ve currently ported bash (1.08) and gcc (1.40), and things seem to work. This implies that I’ll get something practical within a few months, and I’d like to know what features most people would want. Any suggestions are welcome, but I won’t promise I’ll implement them :-). Linus (mailto: torvalds@klaava.helsinki.fi) PS. Yes — it’s free of any minix code, and it has a multi-threaded fs. It is NOT protable (uses 386 task switching etc), and it probably never will support anything other than AT-harddisks, as that’s all I have :-(.
38. Focus on the User • Success depends on a good user experience • Contributions come from happy users
39. User Experience • Starts with installation • What are the first 10 minutes like? • What could turn a user away?
40. Good User Experience Requires Listening
41. Successful Open Source Projects Need Contributors
42. Contributors are the lifeblood of Open Source
43. Why Contribute ?
44. Why Contribute • It feels good to give back • Good way to make friends • Great way to make connections • Gain exposure / personal branding
45. Best Software Education
46. Why Contribute • Establish actual real life experience • Better than a resume • Demonstrates that you can do more than code
47. I’m not a developer • Projects need much more than code • Like saying “I’m not an actor, so I can’t work at a movie studio”
48. Join the mailing list/ forums
49. Answer a question on the mailing list
50. Review the documentation
51. Write some documentation
52. Write a tutorial
53. Screencast a feature
54. File a Bug Report
55. Review tickets
56. Try to reproduce bugs and add information
57. Contribute logos, icons & designs
58. How to Contribute
59. Instead of   “This is Wrong”... “How can I help?”
60. Prepare • Learn the tools of the trade • Git & Github • Read the Documentation • Familiarize yourself with IRC, forums, & the correct channels
61. Take Iniative • Don’t be afraid to try • Open source loves self starters • Open source authors are usually very approachable and open to ideas • Communicate and collaborate as much as possible
62. Ask • What can I help with? • I would like to help with X, but would benefit from some guidance, can someone guide me? • If I contributed Y, would that help?
63. No matter how slow you go, you will always lap those on the sidelines
64. How to Get Contributors
65. Most projects have very few contributors • You must give if you want to get • Contributors are an investment in the future of the project • Contributors pay back many times what you put in
66. Make it Easy to Contribute • Use an “open” open source license (Apache 2.0, MIT, BSD) • Provide contribution guidelines • Provide contribution instructions & tutorials
67. Treat Contributors Well • Happier developers will contribute more • The more welcome people feel the more they will help your project
68. Be Responsive • Respond to Pull Requests in a timely manner • Provide and contribute to a channel where people can ask questions • Respond to issues quickly
69. Invite Contributors • Overcommunicate that contributions are welcome • Ask people to contribute • Ask. Ask. Ask. Invite. Invite. Invite.
70. It’s Dangerous to Go Alone
71. Empower Contributors • When someone shows initative and history of good contributions make them a committer • Resist tempation to control • If you aren’t able to be responsive, appoint more committers
72. Teach • Don’t ever say no. • Teach contributors how it can become a yes • Newly empowered contributors contagiously help others
73. Docker’s Birthday Open-source-a-thon 18 Cities + Online. Mentorship by Go & Docker. Save Whales.   http://docker.party
74. We live in an open source world
75. Without contributions open source would not exist
76. You are the most important contributor
77. Thank You !  Questions ?Icons made by Freepik are licensed by CC BY 3.0 @spf13

