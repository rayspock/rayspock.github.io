---
title: "Some Thoughts on Using Event Sourcing" 
date: 2022-05-23
tags: ["blog", "experience", "developer", "event-sourcing", "journey", "architecture"]
share_img: posts/event-sourcing/hasnain-sikora-time-machine-unsplash.jpg
summary: "About a year ago, I started to work with event sourcing and built a system around it. It seemed quite..."
---

![image](hasnain-sikora-time-machine-unsplash.jpg)
<div class="cn"><sub>
Photo by <a class="au lc" target="_blank" href="https://unsplash.com/@hasnainsikora?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Hasnain Sikora</a> on <a class="au lc" target="_blank" href="https://unsplash.com/s/photos/delorean?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
</sub></div>

<br/>

About a year ago, I started to work with event sourcing and built a system around it. It seemed quite new to me, but the more I learned, the easier it became. Basically, I've already worked with event sourcing for my entire career as a software engineer even starting at school, however, I didn't realise it at that time.

As long as you have coding experience you should be able to work with version control systems such as Git, which enables event sourcing. Every commit you push to Git is stored as an event representing a change that can be added, edited or removed from files or code. This is the core concept of event sourcing where you can source back all the events that have happened in the past. As a result of this, we can revert the changes that have been made in the code from git whenever needed - Just like a time machine isn’t it ;)

The sooner you master Git the quicker it makes your life easier. It had my back a few times in my career and saved a lot of time :) I highly recommend this to those who want to work as a developer and spend some time cultivating it. I digress a little bit here. Let's talk about when to use event sourcing. It’s not a silver bullet that allows you to solve any problem, it really does add complexity to your system, so make sure you think through the goal you want to achieve that can be solved by it before adopting it.

The first scenario where you might use event sourcing is when you want full audit trails in your system like with payment or banking. This is also the core reason why I adopt it in my work. We have different records and transactions, including finance, accounting and medical, that must be tracked and verified.

The second one is reporting. With event sourcing, you have way more insights into your data, and you can generate reports retroactively. Just like data mining where you extract significant information from a collection of data.

The third scenario is parallel processing. Every microservice communicates through event messages, so they are in a loose couple style without depending on each other. Suppose you are looking for a highly scalable solution, this could potentially satisfy horizontal scalability and resilience to system failure.

Are there other problems that can be solved by event sourcing? Tell me what you think and I hope this blog will inspire you to explore solutions for your use cases.