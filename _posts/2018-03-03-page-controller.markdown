---
layout: post
title:  "Autolayout using code"
date:   2018-03-03 15:25:00 +0800
categories: autolayout
---
The whole context of this problem is :
```
private func setupViews() {
//        view.translatesAutoresizingMaskIntoConstraints = false
    view.backgroundColor = .white

    imageView.backgroundColor = .yellow
    view.addSubview(imageView)
    constrain(imageView, view) { imageView, view in
        imageView.left == view.left
        imageView.right == view.right
        imageView.top == view.top
        imageView.height == imageView.width
    }
    ...
```
I try this code to auto-layout using code.
the view is inside a UIPageController using code only, not any storyboard.

So just forget this one and can not make it auto-layout work well

So note for me in this case is :
Need read the documentation of Apple again to remember about the SDK

Instance Property
translatesAutoresizingMaskIntoConstraints
A Boolean value that determines whether the view’s autoresizing mask is translated into Auto Layout constraints.

About [translatesAutoresizingMaskIntoConstraints][link]

[link]: https://developer.apple.com/documentation/uikit/uiview/1622572-translatesautoresizingmaskintoco
