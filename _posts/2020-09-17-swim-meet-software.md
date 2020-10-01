---
title: "Swim meet software"
date: 2020-09-17T21:41:00+10:00
categories:
  - blog
tags:
  - python
  - hobbies
  - webapp
  - anvil.works
---

## TL;DR

I built a WebApp in [Anvil](https://anvil.works). It's a full-stack development solution entirely in Python, and it's perfect for hobby projects (and anything that depends on development velocity).

# Just keep swimming

Sometimes the best motivation for a project is to just scratch an itch. In this case, I'm a member of an amateur swimming club that meets weekly in summer (pandemic permitting!). The attraction of the club, (aside from the very welcoming atmosphere and lovely people) is that it holds time-handicapped races, permitting people of all ages and abilities to swim against each other and have interesting contests.

## Nomenclature

| Word     | Meaning                                                                                                                                                          |
|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Event    | One of the parts of a meet (eg. 50m Freestyle). An event can be qualified using tags (eg. 50m Butterfly, Male, Over 50s).                                        |
| Handicap | A way to make swimmers finish a race almost at the same time.  Faster swimmers are handicapped to start later than slower swimmers based on previous swim times. |
| Heat     | An event might have more people entered into it than can swim at once.  In this case, the even is split into heats (and sometimes finals).                       |
| Meet     | A swim meet is a collection of events, typically held on one day.                                                                                                |
| Scratch  | A type of event that has no handicaps applied. Everybody starts at the same time.                                                                                |
| Tag      | An annotation to an event.                                                                                                                                       |

## When you only have a hammer, everything looks like a nail

Up until now, our club has used a highly customised and macro-laden Excel spreadsheet to prepare for a swim meet and store results. Poolside organisation is paper-based due to a combination of some tech-shy club officials, and the possibility of water damage to mobile devices on the pool deck.

With these constraints, the spreadsheet provides these functions:
1. Generate swim event sheets for printing. These sheets are so that, on arrival, a swimmer can register themself to swim the event. Each sheet is pre-populated with the list of people who have swum the event previously, and their handicaps. The spreadsheet sorts people by their handicap, so that the swim heats will have closely matched swimmers. Event sheets have space for handwritten results and other annotations.
2. After the meet, we enter results into the spreadsheet from the event sheet.
3. It provides tabular results for publishing online.
4. It calculates new handicaps from the results.

Every week, we make a new dated version of the spreadsheet (for back-up purposes), with cumulative results. (Version control is not common outside the software world, although something like Google drive could provide version control) 

## Choosing a new hammer

As a software engineer, my reaction on seeing the spreadsheet was: "This should be in a database. Also, it would be nice to have a user interface to help the club officers out."

Options were, rated by roughly increasing effort:
* Do nothing,
* Use something like MS Access,
* Make a webapp, first choosing a tech stack, or 
* Investigate and use no-code platform.

So then, given that I wanted to do SOMETHING (because {% post_url 2020-09-16-pandemic-hobbies %}), what should I choose?

### Exploration 1: Desktop Database software

I've never used MS Access, and I didn't own a licence for it. Instead, I played with LibreOffice Base for a couple of days. I discarded this approach because it felt like *work*. I was learning something, but it wasn't scratching my itch.

### Exploration 2: No-code solutions

I spent a while exploring the field of [low-code and no-code tech stacks](https://codebots.com/low-code/what-is-no-code-the-pros-and-cons-of-no-code-for-software-development) but felt very limited in what I could achieve - although I suspect very strongly this was due to me not quite understanding the platforms.

### Exploration 3: Elm & GraphQL

My next abortive attempt at making swim meet software was using new-to-me technologies, so I could learn about them.

I've been meaning to get started in [Elm](https://elm-lang.org) for a while, as colleagues have been recommending the language to me since at least 2016. Elm is strictly a frontend language, so I needed to choose a backend also, and settled on [Hasura](https://hasura.io) so I could also learn about GraphQL - and find out if this is a better API spec than REST.

Elm was fun to learn, and taught me a lot. Those lessons will inform my future self, and I hope to do more with Elm one day. As a bonus, I found that the Elm community is singularly warm and welcoming.
 
Hasura has a lot of things going for it. (Database versioning built-in! Schema migrations generated automatically! GraphQL interface autogenerated to match the database!)

My progress was very slow, though, due to unfamiliarity with my entire tech stack. As a hobby project, things started to feel very much like a full-blown work project. Ideally, a hobby project should feel like a [hackathon](https://medium.com/@alexgilleran/what-3-years-of-hacking-for-humanity-has-taught-me-about-building-an-mvp-in-a-weekend-79556625755d), not a marathon.

### My new hammer is an old one from a different toolbox (a.k.a. Python FTW)

I have settled on [Anvil](https://anvil.works) as my platform.

This post is already too long, so I'll list some reasons for my choice:
1. It's Python, all the way through - front-end and back-end. I know Python. Python is especially good for speed of development.
2. It has drag-and-drop UI construction.
3. It has database support built-in, including a default local database.

I'll go into Anvil in more detail in follow-up posts, but suffice to say that I think it's a brilliant platform for getting stuff done quickly. 

As an example, I was able to add user accounts and login to my App in less than an afternoon. It's functionality that I've coded in my professional capacity, and this time, it was so easy it felt like I was cheating.

Anvil. It's great. Check it out.