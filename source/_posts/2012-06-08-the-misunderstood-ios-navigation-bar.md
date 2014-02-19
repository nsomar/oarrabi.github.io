---
layout: post
title: "The Misunderstood iOS Navigation Bar"
date: 2012-11-18 22:22:28 +0300
comments: true
categories: 
---

The very famous iOS navigation bar, or as we geeks call it
*UINavigationBar* is a generally misunderstood component.

In this short article i will try to shed some light on it.

**What a navigation bar is**

* * * * *

*Apple definition (Apple Docs):*

> The UINavigationBar class implements a control fornavigating
> hierarchical content. It’s a bar, typically displayed at the top of
> the screen, containing buttons for navigating up and down a hierarchy.
> The primary properties are a left (back) button, a center title, and
> an optional right button. You can specify custom views for each of
> these

Some points about apple’s definition:

-   *Navigating hierarchical*: To inform and manage the navigation
    structure for the application
<!--more-->
-   *It’s a bar*: And by bar it means it should be contained in a bar
    appearance, a bar has a border, and a bevel to display its starting
    and ending points.
-   *a left (back) button, a center title, and an optional right
    button*: The components of this navigation bars are a back button, a
    middle title to inform the user on which screen he is standing on,
    and an *optional* right auxiliary button.

* * * * *

*Apple HIG points on Navigation Bar:*

The navigation bar is divided in three sections:

-   Back button on the right that has the shape of a backward arrow,
    inside this arrow is the title of the previous page (it seldom hold
    only “back” title).
-   The mid section contains:

    -   The title of the page the user is currently viewing. OR
    -   A filter (Segment control) that filters the current page under
        2-3 different criteria.
-   An optional auxiliary right button that performs only 1 action. this
    right button is not a place where you drop all the actions that you
    didn’t know how to place in the current screen (this is not like the
    overflow button in the Android Action Bar).
     If you really need to add more than one action to the right, then
    you most probably need to rethink the design of the screen.

* * * * *

**What a navigation bar is NOT**

-   The navigation Bar is not a place to dump all the controls that you
    don’t know where to place in the screens.
-   The navigation bar is not an Android Action Bar. the navigation bar
    does not deal with actions, it only deals with the navigational
    hierarchy of the app.
-   The mid section of the navigation bar hold the title of the current
    screen, it shouldn’t be the logo of the app or the company that
    developed the app, and it does not hold some complex control that
    does magic tricks (users rarely discover that such control and
    functionality exist in the apps).
-   The right section of the navigation bar hold only one button, and it
    is by no means a place where you place 2-3 buttons.


