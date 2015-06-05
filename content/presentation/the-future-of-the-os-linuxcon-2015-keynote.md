---
date: 2015-06-05T10:43:50+09:00
description: ""
tags:
- Linux
- Docker
- Operating Systems
title: the future of the Operating System - LinuxCon 2015 keynote
topics:
- Linux
- Docker
---

Given as a keynote at [LinuxCon + CloudOpen Japan
2015](http://events.linuxfoundation.org/events/linuxcon-japan/program/schedule).

Linux has become the foundation for infrastructure everywhere as it defined
application portability from the desktop to the phone and from to the data
center to the cloud. As applications become increasingly distributed in nature,
the Docker platform serves as the cornerstone of Linux’s evolution solidifying
the dominance of Linux today and into tomorrow. 

{{% slideshare 49015468 %}}

## Transcript


1. The Future of the Operating System
2. What is an Operating System ?
3. OS Manages Processes & Resources
4. OS Provides Portability   (same app runs on different hardware)
5. OS Provides Isolation & Reliability
6. Operating Systems & Apps Over Time
7. 1960s &  1970s Mainframe Era
8. OS in 1960s • IBM OS/360 – First OS that kept track of system resources (program, memory, storage) • CTSS – Introduce scheduling • Univac Exec 8, Burrows MCP, Multics
9. OS in 1970s • UNIX takes over mainframes – only IBM’s MVS and DEC’s OpenVMS remain • UNIX (written in C) first portable OS
10. Apps in 1960s & 1970s • Ran on mainframe • Many apps ran on one mainframe (multi-tenancy) • Very few operators • Relatively small set of “users” • Users didn’t interact with application  • CHALLENGE: Very limited reach
11. 1980s &  1990s Microcomputer Era
12. OS in 1980s & 1990s • UNIX dominates mainframes/servers • PC emerges & brings lots of users (expanded reach) –DOS & Windows –Mac System Software –OS2, Amiga OS & BeOS
13. Apps in 1980s & 1990s • Application ran on a desktop • Single user • Operator became the user  • CHALLENGE : Distribution – Physical media – Ship times measured in months/years
14. 1995 - 2005 Dawn of the Internet Era
15. OS in 1995 - 2005 • Browser becomes gateway to Internet applications • Desktop ruled by Windows • Linux emerges as the “OS of the Internet” • LAMP Stack
16. Apps in 1995 - 2005 • Internet emerges, brings easier distribution • Applications are monoliths running on a few machines • Applications run on owned / leased hardware • Applications accessed through browser • Apps have millions of users • CHALLENGE: Scale
17. 2005 - 2015 Distributed Applications Era
18. Apps in 2005 - 2015 • Browser solidified as window (view) to applications • Mobile emerges… most apps merely component (view) to server based applications • Apps have 1+ billion users
19. APPS IN 2005 - 2015 • Apps evolved to be composed of services • Distributed applications running on clusters • NoSQL & Cloud  • CHALLENGE : Operations & Deployment – Many services require coordination – Need duplicate environments (dev, stage, prod)
20. Applications Run on Clusters Static Website Web Front EndBackground Workers User DB Analytics DB Queue API Endpoint oneapplication
21. Components Need to Work Together Static Website Web Front End Background Workers User DB Analytics DB QueueAPI Endpoint oneapplication
22. New OS needs to schedule not only processes, but components across nodes
23. Development VM QA Server Public Cloud Disaster Recovery Developer Laptop Server Cluster Data Center Distributed Applications Challenge Static Website Web Front EndBackground Workers User DB Analytics DB Queue API Endpoint Development Test & QA Production Scale Out oneapplication
24. OS no longer providing application portability
25. OS needs to evolve to meet Application
26. Linux provides foundation for Solution.. but needs another layer
27. Docker + Linux
28. Modern Application Portability
29. The Docker Mission Build Ship Run Anywhere Any Application Local Cloud Data Center
30. Docker Engine Creates, Ships & Runs containers • Deployable anywhere • Communicates with Docker Hub BUILD  Package app and dependencies together SHIP Deploy locally, in the cloud or in the data center RUN  Run containers with monitoring and stats anywhere 
31. Application Portability Run Docker containers unchanged in any environment, on any infrastructure Build Ship Run
32. Schedule Components & Resources
33. Orchestration Compose • Configure multi-container applications with a simple file Machine • Auto-provision hosts and install Engine with a single command • Drivers to integrate with 12 infrastructure partners  Swarm • Running and scheduling clusters of containers
34. Isolation & Reliability
35. Isolation Container provides true isolation of components Build Ship Run
36. Service Reliability Faithful representation of app with encompassed dependencies Build Ship Run
37. Development VM QA Server Public Cloud Disaster Recovery Developer Laptop Server Cluster Data Center Distributed Applications Solution Development Test & QA Production Scale Out Static Website Web Front End BackgroundWorkers Analytics DB Queue APIEndpoint User DB oneapplication
38. The Docker Un-Enabled Organization
39. Case Study: Gilt Groupe Before Docker • 7 Monolithic apps • Wasted time implementing   monolithic PaaS •Dev-to-Prod: weeks
40. Case Study: ING Before Docker •9+ months from commit to deploy • Poorly rated applications •Redundant processes and apps
41. The Docker Enabled Organization
42. Case Study: Gilt Groupe After Docker • 400+ microservices • 100+ innovations a day • Easily burst capacity at peak times •Dev-to-Prod: minutes
43. Case Study: ING After Docker •15 minutes from commit to live • 1,500 deployments per week
44. The Future…
45. … is written by people willing to disrupt the established
46. UBER
47. Distributed Apps are the Future
48. Linux + Docker   is the Future of Operating Systems
49. THANK YOU
