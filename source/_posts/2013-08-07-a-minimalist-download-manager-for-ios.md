---
layout: post
title: "A Minimalist download manager for iOS"
date: 2013-08-07 01:49:26 +0300
comments: true
categories: 
---

Download a set of files in parallel or sequential order.

Why i created this
------------------

Ever wanted to download a set of images in a parallel or sequential
order, like creating a table cell view that resembles Facebook timeline
cell that contains multiple images.

<!--more-->

![Time
line](http://i1348.photobucket.com/albums/p740/o_abdelhafith/Slice1_zps0027ff00.png)

If you tried to create such thing, then you realised that some images
has to be downloaded before the others, namely the first image in the
timeline cell must be downloaded before the second image in this same
cell (remember we have multi images inside the same cell)

Introducing the IADownloadManager
----------------

MY first approach was to create a parallel download manager, this
manager will download any set of unique URLs in a parallel order.

This worked fine now multiple images will be downloaded asynchronously,
but raised a new issue, since we have multiple images on the same cell,
it may be possible that the 2nd image will be downloaded before the
first image, the user will not be able to notice the 2nd image since it
will be mostly out of bounds.

Introducing the IASequentialDownloadManager
----------------

The second approach was by downloading a set of images in a sequential
order, best way to do this i figured was using `NSOperationQueue`,

So i for each time i wanted to download a `NSArray` of `NSURL`, I would
create an `NSOperationQueue` with `maxConcurrentOperationCount` set to
one, each `NSURL` download operation would be added to this queue.

This would create a sequential download order for the items of the
array.

So to sum thins up.

1. **IADownloadManager** downloads a set of URLS in a parallel order.
2. **IASequentialDownloadManager** downloads a set of URLS in a
    sequential order.

What it provides
----------------

-  Easy to integrate and use iOS download manager.
-  Easily download file with the very robust
    [AFNetworking](https://github.com/AFNetworking/AFNetworking)
    library.
-  Deal only with NSURL, you will never have to keep strong or weak
    references of the Download managers.
-  Download files in sequential and parallel order.
-  Make sure each file (NSURL) is being downloaded only once.
-  Have multiple listener/delegates on a single download operation.
-  Download operation unique by URL, never download a URL twice.
-  Cache the downloaded file in Memory and on Disk using
    [EGOCache](https://github.com/enormego/EGOCache).
-  Easily add and remove listeners to observe the download operations.
-  Singleton classes for fast access and minimum memory overhead.
-  Ensure that the UI Thread is never blocked.
-  Delegate or Block event callbacks.
-  All of the above in two lines of code.

### Demoes and code.

To get the demos and code surf to [The
repository](https://github.com/Infusion-apps/iOS-Download-Manager/)

