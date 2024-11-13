---
title: "Learning from Failure"
category: software
date: 2024-09-04 15:41:00 -0300
comments: true
description: Learning from Failure.
---

> “Your first 10,000 photographs are your worst.”
― Henri Cartier-Bresson

I always loved this quote. Although Henri Cartier-Bresson was referring to a differet craft - photography - it still deeply resonated in me right from the start. It is a powerful idea in which I live by and try to apply in every project that I'm involved with.

There's always room to improve. The trick is to look back in search for clues for where to go next.

And in the same way as with photographs, your 10,000 deploys will be your worst. As a software engineer, it is important to keep track of your software development life cycle process and to be prepared when an emergency arrives. We've all been there: you deploy a new version and suddenly you start to see a drop on the access / usage metrics. Then it comes a surge of errors in your monitoring system, and the waves of bad news start following suit. It is an awful feeling of uncertainty and that I really do not recommend.

But once the damage is done, what should we do? How do we handle this kind of situation and how do we prevent this from ever happen again?

The magic word here is: preparation.

Just as we have routine fire drills and other emergency preparedness training in the office, we also need to prepare for adverse situations with our production system, and even more importantly, pay attention to our software lifecycle.

Beyond preparation, there is another essential factor for process improvement and learning: the culture of reflection through post-mortem reports. The concept of a post-mortem is well-known in the technology industry. A post-mortem is a written record of an incident, its impact, the actions taken to mitigate or resolve it, the root cause(s), and the follow-up actions to prevent the incident from recurring.   

Today, I would like to describe the criteria for deciding when to conduct post-mortems, best practices around post-mortems, and tips on how to cultivate a post-mortem culture based on my experience as an engineer over the years.

## The Postmortem Philosophy

The purpose of a postmortem is to ensure the incident is properly documented and that we were able to understand the root causes and define a roadmap for a definitive solution - and if appropriate - a change in culture as well.

Writing a postmortem is not a punishment and should not be used to assign blame. Instead, we should view it as an opportunity to learn and improve the entire company. The document should be a collaborative process that encourages knowledge sharing across the board.

> The primary goal should be collaborate and share knowledge.
> Avoid blame and keep it constructive.

Once we established our mindset towards a blameless and constructive experience, we can move forward and start digging the problem. It is important to note that not all incidents should be accompanied by a postmortem. Postmortems take time to write and deliberate, so each team should ponder whether makes sense to go through the exercise. In my experience, it makes sense to write it down when:

- We had to intervene in the process by any means, like rolling back a version or rerouting traffic.
- User has been impacted beyond a certain threshold
- Resolution time is going to take longer than our tolerance rate
- There was data loss of any kind

<!-- STOPPED HERE -->
<!-- Collaborate and Share Knowledge -->

## What to do when haywire

<!--
1. Recuperar imediatamente o serviço: reverter a versão, subir um servidor extra, apontar para outro servidor; o importante é encontrar uma solução rápida que dê tempo para o time investigar a causa do problema.
2. Iniciar investigação.
3. Reunir os dados e compartilhar com o time.
4. Coordenar com o time a distribuição dos esforços e começar a executá-los (action items)
5. Registrar postmortem
6. Apresentar próximos passos para o time e para os afetados pelo incidente (ser honesto e transparente)
-->

Like every debugging process...

<!-- Best Practice: No Postmortem Left Unreviewed -->
<!-- Introducing a Postmortem Culture -->
<!-- Best Practice: Visibly Reward People for Doing the Right Thing -->
<!-- Best Practice: Ask for Feedback on Postmortem Effectiveness -->
<!-- Conclusion -->
<!-- Share postmortem template example: https://sre.google/sre-book/example-postmortem/ -->


An atmosphere of blame risks creating a culture in which incidents and issues are swept under the rug, leading to greater risk for the organization [Boy13].

You can’t "fix" people, but you can fix systems and processes to better support people making the right choices when designing and maintaining complex systems.

## Conclusion

1. Avoid Blame and Keep It Constructive
2. No Postmortem Left Unreviewed
3. Visibly Reward People for Doing the Right Thing
4. Ask for Feedback on Postmortem Effectiveness

## References

-  [All12] J. Allspaw, "Blameless PostMortems and a Just Culture", blog post, 2012.
-  [Boy13] P. G. Boysen, ["Just Culture: A Foundation for Balanced Accountability and Patient Safety"](https://pmc.ncbi.nlm.nih.gov/articles/PMC3776518/), in The Ochsner Journal, Fall 2013.

<!-- TODO: Add link to Postmortem template (https://github.com/matheus-santos/Architecture/blob/master/templates/0000-postmortem-template.md) in matheus-santos/Architecture-Open -->


