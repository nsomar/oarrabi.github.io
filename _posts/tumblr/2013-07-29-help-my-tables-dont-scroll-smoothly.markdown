---
layout: post
title: Help! My tables don't scroll smoothly!
tags:
- ios
- mobile
- perfromance
- enchance
- table
- scroll
- smooth
---
<p>We all faced times when our <code>UITableView</code> didn&#8217;t scroll as we wanted to. I gathered bellow a simple yet thorough article about what may causes that.</p>

<p>Why is my scroll slow? When you create custom <code>UITableViewCell</code> and you use a combination of UIViews and UIImages, you may cause UIKit to do extra <em>Offscreen rendering</em>.</p>

<h3>What is Offscreen rendering:</h3>

<p>Simply put, is to generate images using Software process neglegting any Hardware acceleration boost.</p>

<h3>Types of Offscreen rendering:</h3>

<ul><li>CPU offscreen, using the CPU to generate images:

<ul><li>Using <code>Core Graphics</code></li>
<li>Anything inside <code>drawRect</code></li>
</ul></li>
<li>GPU offscreen (Blending), the GPU will have to calculate the final image, adds shadow, clips, etc&#8230;:

<ul><li>Layers with <code>shouldRasterize</code></li>
<li><code>cornerRadios</code>, <code>masks</code>, <code>shadows</code>, <code>edge antialiasing</code></li>
</ul></li>
</ul><h3>Offscreen impact on performance:</h3>

<p>Offscreen rendering impacts the performance when its getting done on each frame, in scrolling or animation. but if its done and cached, it may enhance performance.</p>

<h3>But hey!</h3>

<p>We still need to create custom <code>UITableViewCell</code>, fear not the bellow list shows the ways we can achieve that ordered in performance cost.</p>

<h3>Customisation methods ordered by performance:</h3>

<ul><li>Use resizable image and normal images</li>
<li>Use a combination of <code>opaque</code>, <code>non-transparent</code> <code>UIView</code>s.</li>
<li>Use Hybrid mode: Use <code>CoreGraphics</code> and code to create stretchable images that you will <code>cache/purge</code></li>
<li>use <code>CALayer</code> <strong>only</strong> if you need animation</li>
<li>Worst! Draw using <code>CoreGraphics</code> inside <code>drawRect</code></li>
</ul><h3>Major reasons for slow scroll, And their solutions:</h3>

<ul><li>Slow cell creation.

<ul><li><code>Offscreen</code> creation of cell takes too long:<br/>
to solve this issue simplify the drawRect.</li>
<li>Too complex <code>drawRect</code> function:<br/>
Cache any result from <code>drawRect</code> and reuse it.</li>
<li>Too complex view hierarchy:<br/>
Try to flatten the view hierarchy.</li>
</ul></li>
<li>Slow cell movements.

<ul><li>offscreen gets called in each cell:<br/>
Use hybrid mode from above and cache the images.</li>
<li>too many blending operations:<br/>
Make views opaque and <code>rasterize</code> the layers.   </li>
</ul></li>
</ul><h3>Tips for fast scrolling:</h3>

<ol><li>Recycle cells.</li>
<li>Avoid transparent images, views, make them <code>opaque</code>.</li>
<li>Configure the reused cell must be fast.</li>
<li>Always make most of the views <code>opaque</code>, avoid <code>alpha</code> and <code>clearColor</code>.</li>
<li>Don&#8217;t place views on fractions of pixels x = 34.5, always use ceil or floor on pixels.</li>
<li>When setting images adjust them (Scale, Clip) after download and before setting them, don&#8217;t let iOS scales them down.</li>
<li>Scrolling images is faster than views, however the difference is very small if views are <code>opaque</code>.</li>
<li>Use <code>shouldRasterize</code> on layer whenever you can since rasters of the layer will be cached and reused, But remember if you enable <code>shouldRasterize</code> on layers that changes their <code>content</code> or <code>sublayer</code> <code>content</code> frequently you will add cause the performance to drop, since iOS will keep rasterising the layer on each change. </li>
</ol><p>Refs:</p>

<ul><li><a href="http://stackoverflow.com/questions/6731545/when-does-a-view-or-layer-require-offscreen-rendering">http://stackoverflow.com/questions/6731545/when-does-a-view-or-layer-require-offscreen-rendering</a></li>
<li><a href="http://stackoverflow.com/questions/17593524/using-cornerradius-on-a-uiimageview-in-a-uitableviewcell?lq=1">http://stackoverflow.com/questions/17593524/using-cornerradius-on-a-uiimageview-in-a-uitableviewcell?lq=1</a></li>
<li><a href="http://robots.thoughtbot.com/post/33427366406/designing-for-ios-taming-uibutton">http://robots.thoughtbot.com/post/33427366406/designing-for-ios-taming-uibutton</a></li>
<li><a href="http://robots.thoughtbot.com/post/36591648724/designing-for-ios-graphics-performance">http://robots.thoughtbot.com/post/36591648724/designing-for-ios-graphics-performance</a></li>
<li><a href="http://stackoverflow.com/questions/10563986/uiimage-with-rounded-corners">http://stackoverflow.com/questions/10563986/uiimage-with-rounded-corners</a></li>
<li><a href="http://blogs.captechconsulting.com/blog/john-szumski/performance-tuning-older-ios-devices">http://blogs.captechconsulting.com/blog/john-szumski/performance-tuning-older-ios-devices</a></li>
<li><a href="https://developer.apple.com/library/IOS/#documentation/2DDrawing/Conceptual/DrawingPrintingiOS/DrawingTips/DrawingTips.html">Apple Developer Improving Drawing Performance</a></li>
<li><a href="https://developer.apple.com/library/mac/documentation/graphicsimaging/reference/CALayer_class/Introduction/Introduction.html#//apple_ref/occ/instp/CALayer/shouldRasterize">Apple Developer shouldRasterize property</a></li>
</ul>
