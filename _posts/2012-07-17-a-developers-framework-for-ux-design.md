---
layout: post
title: "A developers framework for UX design"
description: ""
category: 
tags: []
---
{% include JB/setup %}

# "If you don't put yourself in the shoes of the user, you are going to create something that is delicately, and supremely, useless."

Tonight, the [hackNY fellows](http://hackny.org) were lucky enough to hear from [Whitney Hess](http://whitneyhess.com), a UX Designer from NYC. While she doesn't run a startup in the classic sense, and many NYC "mentorship programs" have turned her away for exactly that reason, I can honestly say that the discussion we had tonight was one of the top 5—if not the best—talk I have ever heard in my life. While her views were by no means revolutionary, her ability to concisely explain both *why* and *how* she tackled each step; from stakeholder discussions, to user flows, to full on designs, was so powerful that it made me drastically reconsider the way I will approach problems in the future.

In the footsteps of [Blake Masters, the Stanford student who recorded the notes for Peter Theil's Stanford class](http://blakemasters.tumblr.com), I thought I would summarize our discussion so it can be available to the greater web. While these are my words, all credit goes to [Whitney Hess](http://whitneyhess.com)—you should really, really, read [her blog](http://whitneyhess.com/blog), follow her on [twitter](http://twitter.com/whitneyhess) and see her speak.

The format of this piece will be simple: first, I'll give a broad overview of the lessons she communicated, then I'll dive into each step and explain her rationales, tips, and advice.
  
</br>
# Steps to successful UX design  
  
Whitney is of the belief that there is a consistent pattern to UX design that should be followed in nearly every situation. Here is the basic flow of her process:

1. Stakeholder interviews
    
  * talking to the owners (or decision makers) in the business to see what *they want to get out of it*
  
2. Talk to current and future customers and ask what they want
3. Turn customer interviews into "personas," which are combinations of interviews
4. From personas, create user flows and scenarios and implement flow charts
5. From user flows, create detailed outline of necessary features and net worth passed on importance to individual personas
6. From features, create wire frames that implement the features and cover every page
7. Work with visual designer to turn wireframes in to "comps"
8. Work with developers to turn "comps" into actual software

</br>
# Stakeholder interviews

Whitney describes this as one of the most important—if not the most important—steps of the UX design process. Often in a startup, the people in decision making positions can have very different agendas for product, business, and design. It's not that they actively keep their thoughts and opinions from each other, but rather in a startup environment, everyone can be so consumed in their "current tasks" that active communication can often be sidelined. This can lead to a situation where stakeholders have no idea what they are doing, or why they are doing it.

Accordingly, getting down the thoughts of each decision maker, then putting them in the same room and airing those opinions, can have the effect of realigning their goals and refocusing the agenda of the company moving forward. If you take the time to do this, even if it is before you write one line of code, it "can save more time and money that you can imagine" and it becomes easier to make "every decision be based on a logical reasoning of how it can support the business."

As an additional benefit, if you can bring the decision makers into the process early, it can be easier to get them actively involved in the UX design. Often times, stakeholders have no *empathy* for their customers; in other words, they can't imagine another person's experiences. By bringing them into the UX process, they can start to understand how to design for other people rather than themselves.

Because of these two-fold benefits, holding stakeholder interviews and discussions at the beginning of the UX design process can be crucial to success.

[FILL IN WHAT THE QUESTIONS TO ASK ARE]

</br>
# Talk to current and future customers and ask what they want

Whitney's main principle for customer interviews is "that if you're hearing new insights and thoughts from the people you're interviewing, you need to keep interviewing." Only when you start learning nothing new with every interview can you transition to the next step.

So, who do you interview and how do you reach them?

First off, the existing customer base should *always* be taken into account if they will be beneficial to the business moving forward. Not only do you not want to alienate them as you start designing new aspects of the product, they also have the most experience with what you've built thus far, where it succeeds, and where it fails. 

</br>
## Two ways to reach your existing users
</br>

  1. *Send out a survey that asks questions, then have a field that says "enter your email if you're interested in giving more feedback."*

This strategy can be very effective to get talkative users; however, it can also have an unintended filtering effect. Often times, the people who are interested in actively engaging in discussion about your product are not the ones you need to talk to. Rather, it's the people who may be aloof, who are feeling the UX inconsistencies, who's feedback can be the most valuable.

  2. *Break open the database, filter based on user patterns like extended inactivity, and handpick users to reach out to.*

While this strategy may have a lower return rate, it can often provide much more valuable feedback—don't be afraid to reach out to people, the worst that can happen is that they don't respond.

</br>
## How to reach future users

This step can be the hardest for new founders: often times it will be awkward and most times you have no idea where to start. As a first step, Whitney suggests **using twitter to reach potential customers**. With this network, it can be easy to reach people who are not your close friends, but are still in your broader network, so you can tell some sort of specifics about what they are looking for.

For instance, you could tweet "I'm looking for graduating college students who are trying to figure out their career plans, please help me by retweeting." If you have a solid network of followers, a tweet like this—or a few spread out over a week—can bring in a solid set of 2nd or 3rd degree connections whom you can then filter based on qualities.

After twitter, going out in public—like to Starbucks—can also be extremely valuable. Hang around, and when you see someone finishing up their coffee, walk up to them and say:

*"I see that you're a little low on coffee, can I buy you a cup and have you test out this app"*

More often than not, people will be willing, if not overjoyed, to help you out.

Finally, if you're just looking to do usability testing, you might want to turn to someone like the HR person in your company (if it's big enough!). Often times, they have little exposure to product decisions, and their uneducated feedback can be hugely valuable.

Once you stop learning new things, move on to the next step.

</br>
# Turn the interviews into "personas"

As Whitney describes it, a persona is a mood that someone is in at a given point of time. One of her key points is that a persona is a psychographic distinction rather than a demographic split. 

As an example, take a college website. Often times, the navigation will be divided into students, parents, alumni, prospects, and a few other categories. In reality, all of these people are trying to access the same information, so there is no real reason to impose artificial divisors. Instead, personas should be based on the motivations and needs of individual groups of users. 

With your set of interviews, start to focus the users into "primary" and "secondary" personas. The primary personas should be the ones you dedicate the majority of UX design to. While the needs of the secondary personas should be considered, they *can* be ignored. For each persona, rather than visualize them as an abstract set of needs, *actually craft the persona into a real (fake) person*. Give them a name, a history, a set of habits, needs, and wants. Once you have a concrete identity, it becomes much easier to see how said persona will interact with different user flows. This is important.

At this point, you may be wondering how you craft personas if your business is B2B. Hess believes that, when you really dig deep, a company is a persona too. In reality, a company is a collection of humans, with probably a few leading personalities, who make decisions as a whole. Therefore, there's no real reason to treat companies any different from individual users.

Once you have these primary and secondary personas, start creating user scenarios. Every user case should start with "I want to." For instance,

"I want to quickly order food online."
"I want to order the thing I ordered last time."
"I want to..."
etc
etc

These clearly defined *wants* give a framework for creating the necessary features to implement.

</br>
# For each user case, craft the necessary feature requirements

Here, you really want to collect every "feature" across every area of the site. These features can be anything from "log in" to "sort by first letter." Write 'em down.

Now, create a spreadsheet with all the features on the y-axis. On the x-axis, put columns for your primary personas, one column for "tech effort," and one column for "feature status."

Next, weight your personas by importance. For instance, if you think one persona is 3/2 more important than the other, make it worth 3 points and the other worth 2.

For each feature, go through and rate each feature, for each persona:

  - 2 -> love the feature
  - 1 -> like and expect the feature
  - 0 -> no feeling
  - -1 -> hate the feature
  
Now, add up the total, weighted, points for each feature and sort by number of points. From here, with the additional data on tech effort, you can go through and group the features into 4 categories:

  - "Must have"
  - "Should have"
  - "Nice to have"
  - "Won't have"
  
The entire process may take awhile, but at the end you'll have an ordered list of all the features you need and want to implement. Pretty valuable.

</br>
# Create your detailed flow diagrams

With the features outlined, you can start considering the larger picture. For each persona, imagine all of the possible ways they could enter, and exit, your service—and everything in between. Create flow charts. They are awesome.

</br>
# From the flow diagrams, create your wireframes

With features outlined, and flow diagrams completed, the entire vision should be nearing completion. At this point, you should create wireframes for each view/step on your flow diagram.

Here is where things trail off a little for me...obviously, creating wireframes that have "good UX" is a finely honed skill. Yes, the first step is understanding your personas, but even with that understanding, it can be nearly impossible to translate that to wireframes if you don't have experience. Here, you may actually want to go to an expert.

</br>
# Translate the wireframes into beautiful comps

Work with a visual designer.

</br>
# Build your product

That's what your best at, now make it happen.







