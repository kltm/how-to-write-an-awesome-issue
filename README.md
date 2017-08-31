# How to write an awesome issue

A short and informal guide on writing good issues, aimed at non-developers.

## What is this?

A regular user of a project tracker that I manage once wrote to me:

```text
One of my goals in life is to, at least once, be able to write a GH
issue that you will not have the need to rename. 
:)
```

This got me thinking a little about what it is that I do automatically
when I triage an issue in a tracker, and the meaning of issue/ticket
systems in general. No doubt personality quirk, nesting instinct, and
some holdover from a past life all play a part. However, I think that
people on different sides of the fence understand issue trackers very
differently and I thought it might be useful to try explaining it all
the way through from the side of software development.

## Image a world...

To try and keep this abstract, let's image that we work at a company
making an online video game. This imaginary company does all of the
things that you'd imagine that an imaginary game company would do:
produce and maintain several games, have an account system, etc.
Also, at this company, there is a division of labor: there are workers
who are non-technical users/testers and there are workers who create
and fix the games. One of the things that the former group of users
does is report issues about various games to a central tracker, where
the technical side tries to use that information to apply fixes and
create improvements, all while trying to advance the software
according to some external roadmap. All pretty standard fare.

## The anatomy of an issue without issues

A good rule of thumb is that a ticket title should at least contain:
*frequency*, *location*, and an *issue, action, or outcome*. A ticket
body itself should ideally contain *what is*, steps to *reproduce* for
the target audience (the fixers), and what *should be*, as well as as
much associated *context* as feasible. The associated metadata is one
of four tags: enhancement (wish), irritant, affects usability, or
makes unusable (on the Noctua and AmiGO trackers, this is the
wishlist, A, B, and C tags). The larger context is derived from the
tracker itself.

For example, let's look at a fairly well structured made-up issue on
the Super Mario X tracker:

```text
Title: Occasionally, when Mario touches a ?-brick in level 1, Mario dies
Meta: [affects usability]
Body:
When playing and starting from level one from the start screen, Mario
progresses through the level; after passing the first Mushroom, if Mario
touches the ?-brick, there is a chance that the Mario will lose a life.
This seems to happen about one in every fives tries (see attached
video), and does not happen if Mario has not jumped. This does not
happen if Mario starts from a save point after level one.
Mario should be able to touch all bricks at any time without affecting
lives.
```

I'd note here that the user specifically mentions Mario. It turns out,
in the imaginary underlying cause of our imaginary issue, that this
happens with all playable characters. However, the user themselves did
not experience it that way, they are just explaining their own
personal experience with sufficient context to be repeatable. As well,
while this reported issue is serious, the user recognizes that there
is some way forward or workaround and that they can continue. This is
helpful for people on the software side to be able to more easily
prioritize the issue in the context of other fixes and the roadmap
more generally.

Fortunately, in our made-up company, this pretty tightly describes a
possible effect of a just-fixed issue picked up by the software team
about a pointer error in the color palette code that could cause some
semi-random things to happen during color transitions, notably the
yellow in the ?-blocks. While our users description of their issue is
very different, I feel I have enough context to make the call and can
mark this as a duplicate and request re-testing at the next release. I
can forget about this immediately, but can easily search for it if it
comes up again.

An example of the same ticket written poorly could be:

```text
Title: mario 10 broken
Meta: [makes unusable]
Body:
Help! Sometimes mario is dying. And the link for account?
```

To break down some of the things wrong here, and why, field by field:

**Title**. The title is overly specific, vague, or possibly completely
wrong. We know that this is supposed to be the Super Mario X tracker,
so it does not need to be repeated...or is that "10" signifying
something going on on level 10? The fact that it is "broken" is pretty
much a given, but I have little idea of the magnitude, or even what is
going on at the most basic level from reading the title. This can make
the issue harder to find in the future, and would have to be
rewritten.

**Meta**. Given the unhelpful, but possibly dire, title, I'm probably
very worried about this issue. We know from the "good" writing that,
while serious, may not be a complete showstopper. The user (possibly
venting their frustration) may have added some processing cost to
triaging this item. The thought process may be like:

Is it possible on this user's machine nothing really works at all?
We are close to a release and that could be a big problem. I'm going
to have to drop everything (which took a while to get into and may
have to be recreated) and follow-up with this user. Like right now.

**Body**. This is aggressively unhelpful in an almost endless number
of ways--impressive for under a dozen words.

Mario occasionally dies, yes. If you want to get philosophical about
it, that's the point of the game at some level. I assume that the user
has some problem with him dying in some unexpected way, but I have
literally nothing to go off of here. Maybe the person is a pacifist
and thinks that the Mushrooms and Mario should just work things out;
maybe the software is broken; maybe they're having an existential
crisis with Mario as their surrogate. And the account "link" comment?
Is Mario supposed to interact with the account mechanism in some way I
was unaware of (when dying no less), or is the user just tacking on
something unrelated (and inexplicable) for a different issue? Or maybe
Link, a character from a different project, is supposed to interact
with the account mechanism...?

## Things to keep in mind

### Nobody creates a bug on purpose--you are an explorer in a new land

Well, rarely anyways.

Given trying to work through software roadmaps and keeping up with new
issues and needs, a lot can go unnoticed in the software development
process. You may be describing something that nobody has seen before
that, without sufficient context, may be hard to understand or
reproduce--even from the people who made the software. It's always
good to give as much information as possible, including links and
background context.

### Software development is economics

TODO

There can be severe limitations on software development resources within the sciences.

There are also trade-offs between necessary shortcuts (this needs to
go out tomorrow, so sacrifices will be made) and solid development.

## Just how am I supposed to write the follow-up to the user?

While issues as confounding as the one above are rare, I have had
actual examples of issues very much like this in trackers. I think
some may represent at some level a lack of understanding of how the
tracker mechanism is used and viewed on the other side. In some cases,
I think that the user may be more interested in venting frustration
(which is understandable) and getting somebody to "fix it" than in
spending effort on helping to remedy the situation. It is important to
keep in mind that effort for collaboration/engagement is very
important in public projects.

For GO, we overload the trackers at some level and use them as a
feedback forms, notebooks, and participation tools for the community,
as well as actual issue trackers. However, for the trackers to be
effective at the end of it all, they have to be the middle and
long-term memory for the people on the "fixing" side and not streams
of consciousness coming from one or both sides--that would be for
Slack, e-mail, wikis, etc.  For the first example, the cognitive
overhead when I come back to the issue in a week or a month is very
very low--I can even just look at the title, prioritize it, and maybe
work out a theory of how it fits in with the next release or other
issues. In the second case, if I have not already done so, I have to
start a process with the user to extract the necessary information to
be able to duplicate the issue and/or create the institutional memory
of the request. Given time zones and distance, this process can take a
while with multiple contacts, and because the issue does not yet fit
into the literal software's worldview yet, there is some overhead
every time the issue needs to be re-engage with.

## Anatomy of a good problem

Of course, if somebody does not have intimate details about how
something works, it's very hard to write the "perfect" ticket for the
people who are going to modify the software/site/data to get to the
desired outcome. Nobody expects perfect tickets, especially coming from
the outside. However, there are a few rules of thumb to writing a good
issue for a tracker:

* *Can I help you with that?* Sometimes, a ticket is not the appropriate
  avenue (it can depend, see below) or maybe the tracker is wrong. You
  might want to pick a different forum to get help. Maybe not. But it is
  worth a moment of care.
* *Who, what, where, when, why: 5Ws.* Seriously, do you have all of those?
  Unless otherwise painfully clear from the context, this should at least
  include the URL you visited/started from and/or the version of the
  software. "I die on level 1 sometimes touching a block" hits all of
  those and actually gives us a lot to go on--we have a path forward and
  follow-up questions will be easy to generate. If this wasn't something I
  knew about, my first question would be "when" does that happen and try
  and get a detailed description that I could use to reproduce it.
* *What's the cost?* Given your description, how long do you think it
  will take for the person at the other end to reproduce it, really?
  The reproduction/duplication of an issue is, fundamentally, the only
  thing that matters--others can take it from there. And the faster
  the better: if the end-user can spend a minute to make the task at
  the other end a half-hour easier, that is a huge help and likely
  /very/ cost effective--it can be a shared money pool.
* *That's a lot of shrimp.* While your issue is special to you, it is
  balanced against possibly hundreds of other tickets all clamoring
  for attention and relief, not including the roadmap, and sometimes
  things can be dismissed or marked out too quickly in an effort to
  keep momentum going. It helps if you can help us see what you
  see. (To give an example of this, occasionally somebody will point
  something out in a way that I never considered before and it will
  start really bothering me as well; guess what issue gets fixed
  sooner rather than later?)

## Oiling the wheels

Finally, and more personally, there are the small things that I do to
tickets to make them feel more at home, to reduce their cognitive
overhead. While a user may only see a ticket twice--at creation and
(maybe) resolution--I may look over it, on the title or body level,
dozens of times, constantly editing and reshuffling as priorities
shift and roadmaps are restructured. To make that process easier for
me, I try to grease them and make them sail as smooth as possible
through my brain. This may be "fixing" language so that it better
conforms to the way I think about "location" and "frequency", or even
changing a preposition from "in" to "on", as I sometimes use the
former for the internal code of a page (html/js/css) and the latter
for the rendering of the page. It's more clear to me and I'm just
trying to lower my overhead, it has nothing to do necessarily with the
quality or statement of the original ticket--as my understanding of
the issues changes, so probably will the title.

## Future

Honestly, I'd love to have a little training as some point for people
interested in how to use the trackers more effectively at one of these
consortium meetings, both for issues and githubbiness. It might reduce
the overhead of people trying to triage issues and might help remove
some of the "magical box" mindset. The argument that people on the other
side make is that it is the fixers' job to "make it go" and that it an
unnecessary burden on the user/curator side to attempt any kind of
training. I feel that this may be a bit short-sighted, especially when
thinking about the dollar amount of time spent on the other side trying
to figure out what is going on and make a picture, versus a little
nudging of the former. I think that also starts the argument for
avoiding using the trackers as a project management device (and there is
often a lot of pressure to do that for the sake of centralization).
