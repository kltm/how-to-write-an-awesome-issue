# how-to-write-an-awesome-issue

A short informal guide on writing good issues for trackers, aimed at non-developers.

## What is this?

A "regular" user of a project tracker that I manage once wrote to me:

```text
One of my goals in life is to, at least once, be able to write a GH
issue that you will not have the need to rename. 
:)
```

This got me thinking a little about what it is that I do automatically
when I triage an issue in a tracker, and the meaning of issue/ticket
systems in general. No doubt personality quirk, nesting instinct, and
some holdover from a past life all play a part, but I think that
people on different sides of the fence react to the issues trackers
very differently, and I thought it might be useful to try explaining
it all the way through from the side of a developer.

## Image a world...

To try and keep this abstract, let's image that we work at a company
making an online video game.This imaginary company does all of the
things that you'd imagine that an imaginary game company would do:
produce and maintain several games, have an account system, etc.  Also
at this company, there are workers who are non-technical users/testers
and the people who actually create and fix the games; one of the
things that the regular users do is report issues about various games
to a central tracker, where the technical side tries to use that
information to apply fixes and create improvements. All pretty
standard fare.

## The anatomy of an issue without issues

Let's take a look at 
A thread of that previous life ruled that a ticket title should
ideally contain: frequency, location, and issue|action|outcome. A
ticket body itself should contain *what is*, steps to *reproduce* for
the target audience (the fixers), and what *should be*, as well as as
much associated *context* as feasible. The associated metadata is one
of four tags: enhancement (wish), irritant, affects usability, makes
unusable (on the Noctua and AmiGO trackers, this is the wishlist, A,
B, and C tags). The larger context is derived from the tracker
itself. For example, on the Super Mario X tracker, we have:

```text
Title: Occasionally, when Mario touches a ?-brick in level 1, Mario dies.
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

I'd note that the user specifically mentions Mario. It turns out this
happens with all playable characters, but the user themselves did not
experience it, they are just explaining their personal experience with
sufficient context to be repeatable. While serious, the user recognizes
that there is some way forward or workaround to continue.

Fortunately, in our made-up company, this pretty tightly describes a
possible effect of a just-fixed issue picked up by the software team
about a pointer error in the color palette code that could cause some
semi-random things to happen during color transitions, notably the
yellow in the ?-blocks. While their description of that error was very
different, I feel I have enough context to make the call and can mark
this as a duplicate and request re-testing at the next release. I can
forget about this immediately, but can easily search for it if it comes
up again.

An example of the same ticket written poorly would be:

```text
Title: mario 10 broken
Meta: [makes unusable]
Body:
Help! Sometimes mario is dying. And the link for account?
```

To break down some of the things wrong here.

**Title**. The title is overly specific, vague, or possibly completely
wrong. We know that this is supposed to be the Super Mario X tracker,
so it does not need to be repeated...or is that "10" signifying
something going on on level 10? The fact that it is "broken" is pretty
much a given, but I have little idea of the magnitude, or even what is
going on at the most basic level.

**Meta**. Given the unhelpful, but dire, title, I'm very worried about
this.  Is it possible on this user's machine nothing really works at
all? We are close to a release and that could be a big problem. I'm
probably going to have to drop everything (which took a while to get
into) and follow-up with this user. Like now. It will turn out that
while serious, the issue was not that bad, and I probably could have
gone about my business a while longer, getting feedback when I went
through my mail again at the end of the day. There was some cost
associated with this choice.

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

## Nobody creates a bug on purpose-- you are an explorer in a new land

Well, rarely anyways. There is also a fine line between necessary
shortcuts (this needs to go out tomorrow, so sacrifices will be made).

## Just how am I supposed to write the follow-up to the user?

While tickets this bad are rare, I have had actual examples of issues very much
like this in trackers. I think they may represent at some level a lack of
understanding of how the tracker mechanism is used and viewed on the
other side. In this case, I think that the user may have been more
interested in venting frustration (which is perfectly fair/valid) and
getting somebody to "fix it" than in spending effort on helping to
remedy the situation; that effort for collaboration/engagement is very
important in public projects.

For GO, we overload the trackers at some level and use them as a
feedback forms, notebooks, and participation tools for the community, as
well as actual issue trackers. However, for the trackers to be
effective, at the end they have to be the middle and long-term memory
for the people on the "fixing" side and not streams of consciousness
coming from one or both sides (that would be for slack, email, etc.).
For the first example, the cognitive overhead when I come back to the
issue in a week or a month is very very low--I can even just look at the
title, prioritize it, and maybe work out a theory of how it fits in with
the next release or other issues. In the second case, if I have not
already done so, I have to start a process with the user to extract the
necessary information to be able to duplicate the issue and/or create
the institutional memory of the request. Given timezones and distance,
this process can take a while with multiple contacts, and because the
issue does not yet fit into the literal software's worldview yet, there
is some overhead every time the issue needs to be re-engage with.

Of course, if somebody does not have intimate details about how
something works, it's very hard to write the "perfect" ticket for the
people who are going to modify the software/site/data to get to the
desired outcome. Nobody expects perfect tickets, especially coming from
the outside. However, there are a few rules of thumb to writing a good
issue for a tracker:

* Can I help you with that? Sometimes, a ticket is not the appropriate
  avenue (it can depend, see below) or maybe the tracker is wrong. You
  might want to pick a different forum to get help. Maybe not. But it is
  worth a moment of care.
* Who, what, where, when, why: 5Ws. Seriously, do you have all of those?
  Unless otherwise painfully clear from the context, this should at least
  include the URL you visited/started from and/or the version of the
  software. "I die on level 1 sometimes touching a block" hits all of
  those and actually gives us a lot to go on--we have a path forward and
  follow-up questions will be easy to generate. If this wasn't something I
  knew about, my first question would be "when" does that happen and try
  and get a detailed description that I could use to reproduce it.
* Given your description, how long do you think it will take for the
  person at the other end to reproduce it, really? The
  reproduction/duplication of an issue is, fundamentally, the only thing
  that matters--others can take it from there. And the faster the better:
  if the end-user can spend a minute to make the task at the other end a
  half-hour easier, that is a huge help and likely /very/ cost
  effective--it can be a shared money pool.
* That's a lot of shrimp. While your issue is special to you, it is
  balanced against possibly hundreds of other tickets all clamoring for
  attention and relief, and sometimes things are dismissed or marked out
  too quickly. Let's take another look at it, but it helps if you can help
  us see what you see. (To give an example of this, occasionally somebody
  will point something out in a way that I never considered before and it
  will start really bothering me as well; guess what issue gets a hotfix?)

Finally (whoops, that ended up being quite a wall of text), and more
personally, there are the small things that I do to tickets to make them
feel more at home. While a user may only see a ticket twice--at creation
and (maybe) resolution--I may look over it, on the title or body level,
dozens of times, constantly editing and reshuffling as priorities shift
and structures restructured. To make that process easier for me, I try
to grease them and make them sail as smooth as possible through my
brain. In the case of  "Enable Post-to-Twitter in Create Article page",
there are two things that caused hiccups in my mind: one is that I know
now (but not at the time of ticket creation) that this happens for some
user roles but not others--that narrowing maps onto the "location" and
"frequency" parts of the title for me, as it does not uniformly occur
for all users in all situations. So: an update to a previously fine
title. While I was there, I changed the preposition from "in" to "on" as
I sometimes use the former for the internal code of a page (html/js/css)
and the latter for the rendering of the page; it's more clear to me and
I'm just trying to lower my overhead, it has nothing to do necessarily
with the quality or statement of the original ticket--as my
understanding of the issues changes, so probably will the title.

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

Anyways, that's a lot of shrimp :)

Cheers,

-kltm
