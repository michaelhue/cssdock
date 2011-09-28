# CSS Dock (V2)

An experiment mimicking the Dock of OS X using only CSS. Labels, animations, reflections and indicators... it's all there.

## How does it work?

Glad you asked. The dock makes heavy use of the following sweet CSS techniques:

* _Transforms_, _Transitions_ and _Animations_ for the magnification and bouncing effects.
* `:before` and `:after` pseudo-classes to keep the HTML markup clean and display the status indicator.
* `:target` pseudo class to determine which item is active.
* `-webkit-box-reflect` for the reflection of the icons.

## Details, give me details!

Alright, let's walk through this together. The dock is basically an unsorted list with each list item representing one icon. Every item and the list itself gets the `display: inline-block;` property to act like an inline element while preserving their block capabilities. This allows us to use `text-align: center;` in order to keep the items centered and `vertical-align: baseline;` to keep all items at the bottom at any time. This is important so the other items won't "lift off" when one them is enlarged.

On mouseover the corresponding image is enlarged while a transition applied to `width` and `height` ensures a smooth animation. On mouse-out the image transitions back to its original size which results in a nice little magnification effect.

The icon reflection only works in WebKit because of it's proprietary (but kind of awesome) `-webkit-box-reflect` property. A gradient is used as a mask in order to cut off the status indicator, so it won't be part of the reflection.

The bouncing effect is a simple CSS animation which uses the `transform` property to move the item a few pixels to the top. The status indicator is an element generated in CSS and inserted after the active item. But how do we know which item is active? This is where it gets a bit tricky.

CSS gives us an underestimated pseudo-class named `:target`. You all know how we can use URIs to refer to an element within the page, right? An example: the link `<a href="#about">` brings us to the element with the `id` _about_. The bit after `#` is called _fragment identifier_ which is represented by the _id_ attribute on elements. As soon as you click on this link, the _about_ element becomes the current target and CSS applies the `:target` pseudo-class to it.

So when you click on an item in the dock you actually click on a link that refers to it's parent `li` element, which in turn triggers the bounce animation using `:target`, repeats it three times and creates the status indicator below the icon.

And that's all, folks. Be sure to check the source file, lots of comments in there to get you started. And it's actually not that much code.

## But is it actually... you know, useful?

Probably not, at least not without modifications. This is just a quick demonstration to show what's possible using modern web technologies. Use this experiment as a starting point and go bat-shit crazy. I highly encourage it!

I'd love to see what you come up with so please shoot me a line in case you did indeed go bat-shit crazy.

## How about compatibility?

You love to be the party pooper, don't you? Just kidding. The dock works best in current WebKit browsers (Safari and Chrome) but the good news is: it degrades quite gracefully. So while you won't get all effects in all browsers, the experience won't be broken either (except for IE, of course). A quick overview:

* Chrome 12 (Full Support)
* Safari 5 (Full Support)
* Firefox 5 (Advanced Support; no reflections)
* Opera 11 (Basic Support; no reflections and animations)

## Anything else?

Why yes! Thanks a bunch to [Iconsutra](http://iconsutra.com) for letting me use his wonderful MobileMe icon set and also to [Wolfgang Bartelme](http://bartelme.at) who allowed me to use his gorgeous [Flow Wallpaper](http://bartelme.at/journal/archive/flow_wallpaper).

And not to forget all of you guys who gave me feedback and spread the word. Thank you!