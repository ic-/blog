---
title: scrollView
date: 2017-02-20 18:39:33
tags: 
    - scrollView 
    - css  
categories: css
commit: false 
---

### scrollIntoView
- Syntax
    - event.target.scrollIntoView()
    - document.getElementById('demo').scrollIntoView()
<!--more-->
- Parameters
    - scrollIntoView()
    - scrollIntoView(alignToTop)
        - true //align to the top of the visible area
        - false //align to buttom of the visible area
    - scrollIntoView(scrollIntoViewOptions)
        - scrollIntoViewOptions
            - bool/object
            - {
            behavior: "auto" | "instant" | "smooth",
            block: "start" | "end",
            }
            - {block: "start"} === false
            - {block: "end"} === true




