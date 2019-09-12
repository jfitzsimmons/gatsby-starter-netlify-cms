---
templateKey: blog-post
title: 'Lessons in Animation: JS, CSS & jQuery'
date: 2019-09-10T21:52:09.107Z
description: The accuracy of JavaScript vs. the efficiency of CSS and jQuery
featuredpost: true
featuredimage: /img/projectbackground.jpg
tags:
  - performance
  - style
  - animation
---
I aimed for a relaxing, eye catching animation that would be like staring at a fish tank. I started experimenting with HTML5 Canvas, JS and CSS animations. My first and coolest iteration was pure javascript. A circle would grow from a random point on the screen, change hue, and lightness, create a border at a random point around the circle, and then move away from that point at a random speed. It would then bounce around the screen in perpetuity.

I loved the way this animation looked but it was too resource intensive. I then experimented with similar functionality, but using CSS. I couldn’t make the circle move at an angle quite as precisely as pure JS. To mimic the functionality, I split the screen into four quadrants. If the circle was generated in a specific quad, it would move across the screen diagonally towards the furthest quad. The circle would move at a random speed on both the x and y axis creating random angles, while moving away from the starting point, although not quite as precisely as the JS animation.

The problem with this animation style is that it’s not much more efficient than the JS animation. This is because animating the properties of top/left/width/height (properties that affect document flow) are more resource intensive than transforms due to current web and browser standards.

So, I added another css animation that only uses transform. This animation wouldn't bounce off the sides of the window, but would instead, revolve 360 degrees. This time I split the screen in half. If the circle was generated in the right half of the screen, the starting point would be at the top of the circle and the circle would move down. If it generated on the left side, the starting point would be at the bottom of the circle and move up. Also, if the circle is closer to the center of the screen, it has a wider orbit than at the edge of the screen. This is to increase to amount of time the circle remains in view.

This animation is far less intensive than the prior two, though not as cool looking in my opinion. So now I decided to use all three animations. Each time a circle is created, it randomly uses one of the three types of animation. I weighted the css transform animation to show up twice as much as the other two in order to save resources.

One other resource consideration was to change the number of circles generated based on screen size. This might help with performance on mobile devices.

Some other highlights. I heavily leaned on randomization. The circles grow to different sizes. The hue and lightness of the circles change as the circle grows. This makes each circle a unique color, but still fit with the style of the site. There are three different border colors that are chosen at random. I mentioned the different starting points of the border, and the different animations, speeds and angles each circle has.
