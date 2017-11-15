---
title: "Building a modular project using Domain-Driven Design mindset"
category: tech handson laravel
date: 2017-10-27 19:00:00 -0300
---

Hey folks, Matt here.

Recently I was presented to a new approache called Domain-Driven Design and that is really changing my view and actions when tackling a problem. Since it is a new idea, at least for me because it is been around since 2003 with the book "Domain-Driven Design: Tackling Complexity in the Heart of Software" [\[1\]](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_sc_1?ie=UTF8&qid=1509140585&sr=8-1-spell&keywords=Domain-Driven+Design%3A+Tackling+Complexit), I applied the concepts to a new project and now I would like to propose another way to structure your project in order to make it more modular e coupled.

Before we start, I am assuming that you have some knowledge about these subjects:

- PHP programming language
- Any framework
- Sublime Text editor (any editor)

Just as disclaimer, for this tutorial I choose Laravel because it is a new framework in which I started to work with and realized it is pretty fun! There's a good documentation, lots of tutorials and plugins. As a Django fan, I must admit that is a very nice tool to get things done. How did I choose it? Check [this article](/posts/The_Programming_Language_Framework_Dilemma) to find out.

Let's begin, shall we?

## The spaguetti monster app

> "It is just a prototype, put the code anywhere and then next week we get back to it and fix it".

How many times did we foul ourselves into thinking we would have time to restructure our project? Well, too many. When we start a new project we must do it in a [Lean](/posts/Lean_hit_the_market_first_and_learn_from_it) way but it is important to put some thoughts about how we are going to organize before coding.

A MVC framework is good is fine getting started and small projects. But since the methodology divides the files by category (controller, model and view separate by folder) you may have trouble in the future trying to handle dozens of controllers that connectst to dozens of models at the same time.

Dividing your files by category is nice, but becomes hard to avoid conflicts and can make things difficult when working colaboratively.

Ok, so now we identified our first problem: divide by context.

The second problem is the code. It is important to know what is business logic and what is infrastructure logic. Business logic is every code related to your idea like your Products Catalog or your Users List. Infrastructure logic is the code related to the structure running behind your project like Controllers, Providers and Middlewares.

In order to keep as modular as possible, we shoud be aware to never mix what belongs to business to what belongs to infrastructure. This mindset will help us later when separating our project into several services (aka micro service pattern). 

Want a example? Here it goes. Imagine we are working on `ProductsController` and we need to put and authorization step to ensure the user can edit a item. A natural way to do this is putting the auth code directly into the controller:

```
// PATCH api/items/{id}
public function editItem() {
    $user = Auth::getUser();
    if($user->hasRoles('admin')) {
        // Edit item
    }
}
```

But now we want to add the same step for the delete and create methods:

```
// PATCH api/items/{id}
public function editItem() {
    $user = Auth::getUser();
    if($user->hasRoles('admin')) {
        // Edit item
    }
}

// DELETE api/items/{id}
public function deleteItem() {
    $user = Auth::getUser();
    if($user->hasRoles('admin')) {
        // Edit item
    }
}

// ...

```

Noticed the repeated code? If had to change something we would have to replace in every method of every controller so in order to keep it short and clean, we could put the authorization step into an `UserService` and work from there instead of messing with our controllers endpoints.

Now, how to solve these two problems stated above? That's when the DDD enters. Changing our mindset from function based to context based will allow us to put bounds among concerns, making the project clean and little easier to handle. 

The best part is since Doman-Driven Design is a way to structure your code, it is agnostic and can be (and should be) used in every language. If you don't like PHP or your job requires a specific set of tools you still can apply these thoughts! Awesome isn't?

In this article I will give you a brief context of Domain-Driven Design and talk about two patterns that helped me a lot to build better code: repo pattern and service-centered approach.

## Brief explanation about Domain-Driven Design concept

Domain-Driven Design is all about design and creating highly expressive models. DDD also aims to create models that are understandable by everyone involved in the software development, not just software developers.

The trick here is to design your code in a way that a non-developer could understand. In DDD, it is less about the nouns and verbs and more about the concepts. When you talk the same language as the domain experts the work becomes more creative and straightforward for both sides. 

Usually we would create the models and the endpoints would be operations (post, patch, delete, get) to access these models. Pretty straightforward. In DDD we add a layer between the controller and the models, centralizing our logic in it. These classes we will call services. A service provides methods that abstract what we have on our data structure and transform in something more palatable for the expert domains which know nothing about coding.

The general ideia is depicted by the following diagram:

![Service funnel.](/images/posts/Building_a_modular_project_using_Domain-Driven_Design/diagram1.png)

And this is just the tip of the iceberg.

The whole concept of DDD is complex and I will talk about it later, but for a start this would suffice. If you still curious about it I recommend these books:

- Domain-Driven Design: Tackling Complexity in the Heart of Software by Eric Evans
- Implementing Domain-Driven Design by Vaughn Vernon

You can also check my thoughs about it in the post "[Learning concepts of Domain-Driven Design](/posts/Learning_concepts_of_Domain_Driven_Design)".

## Enter the Repo pattern

Usually the framework you choose will come with a ORM. This ORM maps your database to objects that you can manipulate into your code, making our work much easier. It's very tempting to do things like this:

```
// In UsersController

public function get()
{
    $users = User::all();
}
```

The example above seems inoffensive, but can you imagine your project with 10+ controllers with lots of endpoints and every one of theses functions handling the model its own way? It will be a real nightmare when you have to refactor this code.

To keep things sane, we can create a new layer where we will use to access the models. Then if you need to manipulate data you just have to create an instance of this class that is called repository and use the exposed methods. Since every repository has similar actions like `find()`, `update()`, `create()` and `delete()` you will end up with a very nice abstraction and a standardized code.

Ok, so this is what I am saying:

![Repository pattern](/images/posts/Building_a_modular_project_using_Domain-Driven_Design/diagram2.png)

Here's what I did. I created a parent class called `BaseRepository` that shares lots of common functions plus map the responses into nice objects that I can use later as my API responses (I tried Fractal [[4]](https://fractal.thephpleague.com/) by the way and is awesome! Thanks guys). Let's take a look in the code:

```
class BaseRepository
{
    /**
     * @param $model
     */
    public function setModel($model)
    {
        $this->model = $model;
    }

    // [...]

    /**
     * @param array $columns
     * @return \League\Fractal\Resource\Collection
     */
    public function all($columns = ['*'])
    {
        return $this->asCollection(
            $this->model::all()
        );
    }
}
```

And the basic functionalities will be guaranteed for all repos:

```
class ProductRepository extends BaseRepository {

    function __construct(Application $app)
    {
        parent::__construct($app);
        $this->setModel(Product::class);
    }

    // [...]

    // ALL places will use these functions, so if someday we need to change
    // something, it will be easy to do because it is all centered :)

    public function getProductByWeirdField($field) {}
    public function removeAllProductsOlderThan($time) {}
    public function someSpecificRelatedThing($id) {}

```

As I said earlier, this layer make communication between controllers (infrastructure) and models (our business logic) clearly separated and this way we have more control on what is going on in the project. If we have chosen otherwise we would tempted to use the ORM directly in the controller's functions making things difficult maintain in the long run. 

## The new tree structure

You may end up with the following tree structure:

<img src="/images/posts/Building_a_modular_project_using_Domain-Driven_Design/diagram3.png" alt="Drawing" style="width: 250px;"/>

In the image above you can see that we moved our business logic from the default `app` folder to a `business` folder. We did this to keep the business logic separated from the infrastructure. Into the `business` folder you create a folder for each domain you have in your project. Finally into each domain folder we separate the files by type (`Models`, `Repositories`, etc..). This will give us a visual sight of what our microservices are and will make things easier when the time comes.

If you opt to create a new folder (like `business` folder in the example) you will have to change your `composer.json` file in order to autoload your classes properly:

```
// composer.json
{
    "name": "laravel/laravel",
    "description": "The Laravel Framework.",
    "keywords": ["framework", "laravel"],
    "license": "MIT",
    "type": "project",
    "require": {
        // ...
    },
    "require-dev": {
        // ...
    },
    "autoload": {
        "classmap": [
            "database/seeds",
            "database/factories"
        ],
        "psr-4": {
            "App\\": "app/",
            "Business\\": "business/"  // HERE Add to path to folder
        }
    },
    "autoload-dev": {
        "psr-4": {
            "Tests\\": "tests/",
            "Business\\": "business/"  // HERE Add to path to folder
        }
    },
    "extra": {
        "laravel": {
            "dont-discover": [
            ]
        }
    }
    // ...
}
```

And that is it! Now we have a "modular MVC" to work with. This lead us to the next topic that are the services. As I mentioned before, a service is a class that concentrate all business logic and orchestrate the communication between the controllers and the data model.

## Enter the service-centered approach

We covered how repository pattern works and why we should keep business logic separate from infrastructure. Now, what do we do when the models need to communicate with each other? We can't call `ProductRepo` from `UserRepo` or mix things in the controller. That's where the service classes enter.

Keeping the mindset of modularity, we will have a `Services` folder where we are going to do all the crazy things, which means it is where business logic will be placed.

As the example above, if we ever need to fetch information from other domains or modules, we should use the service class `ProductService` to do it:

```
class ProductService {
    public function createAndBroadcast($attributes) {

        $user = $this->auth->getUser();

        // Checking authorization before letting user create the prod
        if(!$user->hasRole('PRODUCT_MANAGER')) {
            throw new UserException('User not authorized.);
        }

        // Create a product
        $newProduct = $this->productRepository->create($attributes);
        
        // Send email to all users
        $this->emailService->newProductCreated(
            $product, 
            $this->userRepository->all()
        );
    }
}
```

Here's why services really shine: there will be other services like e-mails, logs, authentication and authorization that aren't really concern of a repository, since the repository should only deal with data stuff. Hence, here is the place to wrap up everything. In other words, our business logic.

## Conclusion

I hope this article helps you understand briefly how to keep your project tight and modular and give you a new way of thinking about your business. I am still learning and studying these concepts so if you help any doubt or advice I would love to hear!

## References

- [1] Evans, Eric. "[Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_sc_1?ie=UTF8&qid=1509140585&sr=8-1-spell&keywords=Domain-Driven+Design%3A+Tackling+Complexit)";
- [2] Fidao, Chris. "[Hexagonal Architecture](http://fideloper.com/hexagonal-architecture)";
- [3] Laravel. "[The PHP Framework For Web Artisans](https://laravel.com/)";
- [4] PHP League. "[Fractal output complex, flexible, ajax/restul data structures](https://fractal.thephpleague.com/)".
