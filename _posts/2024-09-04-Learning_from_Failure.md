---
title: "Learning from Failure"
category: Software
date: 2024-09-04 15:41:00 -0300
comments: true
description: Learning from Failure.
tags:
    - Culture
---

<img src="/images/posts/79E96BD0-8358-4EEA-9F1F-CE1E8A8E9FA9/9FEEA64F-4EBF-41CE-997B-3B459D42C923.jpg" width="590" alt="Kids playing with blocks"/>

> “Your first 10,000 photographs are your worst.”
― Henri Cartier-Bresson

I always loved this quote. Although Henri Cartier-Bresson was referring to a different craft (photography), it still resonates deeply right from the start. It is a powerful philosophy which I live by and try to apply in every project that I'm involved with.

There's always room to improve. The trick is to look back in search for clues on where to go next.

And in the same way as with photographs, your 10,000 deploys will be your worst. As a software engineer, it is important to keep track of your software development life cycle process and to be prepared when an emergency arrives. We've all been there: you deploy a new version and suddenly you start seeing a drop on the access / usage metrics. Then a surge of errors floods your monitoring system, and waves of bad news follow suit. It's a feeling of dread and uncertainty I wish for nobody.

But once things go south, what should we do? How do we handle this kind of situation and how do we prevent this from ever happen again?

The magic word here is: preparation.

Just as we have routine fire drills and other emergency preparedness training in the office, we also need to prepare for adverse situations with our production system, and even more importantly, pay attention to our software lifecycle.

Beyond preparation, there is another essential factor for improvement: the culture of reflection through postmortem documents. The concept of a postmortem is well-known in the technology industry. A postmortem is a written record of an incident, its impact, the actions taken to mitigate or resolve it, the root cause(s), and the follow-up actions to prevent the incident from recurring.

- Check it out the [template I use for postmortems](https://github.com/matheus-santos/Architecture/blob/master/templates/0000-postmortem-template.md)

Today, I would like to talk about conducting postmortems, its best practices and tips on how to cultivate a postmortem culture.

## The Postmortem Philosophy

The purpose of a postmortem is to ensure the incident is properly documented, that we understand the root causes, and define a roadmap for a definitive solution — and if appropriate — a change in culture as well.

Writing a postmortem is not a punishment and should not be used to assign blame. Instead, we should view it as an opportunity to learn and improve the entire company. The document should be a collaborative process that encourages knowledge sharing across the board.

> The primary goal should be collaborate and share knowledge.
> Avoid blame and keep it constructive.

Once we established our mindset towards a blameless and constructive experience, we can move forward and start digging the problem. It is important to note that not all incidents should be accompanied by a postmortem. Postmortems take time to write and deliberate, so each team should ponder whether makes sense to go through the exercise. In my experience, it makes sense to write it down when:

- We had to intervene in the process by any means, like rolling back a version or rerouting traffic.
- User has been impacted beyond a certain threshold
- Resolution time is going to take longer than our tolerance rate
- There was data loss of any kind

## What to do when things go haywire

The first priority is restore the service to mitigate impact. If the issue went to production, the first approach would be to turn the feature off or reroute the traffic while we investigate the damage. If we are flexible enough, we might even roll back to previous version to give us time to plan our fix.

The main idea here is to find a quick, temporary solution that will give us time to investigate further and develop a definitive solution. We should also consider how to prevent this issue from happening again in the future.

With this in mind, we proceed to create a live document - the postmortem - to record our findings. The file should be available to anyone to come and start collaborating. After finishing the process, the document will be reviewed and published for everyone so we can share what we learned.

Being honest and transparent while we solve the incident is vital. The live document help us communicate clearly with the people being impacted and also invites the team to weight in and help us move fast with the solution.

Other methods to reach out to impacted people, especially users and partners, could be: emails, a service status page ([like Github's](https://www.githubstatus.com/)), and official accounts on social media platforms.

Another aspect in which the live document shines is assisting in coordinating with multiple parties. Having a single source of truth help us coordinate efforts and share knowledge in an organized manner, also keeping everyone on the loop.

When the incident is over and we patched the solution, we go back to the document and invite everybody to participate in the Reviewing process (or Retrospective Sessions) of the incident. This is opportunity that we have to learn and ensure it won't happen again. Whenever I am running Retrospective Meetings, I ask myself and the team three things:

1. What are we doing right and should continue?
2. What are we doing wrong and should stop?
3. What are we not doing and should start?

The postmortem document is the key to help us answer these questions and hopefully will have tons of insights that will help us grow as a team and organization.

I would like to emphasize the Reviewing process is the most important step here and should be partaken by everyone. No Postmortem should be left _Unreviewed_.

## What if my organization do not have a Postmortem Culture?

Learning from our past mistakes and having a history we can access anytime is an invaluable resource. But it comes at a cost, requiring preparation and significant discipline to maintain. One of the biggest challenges is convincing everyone that this process is worthwhile, despite the preparation costs.

The biggest lessons I had in fostering this culture were:

- Propose it as an experiment: ask for a trial period where you can create documents and use them later to demonstrate their value. This will also help you understand how to better integrate it into the current workflow.
- Make it a rewarding experience: the process should be blameless and encourage everyone to participate. Once it is complete, you can take advantage of it and share it publicly to celebrate.
- Encourage senior leadership to participate: changing culture is difficult and it only works if everyone is on board. Invite leadership to join the conversation and be part of the change.

## What's next?

Finally, don't forget to ask for Feedback! In my experience, each process ends up different depending on the team and organization. So, make sure to ask for help and invite everyone to be part of this. By doing this together you sure will be building something unique and lasting.

## Conclusion

Cultivating a postmortem culture can be very challenging, but is worth it. Thanks to that I can say with confidence how much it helped me find the clinks in the armor and be better at what I do.

Here's the template I use for you to get started:

- [Postmortem Template File](https://github.com/matheus-santos/Architecture/blob/master/templates/0000-postmortem-template.md)

In short, these are the best practices when conducting a postmortem:

1. Avoid Blame and Keep It Constructive
2. No Postmortem Left Unreviewed
3. Visibly Reward People for Doing the Right Thing
4. Ask for Feedback on Postmortem Effectiveness

I hope this is the beginning of a long journey of growth for you and your team.

See you next time!

## References

1. J. Allspaw, "Blameless PostMortems and a Just Culture", blog post, 2012.
2. P. G. Boysen, ["Just Culture: A Foundation for Balanced Accountability and Patient Safety"](https://pmc.ncbi.nlm.nih.gov/articles/PMC3776518/), in The Ochsner Journal, Fall 2013.

<!-- Inspired by: https://sre.google/sre-book/postmortem-culture/ -->