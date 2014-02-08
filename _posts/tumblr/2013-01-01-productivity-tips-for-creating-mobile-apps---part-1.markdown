---
layout: post
title: Productivity tips for creating mobile apps - Part 1.
tags: 
---
<p>Isn&#8217;t it annoying to manage both the retina and standard icons in your iOS application?</p>
<p>Having the designer slice both the sizes is quite annoying for both of you. and dealing with icons that have a slight not intentional difference between the retina and standard versions is time consuming.</p>
<p>Sometimes you build the app for the iPhone 4 and everything looks great, then you build the same version for iPhone 3GS  and some icons and images dont quite look right.</p>
<p>Well if you ever felt that this kind of work should be automated, then you were right. with a help of a couple of tools all of these annoying tasks will be done automatically.</p>
<p><strong>The issues that i will discuss:</strong></p>
<ul><li>Dealing with retina and standard versions.</li>
<li>Getting the color and sizes from a designer wireframe or prototype.</li>
</ul><p>After a lot of trials and errors regarding the points above i have created a subsystem of tools and scripts that does this work for me, i will share them with you and try to explain why they are so awesome.</p>
<p>In this part i will talk about the first point.</p>
<h1><strong>Dealing with retina and standard versions</strong></h1>
<p>If you ever created a mobile app then you have dealt with standard and retina images, but you dont have to do that anymore you can easily have a script or tool that batch converts all the retina icons and scales them back to standard. what you will need is only the retina version of the images from the designers.</p>
<p>You can use one of these two solutions:</p>
<ul><li>Add a custom script to xcode, this is the most elegant solution, the creation of the standard images will be done automatically, check the answer here (<a href="http://stackoverflow.com/questions/8087997/automatic-resizing-for-non-retina-image-versions">http://stackoverflow.com/questions/8087997/automatic-resizing-for-non-retina-image-versions</a>)</li>
<li>Use a standalone application. there are a lot of applications to use, some of them are free and some paid.</li>
</ul><p>               <a href="https://itunes.apple.com/us/app/resourcehelper/id521474600?mt=12">Resource helper</a> (paid)<br/>               <a href="https://itunes.apple.com/us/app/resizer/id411277085?mt=12">Resizer</a> (free)<br/>               <a href="https://itunes.apple.com/us/app/shipit!/id492043869?mt=12">Ship it</a> (paid)</p>
<p>I use Resource helper since it has a lot of amazing features that helps creating mobile apps, like icons and screenshot resizing, artwork generating and other features.</p>
<p>There are other solutions, like using Mac automator and Photoshop (<a href="http://www.youtube.com/watch?feature=player_embedded&amp;v=FVBG45Es7Jg">check video about using photoshop</a>)</p>
<p>Any of the options stated above will save you a good amount of time that you could hopefully reinvest in creating better apps.</p>
