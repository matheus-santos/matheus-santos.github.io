---
layout: default
title:  "Thoughts on building a solid REST API"
date: 2018-08-30 08:47:00 -0300
categories: code tutorial architecture
comments: true
---

Hey folks, Matt here.

Application programming interface is a set of methods or subroutines, communication protocols and tools for building software. Specifically we have what is called RESTful API a method of allowing communicationg between a web-based client and server.

As a developer we have to deal with all sort of APIs every day. It is part of our job to design a solid way to communicate our servers with an mobile app, website or even other machines.

Today I would like to share with you some tips on how to build a solid RESTful API. As important as that, we also have to keep in mind two other key factors that will ensure a sweet experience when exploring your API: readability and modularity.

For the sake of simplicity, we will talk about a very common function that almost every API has: user and product flow (registration, exploration, deletion).

# 1. Start by design

This is the most important step when designing and implementing an API. It consists of preparing documents that describes how entities should be exposed and the relationship with each other. As for me I strongly believe that an API should reflect its database design. What I mean by that is that the end your API is a way to clients iterate with your database, so why not cut complexity and make it look like your model-entity-relationship? Works like a charm.

So, start by defining your main domains and its endpoints. Using the user/product example, we can clearly see a distinction among domains: product domain, say "commerce"; and user domain, say "accounts":

```
/api-v1/commerce
/api-v1/accounts
```

This works best when your software is designed using the Domain-driven-development (DDD) principle. If you never heard before, check [this article](Building_a_modular_project) where I talk a little about this principle and baby steps on how to get started.

Ok, we still have to define our endpoints and our methods. The most common methods for a simple endpoint are GET, POST, PATCH and DELETE. Use use PATCH instead of PUT here because PUT is primarily to update existing resource and may work as an `upsert` method while PUTCH gives us the ability to make partial update on a resource [[1]](#). 

So you will end up with:
```
GET /api-v1/commerce/users
GET /api-v1/commerce/users/:id
POST /api-v1/commerce/users
PATCH /api-v1/commerce/users/:id
DELETE /api-v1/commerce/users/:id

GET /api-v1/accounts/products
GET /api-v1/accounts/products/:id
POST /api-v1/accounts/products
PATCH /api-v1/accounts/products/:id
DELETE /api-v1/accounts/products/:id
```

This list works as a checklist and make it easier to define objective tasks to delegate to team members.

The point is that building your model first helps us to see more clearly the relationships and responsibilities of each domain and entity.

# 2. Choose your tools

Now that we have an abstract plan, it is time to choose our weapons. That is a very difficult choice for some because we have a very wide range of options but as a rule of thumb try to keep it simple and choose what you are used to.

## Language / Framework

This is fun. Choosing a language to work with is always a though choice and it is even harder when you have to choose a framework too. But if our design is okay and the domains are well settled and documented we can always scale to something more robust or that meets specific needs. Of course the final choice will decided with the team, so always have this in mind:

1. Choose a framework that most of the devs are familiar
2. If you choose a novel framework, keep at the least the language familiar
3. If you need something fast, choose a lightweight framework. If you wish to scale and do not have time to rewrites, choose a more robust one. It is all about balance time/effort.

Avoid changing all at once because this will increase time to launch your alpha version.

## REST client

Since we are building an API it is nice to have at hand some tool to make requests and render responses. As for me I would recommend one of these tools:

- [Postman](https://www.getpostman.com/): this one allows you to scale and provides some sweet features like mock servers and auto documentation generator.
- [Insomnia](https://insomnia.rest/): very handy tool for a "hit the ground running" approach. It has direct approach and a sweet layout that makes everything clear and simple.

Really, both of them are good and you cant go wrong.

# 3. Choose your API specification

Now that we have chosen our tech it is time to set up some conventions and best practices. A software that is consistent and well formatted is easier to read and explore therefore is much more likable to work with.

An specification is a document that provides how the endpoint should expose its entities and also comes with a list of response protocols and headers that helps with cache, formatting and decision-making by client side.

Two commons specifications that I grew to love work with are [HAL](http://stateless.co/hal_specification.html) and [JSON:API](http://jsonapi.org/). 

As a front-end developer I used to struggle a lot working with different formats and trying to figure out how to navigate and link these entities. 

So choose a specification and stick to it. This will pay very well in the future with a concise API.

# 4. Tests and mocks

With our specification set we know exactly the data structure that is being sent and received. It becomes very useful if the project has both client side and server side being developed at same time. Sometimes the front-end developer gets stuck because there's no endpoint to access but then you can provide the general idea and give him to use while the back-end is being finished.

There are different ways to mock your server both from client and server side but since we know what to expect it is easier to propagate and apply.

# 5. Wrap all up with a sweet process and user documentation

Hopefully if you reach this point you already have a tight API to explore and communicate. But it is important to tell the story and write a guide to your users and devs about your application. It is importante to note that we have two different actors on the scene:

- The **user** who will deal with your application either by integration or exploration
- The **developer** who will improve and give maintenance to your application

Keep in mind that they have different necessities so basically you will end up writing to documents: "why we did this way" and "how you will use it".

Why have formal documents? First, writing the decisions down is essential. Only when one writes do the gaps appear and the inconsistencies protrude. The act of writing turns out to require hundreds of mini-decisions, and it is the existence of these that distinguishes clear, exact policies from fuzzy ones.

Second, to "spread the word". The manager's fundamental job is to keep everybody going in the same direction, his chief daily task is communication  and these documents will immensely lighten the load.

Finally, documents give him a data base and checklist. By reviewing them periodically the team can sees where they are and where they and how to navigate.

# Conclusion

This are a checklist that works very well when designing your RESTful API and it is generic enough to apply to other projects like [GraphQL](https://graphql.org/) and [gRPC](https://grpc.io/). 

Try to keep your design clear and concise and prepare for scale by using the [DDD](Building_a_modular_project) principle. 

If you are building an prototype to prove your concept go for a easier language and use a framework to boost up your productivity. 

Use a REST client to document your endpoints and easily share with your colleagues.

Any thoughts on this? You can reach my by e-mail or in the comment box below.

# References and further readings

- [1] REST API Tutorial; "HTTP Methods"; [https://restfulapi.net/http-methods/](https://restfulapi.net/http-methods/)
- JSON:API; [http://jsonapi.org/](http://jsonapi.org/)
- HAL - Hypertext Application Language; [http://stateless.co/hal_specification.html](http://stateless.co/hal_specification.html)
- O'Reilly; "RESTful Web APIs" by Leonard Richardson, Sam Ruby, Mike Amundsen; [http://shop.oreilly.com/product/0636920028468.do](http://shop.oreilly.com/product/0636920028468.do)
- Wrox; "Patterns, Principles, and Practices of Domain-Driven Design"
by Scott Millett, Nick Tune; [http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html](http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html)