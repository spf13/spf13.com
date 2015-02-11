---
date: 2014-09-03T17:36:12-04:00
description: ""
tags:
- go
- development
- evangelism
- workshop
- public speaking
- OSCON
- advocacy
title: giving an effective workshop
topics:
- Development
- Developer Advocacy
draft: true
---

My definition of a workshop is that there is a level of interaction
greater than a talk and the attendees are participants, not an audience.
Workshops across large groups are really hard because everyone is at
different levels and with a large group you can’t help everyone keep up.
You really have three different options.

1. Don’t give a workshop, give a 3 hour presentation. I’ve seen a lot of
   people take this approach, it seems like the most common one. It’s
   reasonably safe, everyone can follow it at the same pace and it’s
   easy to fit it in the allotted time. However 3 hours is too long for
   an audience to keep their attention. Even 90 minutes is too long,
   especially for a single speaker. Whenever I’ve attended a workshop
   that fit this description it’s pretty obvious that around the 60
   minute mark the audience loses interest.

2. Do give a workshop, but structure it for the beginners. This is
   effective because, well, first of all, it is a workshop. The positive
   aspect is that nobody is left behind. Unfortunately anyone at a level
   above beginner will feel bored much of the time.

3. Give a workshop that works at different learning levels and deliver
   them all. If done right, this is clearly the best option, but it’s
   also the hardest to do. Not only is it hard to deliver, but it takes
   3x longer to prepare than option 2.

At OSCON 2014 I had the opportunity to give a workshop on [Building your
First Go App](/presentation/first-go-app/). The expected audience was
200 people. Acknowledging that Go is a pretty new language and even
people that had some familiarity with Go probably weren’t familiar with
the libraries we were using. Even more challenging is that the
participants were coming from a lot of different backgrounds. Java
programmers approach things very differently from Ruby programmers for
example. So not only were people at different levels, but some concepts
that had similarities to Java would be easy for those with that
background, while other concepts that had similarities with Javascript
would be easy for a different set of people. This was shaping up to be
the most challenging workshop I’ve ever given. Here’s how I approached
it.

## Preparation

I decided to take the third approach. I spent the greater part of 4
weeks preparing the workshop, or around 90 hours. 90 hours for a 3
hour workshop may seem excessive, but let’s break it down.

* 5  hours preparing an outline
* 23 hours coding
* 2  hours designing the deck design
* 30 hours building the deck
* 20 hours rehearsing it 5x
* 10 hours refining it based on feedback (code & deck)


## Define a Theme

Because it’s such a long time. It really helps to have a central theme
guiding your workshop. Since a workshop is so goal oriented, the theme
us usually pretty easy to come up with. In my case it was to build a
single application. At the end of the workshop they would have a
functioning application that they built. This is an easy theme that
weaves through every part of the workshop.

## Sketch an Outline

The first step is to create a rough outline about what you are trying to
accomplish. In this case I needed to come up with the major points I
wanted to convey, then figure out an application that both fit those
points and could conceivably be built in 3 hours with the right
guidance. At this stage the outline can just be the major points. It’s
just there to provide some structure and guidance as you move into the
next step.

## Write Code First

This is one thing I didn’t do as well as I wanted to do. I tried to
build the deck first, then write the code in the steps I was going to
deliver the presentation in. While it seemed like a good idea, it made
it very difficult to rearrange the content the way that worked best. I
ended up rewriting a lot of it as a result. Lesson learned. Write the
complete code first. Commit often, far more often than you normally
would so that you can rebase, rearrange and squash effectively later.

### Building the Deck

Because I wanted to speak to people of different experience levels at
the same time I decided that the best way to do this wasn’t by spending
the first third introducing the Go language. Instead I opted for an
iterative approach with instruction followed by code.

### Code with a message

Break up the code into the steps needed to best accompany your
message.

### Rehearse, Rehearse, Rehearse



## Giving the Workshop


