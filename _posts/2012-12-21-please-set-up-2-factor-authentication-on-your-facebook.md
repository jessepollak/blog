---
layout: post
title: "Please set up 2-factor authentication on your Facebook"
description: ""
category:
tags: []
---
{% include JB/setup %}

Today, while messing around with the new Facebook privacy settings, I stumbled across the ability to setup 2-factor authentication for my Facebook account. Evidently, this feature was [introduced in May](https://www.facebook.com/note.php?note_id=10150172618258920), but up until yesterday I never knew it existed.

With the fast growing trend towards using your Facebook account as a single-sign-on provider to enable account creation and access on other web services, the security of your Facebook account is paramount. If a hacker were to gain control of it, they would most likely gain control of a huge swath of services you use on a daily basis (at least for me that's the case).

2-factor autentication provides an additional layer of security: while before if a hacker discovered your password, they could log in as you on any computer with no problems, with 2-factor authentication they need a second form of identification (in this case, your mobile phone). Essentially, any time you log into a new computer, your phone gets a SMS with a confirmation code, which you then type in and your login is confirmed. Without your phone, a hacker will never be able to access your account.

Right now, you're probably thinking that that sounds like a pain in the ass: luckily, Facebook makes adding verified computers a breeze, so you won't have to do the 2-factor authentication on computers you approve (like your personal computer). Obviously, this reduces the security a bit, but the main goal is still achieved.

Setting up 2-factor authentication on your Facebook is super easy, just follow these steps.

In the right header, click the lock icon to access the new privacy panel:

![lock](http://cl.ly/image/3g210r3S1Q3s/Screen%20Shot%202012-12-21%20at%205.08.47%20PM.png)

Next, click the 'See More Settings' link:

![see more settings](http://cl.ly/image/0M1f0w2E1O0s/Screen%20Shot%202012-12-21%20at%205.08.47%20PM.png)

In the left navigation panel, click the security link:

![security link](http://cl.ly/image/2c2h3L0P0I31/Screen%20Shot%202012-12-21%20at%205.11.20%20PM.png)

Now, click the edit next to 'Login Approvals' and follow the steps that Facebook provides;

![login approvals](http://cl.ly/image/0T1Y0Q2I3Y33/Screen%20Shot%202012-12-21%20at%205.13.09%20PM.png)

Enjoy your newly secured Facebook account!

<p class='endnote'>PS. if you're interested in checking out a 2-factor authentication system that is easier to use than usernames and passwords, check out <a href='https://clef.io'>Clef</a>, the startup I'm working on right now.</p>