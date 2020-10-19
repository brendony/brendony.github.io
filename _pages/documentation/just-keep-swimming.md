---
title: "Just keep swimming - User Guide"

permalink: /documentation/just-keep-swimming

date: 2020-10-19T21:41:00+10:00

categories:
  - documentation
  
tags:
  - python
  - hobbies
  - webapp
  - anvil.works
  
comments: false

---

## Glossary

| Word       | Meaning                                                                                                                                                          |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Event      | One of the parts of a meet (eg. 50m Freestyle). An event can be qualified using tags (eg. 50m Butterfly, Male, Over 50s).                                        |
| Discipline | A swimming discipline, eg. Freestyle, or Breaststroke.                                        |
| Handicap   | A way to make swimmers finish a race almost at the same time.  Faster swimmers are handicapped to start later than slower swimmers based on previous swim times. |
| Heat       | An event might have more people entered into it than can swim at once.  In this case, the even is split into heats (and sometimes finals).                       |
| Meet       | A swim meet is a collection of events, typically held on one day.                                                                                                |
| Nominal handicap | A swimmer's expected time to complete an event, based on historical performance.                                                                                            |
| Race handicap | A delay between the start of a heat and when a swimmer should begin swimming. When well handicapped, a heat might finish with several swimmers touching the wall at almost the same time |
| Scratch    | A type of event that has no handicaps applied. Everybody starts at the same time.                                                                                |
| Tag        | An annotation to an event.                                                                                                                                       |


## Log in and Log out

[Just keep swimming](https://just-keep-swimming.anvil.app/) is a web-based app to manage an amateur swimming club. To access the app, you must first be enrolled into the system. Use your account credentials to login.

To log out of the system, click on your email address in the top-right of the screen, and select *Log out*.

## Editing tables

Most of the tables in *Just keep swimming* use similar design shortcuts:

* The top row of the table is specifically for adding new data to the table. Generally, the rightmost column of this first row will have a '+' (plus) button which will become clickable when enough information has been added to the row. When you click the '+' button, the new data will become visible in the table below the top row, and the top row should empty itself, ready for more new data,
* Tables are paginated. Different pages can be selected using buttons in the bottom right of the table,
* In general, the table will tell you when values in a cell are not in the right format, by showing a message under the cell,
* A '-' (minus) button on a row indicates that clicking this button will remove the row from the system.

## Navigation

The following sections comprise *Just keep swimming*. Click on the heading at the top of the page to navigate to that functionality.

### Home

This section contains the User Guide for the software - you are reading it!

### [Setup](https://just-keep-swimming.anvil.app/#setup)

![setup](/assets/images/jks-user-guide/setup.png)

This section allows you to manage meets:
* create a new meet,
* edit an existing meet, and 
* delete a meet (but I recommend that you don't do this in general).

#### Creating a new meet

Create a new meet by editing the top row of the *Swim meets* table. 
A meet consists of a Date, a Name and a Season. Currently, Seasons are hardcoded into the system, and you can choose a season from the drop-down. Note that the latest season is the default. Adding a new meet requires at least a Date and a Season.

#### Selecting a meet

The *Swim meets* table has a series of radio buttons in the first column. Clicking one of the radio buttons selects that meet, with these effects:
* the meet becomes selected and outlined in orange - to show that it has been selected,
* the events of the meet become visible in the *Meet Events* table,
* the meet becomes editable - you can change the Date, Name or Season of the meet.

#### Editing a meet

A meet can be edited from the table once it has been selected using the radio button.

#### Adding events to a meet

Use the *Meet Events* table to add events to the selected meet. In general, most events will have only values for distance and discipline. Use Tags to show an event was limited in some way (eg. Women) or special (eg. Club Championships).

### [People](https://just-keep-swimming.anvil.app/#people)

The *People* table shows club members listed in alphabetical order by surname. You can Add, Edit and Remove people from the system (although I would strongly advise against removing people from the system).  Future work on the software might include keeping track of currently active people, or even manage their registration fees, and possibly even checking in before a meet.

### [Program](https://just-keep-swimming.anvil.app/#program)

Our swim club is paper-based on the pool deck:
1. Electronic devices and pool water don't mix, and
2. Screens can be very hard to read in sunshine.

Therefore, this page allows configuring and printing event programs for
* registration by a swimmer at check-in,
* planning out heats between registration and the event,
* entering results by hand.

Selecting a meet from the drop-down displays all events in the chosen meet.

Each event will have people listed in the table. People are shown by default if they have swum in that event in the year preceding the meet. It is possible to add or remove people from the printed program by selecting their name from the "Add or remove:" drop-down immediately below the event's program.

The swimmers are sorted by their *nominal handicap*, so that swimmers of similar ability are likely to end up in heats together. Currently, the *nominal handicap* for a swimmer is the quickest time from their previous 5 results in that event, including results up to a year old.

When you are happy with the program for each event, click the *Download PDF* button to obtain a printable version of the programs.