# How to write an awesome issue

A short and informal guide on writing good issues in modern issue
trackers, aimed at non-developers.

## What is this?

A regular user of a project tracker that I manage once wrote to me:

```text
One of my goals in life is to, at least once, be able to write a GH [GitHub]
issue that you will not have the need to rename.
:)
```

This got me thinking a little about what it is that I do automatically
when I triage an issue in an issue tracker like GitHub, and the
meaning of issue/ticket systems in general. No doubt personality
quirk, nesting instinct, and some holdover from a past life all play a
part. However, I think that people on different sides of the
development fence understand issue trackers very differently and I
thought it might be useful to try explaining it all the way through
from the side of software development.

For the impatient, there is a TL;DR at the bottom of the page. But
you're not impatient, right?

## What is an issue tracker?

The glib answer to "what is an issue tracker?" is that it is a tracker
for issues. And it is, but it is missing a lot of the point of what
makes a modern issue tracker like GitHub so popular within various
development communities. To illustrate this, I want to highlight one
specific feature of GitHub and how I use it: commit and history
tracking.

As part of the coding process, GitHub allows code commits to "tag" (or
reference) specific issues or comments within issues. With that, the
GitHub interface allows one to click on link within an issue to see
the referencing code (or vice versa). Moreover, with this information,
GitHub provides a view of source code that allows one to see the
commit history (and thus the issue and comments) for every line of
code.

One of the great things about this is that oftentimes in code,
especially in large long-term multi-person projects, when one finds
something that seems anomalous--an oddity, comment, or possible
problem--we've created a great timesaver. If people have be
conscientious in adding tags during commits, one can jump directly
back into the conversation that resulted in a particular piece of
code, clarifying what is going on, reducing research, and giving a
context for decisions (or errors) made in the past.

If, on the other hand, a ticket has a changing meaning, too large a
scope, or grown too large, less context can easily be derived from
this history, reducing it's utility for this case and possibly
increasing future "costs".

This gets to the heart of a question about issue trackers: if an issue
tracker is to be used as part of a development stack, certain rules or
norms should be followed to allow as much specific history as possible
to be preserved with the code.

For the GO, we overload the trackers at some level and use them as a
feedback forms, notebooks, and participation tools for the community,
as well as actual issue trackers. However, for the trackers to be
effective as development tools at the end of it all, some trackers
need to be the middle and long-term memory for the people on the
"fixing" side, in addition to sorting, reporting, and planning
tools. (For the latter, GitHub Project kanban, Gitter, e-mail, and the
wiki are also there for some of these; YMMV.)

Following through with that, and given that a person making a ticket
may not be familiar with the ins and out of the code or which project
something is associated with, what is the best way to write a ticket
and interact with a tracker?

## The anatomy of an issue without issues: A Tale of Two Tickets

Heading out with that train of thought, how does one write a
good/useful issue that will stand the test of time? A good rule of
thumb is that a ticket title should at least contain: *frequency*,
*location*, and an *problem, action, or outcome*. A ticket body itself
should ideally contain *what is*, what *should be*,and the steps to
*reproduce* the issues from scratch for the target audience (the
developers), as well as as much associated *context* as feasible.

In the GO trackers, there is often associated metadata in the form of
tags. A common case is that there are tags that fill the rolls of:
*wish*, *irritant*, *affects usability*, or *makes unusable* (on the
Noctua and AmiGO trackers, this is the enhancement, A, B, and C
tags). The larger context is derived from the tracker itself.

To help illustrate the use of these points, let's look at a "good"
ticket and a "not-so-good" ticket, both based on the same problem.

To try and keep this abstract, let's imagine that we work at a company
making an online video game. This imaginary company does all of the
things that you'd imagine that an imaginary game company would do:
produce and maintain several games, have an account system, etc.
Also, at this company, there is a division of labor: there are workers
who are "non-technical" users/testers and there are workers who
directly create and fix the games. One of the things that the former
group of users does as part of their duties is report issues about
various games to a central tracker, where the "technical" side tries
to use that information to apply fixes and create improvements, all
while trying to advance the software according to some internal
roadmap. All pretty standard fare.

### The Good Ticket

For example, at this made-up company, let's look at a fairly well structured
made-up issue on the *Super Mario X* (game title) tracker:

```text
Title: Occasionally, when Mario touches a ?-brick in level 1, Mario dies
Meta: [affects usability]
Body:
When playing and starting from level one from the start screen, Mario
progresses through the level; after passing the first Mushroom, if Mario
touches the ?-brick, there is a chance that the Mario will lose a life.
This seems to happen about one in every five tries (see attached
video), and does not happen if Mario has not jumped. This does not
happen if Mario starts from a save point after level one.
Mario should be able to touch all bricks at any time without affecting
lives.
```

I'd note here that the user specifically mentions Mario. It turns out,
in the imaginary underlying cause of our imaginary issue, that this
happens with all playable characters. However, the user themselves did
not experience it that way, they are just explaining their own
personal experience with *sufficient context* to be *repeatable*. As
well, while this reported issue is serious, the user recognizes that
there is some way forward or workaround and that they can
continue. This is helpful for people on the software side to be able
to more easily prioritize the issue in the context of other fixes and
the roadmap more generally.

Fortunately, in our made-up company, this pretty tightly describes a
possible effect of a just-fixed issue picked up by the software team
about a pointer error in the color palette code that could cause some
semi-random things to happen during color transitions, notably the
yellow in the ?-blocks. While our user's description of their issue is
very different, I feel I have enough context to make the call and can
mark this as a duplicate and request re-testing at the next release. I
can forget about this immediately, but can easily search for it if it
comes up again.

### Through the Looking Glass

An example of the same issue written less-well into a ticket could be:

```text
Title: mario 10 broken
Meta: [makes unusable]
Body:
Help! Sometimes mario is dying. And the link for account?
```

This contrast here should hopefully be apparently, but it may be
useful to break down some of the things that are not optimal here, and
why, field by field:

**Title**. The title is probably overly specific or wrong. We know
that this is supposed to be the Super Mario X tracker, so it does not
need to be repeated, right? Or is that "10" signifying something going
on on level 10? That's a question for the reporter then. The fact that
it is "broken" is pretty much a given, but I have little idea of the
magnitude, or even what is going on at the most basic level from
reading the title. This can make the issue harder to find in the
future, and would have to be rewritten.

**Meta**. Given the possibly dire, title, I may be very worried about
this issue and this tag dials that up. However, we know from the
information in the body of the ticket that, while serious, this issue
may not be a complete showstopper. The user (possibly venting their
frustration) may have added some processing cost to triaging this
item; or maybe everything really is on fire. A developer's thought
process may be like:

Is it possible on that for this user nothing really works at all?  We
are close to a release and that could be a big problem. I'm going to
have to drop everything (which took a while to get into and may have
to be recreated) and follow-up with this user. Like right now.

**Body**. Not great, but takes a little unpacking to get at
why--impressive for under a dozen words.

The first sentence of the report is that Mario occasionally
dies. Understood, but that happens in games sometimes. One can assume
that the reporter has some problem with Mario dying in some unexpected
way, but they have given no additional context to make much of a
useful model--maybe the person is a pacifist and thinks that the
Mushrooms and Mario should just work things out; maybe the software is
broken; maybe something else entirely is playing out.

The second sentence's account "link" comment is confusing here as
well. It may be that Mario is supposed to interact with the account
mechanism or another character "Link" in some way I was unaware of
(while dying no less), or it may be that the reporter is tacking a
second, possibly unrelated, issue onto the first.

### Comparing the two

While issues as confounding as the "not-so-good" one above are rare, I
have had to triage tickets very much like this. In some cases, I think
that the user may be more interested in venting frustration (which is
completely understandable) and getting somebody to "fix it" than in
spending effort on helping to remedy the situation relative to other
priorities. It is important to keep in mind that effort towards
collaboration/engagement is very important in public projects.

For the "Good" example, the cognitive overhead when I come back to the
issue in a week or a month is very very low--I can even just look at
the title, prioritize it, and maybe work out a theory of how it fits
in with the next release or other issues. In the second case, if I
have not already done so, I have to start a process with the user to
extract the necessary information to be able to duplicate the issue
and/or create the institutional memory of the request. Given time
zones and distance, this process can take a while with multiple
contacts, and because the issue does not yet fit into the literal
software's worldview yet, there is some overhead every time the issue
needs to be re-engage with.

## The Good Ticket in a broader context

The above examples can be a little disorienting in that they describe
software that the reader is likely unfamiliar with. Of course, if
somebody does not have intimate details about how something works or
how something is experienced, it's very hard to write the "perfect"
ticket for the people who are going to deal with it on either side of
the fence. While it is expected that nobody is writing the Platonic
Ideal ticket (which happily includes a PR, foot massage, and a gift
card:), there are a few broad things to keep in mind beyond any
specifics:

* *Who, what, where, when, why: 5Ws.* Does the ticket include all of
  these in some way?  Unless clear from the context, this may include
  the URL one visited/started from and/or the version of the
  software. "I die on level 1 sometimes touching a block" hits all of
  those and actually gives us a lot to go on--we have a path forward
  and follow-up questions will be easy to generate. If this wasn't
  something I knew about, my first question would be "when" does that
  happen and try and get a detailed description that I could use to
  reproduce it.
* *Can I help you with that?* Sometimes, a ticket is not the
  appropriate avenue (it can depend, see below) or maybe the tracker
  is wrong. You might want to pick a different forum to get
  help. Maybe not. But it is worth a moment of care.
* *Triaging from the Horn of Plenty.* While your issue is special to
  you, it is balanced against literally hundreds of other tickets all
  clamoring for attention and relief in various projects, not even
  including the long-term project-wide roadmaps. In this environment,
  sometimes things can be dismissed or marked out too quickly in an
  effort to keep momentum going. It helps if you can help developers
  see what you see. (To give an example of this, occasionally somebody
  will point something out in a way that I never considered before and
  it will start really bothering me as well; guess what issue gets
  fixed when I'm waiting in a cafe on Saturday afternoon?)
* *Nobody creates a bug on purpose* Congratulations--you are an
  explorer in a new land! Given trying to work through software
  roadmaps and keeping up with new issues and needs, a lot can go
  unnoticed in the software development process. You may be describing
  something that nobody has seen or even thought about before, and
  without sufficient context, may be hard to understand or reproduce,
  even from the people who made the software. It's always good to give
  as much information as possible, including links and background
  context.
* *What was that again?* From the description, how long would the
  reporter think a stranger would take to reproduce the issue? The
  reproduction/duplication of an issue is, fundamentally, the most
  important thing. From there, everything else can be filled out. If
  the reporter can spend an additional minute to make the developer
  triage a half-hour easier, that is a huge help and likely /very/
  cost effective for a project overall.
* *Software development is economics* Related to the above, especially
  in smaller endeavors, time and money are always severely
  limited. With that in mind, what I'm about to say is *not* strictly
  true, but it may be a good model to have when creating a ticket:
  every ticket opened, no matter how small or trivial, takes *at
  least* 15 minutes of developer time to manage and triage before any
  work can actually be spent on the actual issue. This time includes,
  reading, adding extra context, asking the user to supply context,
  prioritizing, changing trackers, making the issue searchable,
  looking up and adding references to related issues, adding
  contextual notes, ballparking the time, etc.
  I am *not* saying that tickets should not be created, but rather that
  they are created mindfully and try to give as many of those given 15
  minutes back over to dealing with the underlying issue, rather than
  trying to recreate what was intended after the fact.
* *Like butter* Finally, and more personally, there are the small
  things that may I do to tickets to make them feel more at home--to
  reduce my cognitive overhead in dealing with them. While a user may
  only see a ticket twice--at creation and (maybe) resolution--I may
  look over it, on the title or body level, dozens of times,
  constantly editing and reshuffling as new information comes to
  light, priorities shift, or roadmaps are restructured. To make that
  process easier on myself, I try to make as smooth reading as
  possible. This may be "fixing" language so that it better conforms
  to the way I think about "location" and "frequency" in a project, or
  even changing a preposition from "in" to "on", as I sometimes use
  the former for the internal code of a page (html/js/css) and the
  latter for the rendering of the page. It's more clear to me and I'm
  just trying to lower my overhead, it has nothing to do necessarily
  with the quality or statement of the original ticket; as my
  understanding of an issue changes, so probably will the title.

<!-- ## Future -->

<!-- Honestly, I'd love to have a little training as some point for people -->
<!-- interested in how to use the trackers more effectively at one of these -->
<!-- consortium meetings, both for issues and githubbiness. -->

<!-- It might reduce -->
<!-- the overhead of people trying to triage issues and might help remove -->
<!-- some of the "magical box" mindset. -->

<!-- The argument that people on the other -->
<!-- side make is that it is the developers' job to "make it go away" and that it an -->
<!-- unnecessary burden on the user/curator side to attempt any kind of -->
<!-- training. -->

<!-- I feel that this may be a bit short-sighted, especially when -->
<!-- thinking about the dollar amount of time spent on the other side trying -->
<!-- to figure out what is going on and make a picture, versus a little -->
<!-- nudging of the former. -->

<!-- I think that also starts the argument for -->
<!-- avoiding using the trackers as a project management device (and there is -->
<!-- often a lot of pressure to do that for the sake of centralization). -->

## TL;DR

Writing software for numerous large projects at the same time is
expensive and difficult, good tracker use can make things more
efficient and easier, as well as improving communications between
software users and software creators.

It is general good practice narrow a ticket to be as specific as
possible and to give enough context so that it is easily repeatable.

A ticket title should contain:

* *frequency* (how often/when something happens)
* *location* (URL, place in file, etc.)
* *problem, action, or outcome*

A ticket body should contain:

* *what is* occurring
* what *should be* occurring
* steps to *reproduce* what the user is having issue with
* as much associated *context* as feasible


Above all, keep in mind that the main purpose of ticket is to
communicate experience and history for the intended audience.

## Afterwards

Above all: be happy having issues, sometimes they're all we have!
