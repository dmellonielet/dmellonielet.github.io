---
layout: post
title: "Writing Terrible Documentation"
date: 2021-11-30 03:00:00 -0000
author: "Nielet D'mello"
tags: ['software engineering', 'technology']
image: /images/write.jpg
---

![Documentation](/images/write.jpg "Photo by Florian Klauer on Unsplash")


Almost every engineering culture these days somewhat hinges on documentation. It serves as means of effective knowledge sharing, communicating key design decisions and changes. There's a lot of good content out there on what makes good engineering documentation. Yet, too often, we come across documentation that falls short on so many aspects.


I have first-hand seen the criticality of good documentation for scaling up an initiative and getting broader outreach. 
Sometimes, we write a lot of rich docs and still encounter reader feedback that it's too complicated and feels terrible to read.

This post is my attempt to distill some common feedback I've reviewed, so here's the 411 on writing terrible documentation as an engineer. :memo:

### Do not understand your target audience
This one is quite nuanced and depends on the scale and reach of your work. If something you are working on as an engineer spans across the company or organization, chances are your target audience will vary in terms of their domain expertise and levels. You may skip asking these questions- 'Who will read this documentation? Why? What user experience are we aiming for?'. In such cases, taking a one-size-fits-all approach is the best recipe for making the docs terrible. 

### Assume readers have a lot of contexts
Context varies. The readers probably already know about some design decisions or underlying related concepts. However, if you look to exercise the curse of knowledge, you can assume your reader already know a lot and make no explicit attempts to provide context. Even better if there's outdated or partial documentation on the topic.

### Make it complicated
The best way to make your readers lose their train of thought is to write long, complicated sentences. Skip the urge to simplify sentences so your readers can incur a ton of cognitive overload. Do not provide visual guides and illustrations. It will only make it easy for readers to grasp concepts.

### Do not categorize
If your project has many components, keeping the information scattered all over the place will keep the users struggling to connect the dots.
Almost always, readers are looking to find information on a topic. For example: getting started guides, runbooks,  FAQs, etc. By not categorizing relevant information, make it harder for readers.

### Make navigation complicated 
Try not to surface the most relevant information first. Thinking about first-time user experience (FTUE) is useless. Send readers down the rabbit hole of links when trying to navigate documentation. It's the perfect way to have readers lost in the weeds and forget what exactly it is that they started reading in the first place. 

### Skip references and helpful links
Tying back to the idea of context, skipping references and guides is best to leave the readers with incomplete knowledge.

### Discard feedback
Last but not least, do not seek feedback because it will involve some points listed above. Try not to give a mechanism for readers to provide feedback. If they do, ignore it. 


There you have it- A perfect recipe for writing terrible documentation. :dart: