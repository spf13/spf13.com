---
Description: ""
Keywords:
- Development
- Leadership
- Uncategorized
- development
- software
Section: post
Slug: release-early-release-often-to-minimize-risk
Tags:
- development
- software
Thumbnail: /images/1367_Gantt-chart-textless.png-200x200.png
Title: Release early, release often to minimize risk
Topics:
- Development
- Leadership
Url: post/release-early-release-often-to-minimize-risk
date: 2011-05-05
disqus_identifier: 1363 http://spf13.com/?p=1363
disqus_title: Release early, release often to minimize risk
disqus_url: http://spf13.com/post/release-early-release-often-to-minimize-risk/
---

{{% img src="/media/Gantt-chart-textless.png" class="third right" alt="gantt chart" %}}

Release Cycles have been debated for the last 30 years and will
certainly be for the next 30. Arguments for longer release cycles with
larger releases usually focus on how risky these rapid releases are and
the stability and polish these larger releases with their longer cycles
bring. These arguments are absolute rubbish. To add to the discussion
I’ll put a different emphasis than I’ve heard before. Release early and
release often **to minimize risk**.

# 1. Minimize risk to market

Paul Graham says it quite well, so no need to restate.

> The thing I probably repeat most is this recipe for a startup: get a
> version 1 out fast, then improve it based on users’ reactions.
>
> By “release early” I don’t mean you should release something full of
> bugs, but that you should release something minimal. Users hate bugs,
> but they don’t seem to mind a minimal version 1, if there’s more
> coming soon.
>
> There are several reasons it pays to get version 1 done fast. One is
> that this is simply the right way to write software, whether for a
> startup or not. I’ve been repeating that since 1993, and I haven’t
> seen much since to contradict it. I’ve seen a lot of startups die
> because they were too slow to release stuff, and none because they
> were too quick.
>
> One of the things that will surprise you if you build something
> popular is that you won’t know your
> users. [Reddit](http://reddit.com/) now has almost half a million
> unique visitors a month. Who are all those people? They have no idea.
> No web startup does. And since you don’t know your users, it’s
> dangerous to guess what they’ll like. Better to release something and
> let them tell you.
>
> [Wufoo](http://wufoo.com/) took this to heart and released their
> form-builder before the underlying database. You can’t even drive the
> thing yet, but 83,000 people came to sit in the driver’s seat and hold
> the steering wheel. And Wufoo got valuable feedback from it: Linux
> users complained they used too much Flash, so they rewrote their
> software not to. If they’d waited to release everything at once, they
> wouldn’t have discovered this problem till it was more deeply wired
> in.
>
> Even if you had no users, it would still be important to release
> quickly, because for a startup the initial release acts as a shakedown
> cruise. If anything major is broken– if the idea’s no good, for
> example, or the founders hate one another– the stress of getting that
> first version out will expose it. And if you have such problems you
> want to find them early.
>
> Perhaps the most important reason to release early, though, is that it
> makes you work harder. When you’re working on something that isn’t
> released, problems are intriguing. In something that’s out there,
> problems are alarming. There is a lot more urgency once you release.
> And I think that’s precisely why people put it off. They know they’ll
> have to work a lot harder once they do. <cite> Paul Graham</cite>

# 2. The smaller the release the smaller chance something goes wrong.

This point is so logical it would be hard to challenge (but I’m sure
someone will). The smaller the change set, the less that is affected by
the change set. Isolated features can safely be deployed without
examining the entire system for issues. By isolating development into
specific features you are able to shrink the amount of QA necessary and
can be able to automate nearly all of it. Furthermore frequent releases
with isolated changes make tracking down issues easy as you have a much
smaller set of changes to review.

# 3. Quicker releases = faster fixes

No team is perfect, from time to time, regardless of the process, a
release goes out with a bug. The shorter the release cycle the faster
those fixes are in the hands of consumers and the less the development
team needs to live with a known bug in the product. Nothing drives
developers productivity down further than having to handle bug reports
of issues that have already been fixed but keep being reported. Simply
stated there is a great cost to an organization for every day a bug is
fixed and not released. The worst part is that this is a cost that can
be completely avoided with continuous deployment.

# 4. The more often the releases the better the quality of released code

With longer releases there is an enormous amount of pressure to “Make
the release” We’ve all been there 2 days before the release and 4 days
of work to go. We can’t delay the release, and we are so close so we
pull a couple all nighter getting the code completed before the release.
Triumphant we celebrate that we overcame the timeline and conquered the
schedule.. or did we. What typically happens is that buggy code is
committed and released, developers experience burnout and are
frustrated, productivity and quality and stability are all compromised.
The team behind chromium found this. As the Chromium blog, [Release
Early, Release
Often](http://blog.chromium.org/2010/07/release-early-release-often.html)
states:

> Under the old model, when we faced a deadline with an incomplete
> feature, we had three options, all undesirable: (1) Engineers had to
> rush or work overtime to complete the feature by the deadline, (2) We
> delayed the release to complete that feature (which affected other
> un-related features), or (3) The feature was disabled and had to wait
> approximately 3 months for the next release. With the new schedule, if
> a given feature is not complete, it will simply ride on the next
> release train when it’s ready. Since those trains come quickly and
> regularly (every six weeks), there is less stress.

Chromium moved to a much shorter 6 week build cycle, very rapid for
desktop software, but that same 6 weeks would be considered long on the
web due the instant acceptability of the web. There’s only ever one
version out there, everyone adopts it immediately.

# 5. Frequent releases allow true prioritization of business needs

The longer the time between releases the more managers try to “fill the
release”. When the release is treated as a bucket that need to be filled
with perfect efficiency than managers compromise the more important for
the “fits now”. Rather than attacking the most critical work and
releasing when ready, managers pride themselves on their ability to
wield a Gantt chart like Tetris filling up ever single block. What they
gain in efficiency they lose in business.

# 6. The more often the release the better the team will be at releasing

This out of necessity, and there are plenty of stories of teams that
implemented continuous deployment and had disastrous results, but as a
general rule smart teams will get better at something the more frequent
they do them. Additionally, the more often they have to eat the cost of
deployment the more likely they are to build processes around it to
minimize that cost. A manager may decided that the process needs to be
refined to a given point before incurring the cost frequently. This is
excellent and serves all as the team will have a more polished and
improved deploy process while providing the above benefits. As [Drew
Miller](http://twitter.com/anglicangeek) states

> The more often you release, the better you are at releasing; release
> overhead decreases over time. With long release cycles, the pain of
> release inefficiency is easy to ignore and justify and the urgency and
> incentive to trim that waste is very low. The sense of urgency for
> frequent releases drives velocity, more than off-setting the cost of
> release overhead. <cite> Drew Miller </cite>

The longer the release cycle is the larger and more complex the
changeset is, the longer the delay to market is and the greater the risk
of misdirection. The safest release cycle is the shortest sane one for
any given situation. Whether that’s 6 minutes, 6 hours, 6 days or 6
weeks, keep it short and you’ll avoid risk.
