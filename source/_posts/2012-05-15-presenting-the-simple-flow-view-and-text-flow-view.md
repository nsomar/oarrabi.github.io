---
layout: post
title: "Presenting the simple flow view and text flow view"
date: 2012-11-09 22:22:28 +0300
comments: true
categories: 
---

So after posting my [simple
pseudo](http://omarabdelhafith.tumblr.com/post/35283053691/flow-view-simple-pseudo-code-in-objective-c-on-ios "simple pseudo")
code for flow view, i came up with a pretty easy implementation for the
flow view.

I also implemented a simple text flow, you add labels with text and it
will space them evenly and divide them to rows.

How does this work
==================

**First**: You specify the `itemHeight` for all the itmes that you want
to add to the flowview.
<!--more-->

    self.flowView.itemHeight = 20; 
{:lang="ruby"}

**Second**: Create the any subclass of `UIView` and add it to the flow
view You dont specify the frame of this view, since the flow view will
calculate the frame at runtime. You will only need to specify the width
of the added view

    UIView *viewToAdd = [[UIView alloc] init]; 
    viewToAdd.backgroundColor = [UIColor redColor]; 
    viewToAdd.tag = 0; 
    [self.flowView addItem:viewToAdd withWidth:220]; 
{:lang="ruby"}

Thats it, now the views will be added to the flow view.

**Third (Optional):** You can set the delegate of the flow view to
recieve touch event on the added views.

    self.flowView.delegate = self; 
{:lang="ruby"}

The delegete function will be called when views are tapped

    - (void)flowView:(IAFlowView *)flowView didPressView:(UIView *)view 
{:lang="ruby"}

``
{% gist 4042014 %}

you can find the source
[here](https://github.com/Infusion-apps/IAFlowView)

