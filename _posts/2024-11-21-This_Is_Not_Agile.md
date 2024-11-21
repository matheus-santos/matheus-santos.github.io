---
title: "This is not Agile"
category: Software
date: 2024-11-21 00:00:00 -0300
comments: true
description: On how to detect software projects that are really using agile development versus those that are simply waterfall or spiral development in agile clothing.
tags:
    - Culture
---

<img src="/images/posts/894A9FFA-FB16-49C3-8D2C-8E9ED14B0957.jpg" width="100%" alt="People getting ready to run"/>

_<center>🔈You can listen to this article by clicking on the play button below. I hope you enjoy!</center>_

<!--
<iframe
   frameborder="0"
   width="100%"
   height="75"
   src="https://drive.google.com/file/d/1gkwg4z7Z2xBCMIqWVQP2_PIJg15Yp8cI/preview">
</iframe>
-->

<iframe width="100%" height="125" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/1964121967&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/matheus-cesario-2" title="Matheus Cesario" target="_blank" style="color: #cccccc; text-decoration: none;">Matheus Cesario</a> · <a href="https://soundcloud.com/matheus-cesario-2/detecting_agile_bs" title="Detecting_Agile_BS" target="_blank" style="color: #cccccc; text-decoration: none;">Detecting_Agile_BS</a></div>

Agile is a buzzword of software development, and so nowadays all software development projects are, almost by default, declared to be "agile".

But let's be honest: sometimes, things are not always what you see from the outside. It is common to see teams misinterpreting Agile principles and experienced engineers getting confused with the workflow when attempting to introduce it into a project.

Today I would like to share my thoughts on how to detect software projects that are truly using agile development versus those that are simply waterfall or spiral development disguised as agile (“agile-scrum-fall”).

Agile software development is the term used to refer to a set of methods and approaches that reflect values and principles involving the discovery of requirements and the refinement of solutions in a dynamic and incremental manner. Its main characteristic is to encourage collaboration and communication among all stakeholders in the product, always aiming for the customer experience - the end user - as the guiding principle for product development.

The first mention of incremental and interactive development practices date back to 1957, with structured methodologies such as "evolutionary models" and "adaptive models" becoming more popular in the 1970s along with the increase in complexity of software projects.

The term "Agile" became truly popular in the early 2000s, with the publication of the [Agile Manifesto](https://agilemanifesto.org/), a document written by renowned practitioners in the field of engineering. The Agile Manifesto stands out for its simplicity, which was also the key piece as it represented a response against bureaucratic and rigid models, such as *Waterfall*.

The principles are amazingly simple [[1]](https://agilemanifesto.org/):

- **Individuals and interactions** over processes and tools
- **Working software** over comprehensive documentation
- **Customer collaboration** over contract negotiation
- **Responding to change** over following a plan

It's mind-blowing how such a straightforward framework has transformed the way we handle projects and collaborate within organizations.

Still, today we see organizations that say that are "Agile", when in fact they use little or no agile principles. There are a lot of variables here, but the most important aspect to make an organization truly agile is the **commitment to change**. The process will only work if everyone is on board, otherwise it will go back to old habits or end up with methods that bring the illusion of control, but little to no results.

## Key flags that a project is not really agile

In my view, being Agile means bringing everyone on board and empowering each individual with enough knowledge and opportunity to share their opinion. It is about actively listening to someone and having the courage to change course when necessary. It is about collaborating with each other and responding to change instead of stubbornly fixating on a plan.

In my experience, a project is **not** Agile when:

1. The team is building software in a vacuum, without considering the needs of the people who will use it.
2. The development team is not receiving regular feedback from users, including bug reports and assessments of the software's performance. Talking once at the beginning of a program to verify requirements doesn’t count!
3. Meeting requirements is prioritized over rapid delivery of a functional product.
4. Stakeholders like developers, testers, contractors, end-users, managers are acting more-or-less autonomously, which often brings responses like "it’s not my job" when something breaks.
5. End-users of the software are missing-in-action throughout development. They should be present during Release Planning and User Acceptance Testing.
6. There are no DevSecOps culture whatsoever or it manual intervention is often required for processes that can and should be automated, such as automated testing, continuous integration, continuous delivery.

## Ok, my team is not really Agile. How do I improve it?

First step is convincing everyone the opportunity for improvement and the importance of applying these principles. Old habits are hard to change and honestly, changes are always a little scary.

Use this as an opportunity to bring the team together and give room for everyone to voice their concerns. Collaborating and communicating early and constantly will help you shape the vision and empower everyone to take ownership and contribute to the initiative as well.

So, think about bringing change incrementally. Trying to change everything at once is not a good idea because it may get people overwhelmed, resulting in a defensive position agains change.

In my experience, the best way to do it is incrementally, or baby steps. Think about what parts of the workflow should be prioritised and propose small experiments to be measured overtime. As your work progresses, collect data on performance and use it later to compare with previous results.

Implementing it in waves will give you the time you need to catch your breath and let the changes settled in before moving on to the next challenge. Collaborating constantly will help you spread awareness and become more adaptable to unforeseen challenges.

As you move forward, these small waves of change will give you the credibility and confidence to tackle bigger and bigger challenges. It's ok to feel overwhelmed, just remember to always rely on your team to help you overcome the fear of it.

## Checklist to identify if your team is agile

Whenever I join a new team and start to feel there are opportunities for improvement but can't really point out where where, I ask myself these questions:

1. Are teams delivering working software to at least some subset of real users every iteration and gathering feedback?
2. Is there a product charter that lays out the mission and strategic goals?
3. Do all members of the team understand both and are they able to see how their work contributes to
both?
3. Is feedback from users turned into concrete work items for sprint teams on timelines
shorter than one month?
4. Are teams empowered to change the requirements based on user feedback?
5. Are teams empowered to change their process based on what they learn?
6. Is the full ecosystem of your project agile (git, travisCI, test coverage, etc)? *Agile programming teams followed by linear,
bureaucratic deployment is a failure.*

For a team working on agile, the answer to all of these questions should be "yes". If you got any "no" here, this is where you should start.

## Conclusion

It is strange how "Agile" can be something so simple and yet so complex to describe. Collaborating in rapid cycles of incremental changes while actively listening to feedback is the most powerful tool I know to navigate uncertainties and grow to the right direction.

Do not let yourself go and get stuck behind rigid processes that hinder growth and bring morale down. Focus on people. People will never go out of business.

Hope you enjoyed the conversation of today.

See you next time!