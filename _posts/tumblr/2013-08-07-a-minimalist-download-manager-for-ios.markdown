---
layout: post
title: A Minimalist download manager for iOS
tags: 
---
<p>Download a set of files in parallel or sequential order.</p>

<h2>Why i created this</h2>

<p>Ever wanted to download a set of images in a parallel or sequential order, like creating a table cell view that resembles Facebook timeline cell that contains multiple images.</p>

<p><img src="http://i1348.photobucket.com/albums/p740/o_abdelhafith/Slice1_zps0027ff00.png" alt="Time line"/></p>

<p>If you tried to create such thing, then you realised that some images has to be downloaded before the others, namely the first image in the timeline cell must be downloaded before the second image in this same cell (remember we have multi images inside the same cell)</p>

<h3>Introducing the IADownloadManager</h3>

<p>MY first approach was to create a parallel download manager, this manager will download any set of unique URLs in a parallel order.</p>

<p>This worked fine now multiple images will be downloaded asynchronously, but raised a new issue, since we have multiple images on the same cell, it may be possible that the 2nd image will be downloaded before the first image, the user will not be able to notice the 2nd image since it will be mostly out of bounds.</p>

<h3>Introducing the IASequentialDownloadManager</h3>

<p>The second approach was by downloading a set of images in a sequential order, best way to do this i figured was using <code>NSOperationQueue</code>,</p>

<p>So i for each time i wanted to download a <code>NSArray</code> of <code>NSURL</code>, I would create an <code>NSOperationQueue</code> with <code>maxConcurrentOperationCount</code> set to one, each <code>NSURL</code> download operation would be added to this queue.</p>

<p>This would create a sequential download order for the items of the array.</p>

<p>So to sum thins up.</p>

<ol><li><strong>IADownloadManager</strong> downloads a set of URLS in a parallel order.</li>
<li><strong>IASequentialDownloadManager</strong> downloads a set of URLS in a sequential order.</li>
</ol><h2>What it provides</h2>

<ul><li>Easy to integrate and use iOS download manager.</li>
<li>Easily download file with the very robust <a href="https://github.com/AFNetworking/AFNetworking">AFNetworking</a> library.</li>
<li>Deal only with NSURL, you will never have to keep strong or weak references of the Download managers.</li>
<li>Download files in sequential and parallel order.</li>
<li>Make sure each file (NSURL) is being downloaded only once.</li>
<li>Have multiple listener/delegates on a single download operation.</li>
<li>Download operation unique by URL, never download a URL twice.</li>
<li>Cache the downloaded file in Memory and on Disk using <a href="https://github.com/enormego/EGOCache">EGOCache</a>.</li>
<li>Easily add and remove listeners to observe the download operations.</li>
<li>Singleton classes for fast access and minimum memory overhead.</li>
<li>Ensure that the UI Thread is never blocked.</li>
<li>Delegate or Block event callbacks.</li>
<li>All of the above in two lines of code.</li>
</ul><h3>Demoes and code.</h3>

<p>To get the demos and code surf to <a href="https://github.com/Infusion-apps/iOS-Download-Manager/">The repository</a></p>
