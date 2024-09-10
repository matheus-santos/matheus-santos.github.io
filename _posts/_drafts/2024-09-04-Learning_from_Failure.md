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

<!-- TODO: Translate text to English -->

The magic word here is: preparation. <> Da mesma forma que nós temos treinamentos rotineiros de incêndio e outras situações adversas no escritório, nós também temos que nos preparar para situações adversas com o sistema em produção, e mais ainda, com nosso ciclo de vida do software.

E além da preparação, existe um outro fator essencial para o aperfeiçoamento do processo e aprendizado: a cultura de reflexão por meio de relatórios *postmortems*. O conceito de postmortem é bem conhecido na indústria de tecnologia [All12]. Um postmortem é um registro escrito de um incidente, seu impacto, as ações tomadas para mitigá-lo ou resolvê-lo, a(s) causa(s) raiz e as ações de acompanhamento para evitar que o incidente se repita.

No post de hoje, vamos descrever os critérios para decidir quando conduzir postmortems, algumas práticas recomendadas em torno de postmortems e dicas sobre como cultivar uma cultura postmortem com base na experiência que adquirimos ao longo dos anos.

**O que fazer quando um incidente é detectado?**

<!-- TODO: Stopped here! -->

<!--
1. Recuperar imediatamente o serviço: reverter a versão, subir um servidor extra, apontar para outro servidor; o importante é encontrar uma solução rápida que dê tempo para o time investigar a causa do problema.
2. Iniciar investigação.
3. Reunir os dados e compartilhar com o time.
4. Coordenar com o time a distribuição dos esforços e começar a executá-los (action items)
5. Registrar postmortem
6. Apresentar próximos passos para o time e para os afetados pelo incidente (ser honesto e transparente)
-->


## References

-  [All12] J. Allspaw, "Blameless PostMortems and a Just Culture", blog post, 2012.

<!-- TODO: Add link to Postmortem template (https://github.com/matheus-santos/Architecture/blob/master/templates/0000-postmortem-template.md) in matheus-santos/Architecture-Open -->


