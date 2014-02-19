---
layout: post
title: "Help! My tables don't scroll smoothly!"
date: 2013-07-29 01:49:26 +0300
comments: true
categories: 
---

We all faced times when our `UITableView` didn’t scroll as we wanted to.
I gathered bellow a simple yet thorough article about what may causes
that.

Why is my scroll slow? When you create custom `UITableViewCell` and you
use a combination of UIViews and UIImages, you may cause UIKit to do
extra *Offscreen rendering*.

<!--more-->

### What is Offscreen rendering:

Simply put, is to generate images using Software process neglegting any
Hardware acceleration boost.

### Types of Offscreen rendering:

-  CPU offscreen, using the CPU to generate images:
    -  Using `Core Graphics`
    -  Anything inside `drawRect`
-  GPU offscreen (Blending), the GPU will have to calculate the final
    image, adds shadow, clips, etc…:
    -  Layers with `shouldRasterize`
    -  `cornerRadios`, `masks`, `shadows`, `edge antialiasing`

### Offscreen impact on performance:

Offscreen rendering impacts the performance when its getting done on
each frame, in scrolling or animation. but if its done and cached, it
may enhance performance.

### But hey!

We still need to create custom `UITableViewCell`, fear not the bellow
list shows the ways we can achieve that ordered in performance cost.

### Customisation methods ordered by performance:

-  Use resizable image and normal images
-  Use a combination of `opaque`, `non-transparent` `UIView`s.
-  Use Hybrid mode: Use `CoreGraphics` and code to create stretchable
    images that you will `cache/purge`
-  use `CALayer` **only** if you need animation
-  Worst! Draw using `CoreGraphics` inside `drawRect`

### Major reasons for slow scroll, And their solutions:

-  Slow cell creation.
    -  `Offscreen` creation of cell takes too long:\
         to solve this issue simplify the drawRect.
    -  Too complex `drawRect` function:\
         Cache any result from `drawRect` and reuse it.
    -  Too complex view hierarchy:\
         Try to flatten the view hierarchy.
-  Slow cell movements.
    -  offscreen gets called in each cell:\
         Use hybrid mode from above and cache the images.
    -  too many blending operations:\
         Make views opaque and `rasterize` the layers.

### Tips for fast scrolling:

1. Recycle cells.
2. Avoid transparent images, views, make them `opaque`.
3. Configure the reused cell must be fast.
4. Always make most of the views `opaque`, avoid `alpha` and
    `clearColor`.
5. Don’t place views on fractions of pixels x = 34.5, always use ceil
    or floor on pixels.
6. When setting images adjust them (Scale, Clip) after download and
    before setting them, don’t let iOS scales them down.
7. Scrolling images is faster than views, however the difference is
    very small if views are `opaque`.
8. Use `shouldRasterize` on layer whenever you can since rasters of the
    layer will be cached and reused, But remember if you enable
    `shouldRasterize` on layers that changes their `content` or
    `sublayer` `content` frequently you will add cause the performance
    to drop, since iOS will keep rasterising the layer on each change.

Refs:

-  [http://stackoverflow.com/questions/6731545/when-does-a-view-or-layer-require-offscreen-rendering](http://stackoverflow.com/questions/6731545/when-does-a-view-or-layer-require-offscreen-rendering)
-  [http://stackoverflow.com/questions/17593524/using-cornerradius-on-a-uiimageview-in-a-uitableviewcell?lq=1](http://stackoverflow.com/questions/17593524/using-cornerradius-on-a-uiimageview-in-a-uitableviewcell?lq=1)
-  [http://robots.thoughtbot.com/post/33427366406/designing-for-ios-taming-uibutton](http://robots.thoughtbot.com/post/33427366406/designing-for-ios-taming-uibutton)
-  [http://robots.thoughtbot.com/post/36591648724/designing-for-ios-graphics-performance](http://robots.thoughtbot.com/post/36591648724/designing-for-ios-graphics-performance)
-  [http://stackoverflow.com/questions/10563986/uiimage-with-rounded-corners](http://stackoverflow.com/questions/10563986/uiimage-with-rounded-corners)
-  [http://blogs.captechconsulting.com/blog/john-szumski/performance-tuning-older-ios-devices](http://blogs.captechconsulting.com/blog/john-szumski/performance-tuning-older-ios-devices)
-  [Apple Developer Improving Drawing
    Performance](https://developer.apple.com/library/IOS/#documentation/2DDrawing/Conceptual/DrawingPrintingiOS/DrawingTips/DrawingTips.html)
-  [Apple Developer shouldRasterize
    property](https://developer.apple.com/library/mac/documentation/graphicsimaging/reference/CALayer_class/Introduction/Introduction.html#//apple_ref/occ/instp/CALayer/shouldRasterize)


