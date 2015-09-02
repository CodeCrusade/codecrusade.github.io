---
layout: post
title: "stop using bootstrap"
date: 2015-09-02 13:41:22 -0500
comments: true
categories: 
---

TLDR: Let SCSS DRY up your markup and keep your styles where they
belong, in your css

You love Bootstrap. I love Bootstrap. It's fantasic for getting a 
site out the door quickly with some nice styling. BUT....
How often have you seen this uglyness?

```html
<div class="container">
    <div class="row">
        <div class="col-sm-10">
            Lorem Ipsum
        </div>
        <div class="col-sm-2">
            <ul>
                <li>Morem Ipsum</li>
            </ul>
        </div>
    </div>
</div>
```

This is nearly as bad as all the style= tags from a few years back. You 
are explicitly tying your stying to your markup and making a hard to 
maintain mess. Now when you need to change to your new design fresh from
your new marketing team, you have a million html files that need to be
updated to the new style. This is a serious violation of the
[Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle)

So, how can we DRY this up and make our design more flexible and more
accepting of change. Easy, it's built in.  SCSS and LESS both support syntax
for inheriting properties. Lets see what this would look like with a bit of
SCSS help.

```scss
.content {
  @extend col-sm-10;
}
.sidebar {
  @extend col-sm-2;
}
```

```html
<div class="container">
    <div class="row">
        <div class="content">
            Lorem Ipsum
        </div>
        <div class="sidebar">
            <ul>
                <li>Morem Ipsum</li>
            </ul>
        </div>
    </div>
</div>
```

There is no need to override Bootstrap where their classes make
sense in your code (for example row), but now you have contextual
anchors in your markup that mean something to your applicaton
and when the time comes for change, you only have to change the scss 
directives making changes and upgrades much easier.



