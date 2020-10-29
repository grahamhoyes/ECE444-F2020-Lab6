# ECE444-F2020-Lab6
ECE444 Fall 2020 Lab 6: Test-Driven Development

## Pros and Cons of TDD
Well-tested code is a hallmark of a healthy software development project. It greatly decreases the number of bugs that slip through (though doesn't fully eliminate them), eases the burden on those QAing the code, and increases confidence in what is being delivered. 

From personal anecdotes, I have had to deploy untested code in the past due to severe time constraints, and it's a nerve-wracking experience hoping nothing goes wrong. With tested code, on the other hand, I feel much better about putting code out in the wild. This has been one of the driving factors behind the development of IEEE UofT's [Hackathon Template](https://github.com/ieeeuoft/hackathon-template), of which I am a lead developer. The project is a large scale Django application that is currently handling hundreds of users in production, and follows strong testing practices.

Test-driven development is a special category of writing tested code: Write the tests before the functionality, which should of course fail, then write the functionality so that the tests pass. Rinse and repeat for each unit of functionality. This works extremely well if software specifications are well-defined in advance, ensuring that the developer is sticking to those specifications in addition to the benefits of testing in general.

Where TDD specifically falls short, I find, is in an agile environment where software isn't fully defined in advance. Take, for example, the development of a new API endpoint that currently has no consumers. We know that it should serve, say, the `Post` model. On it's own, a list of posts isn't difficult and it would be easy to define a JSON structure ahead of time and write a test before writing the code.

But what if you're doing something fancier, and that you don't have full control over? I often find this to be the case when working with [Django REST Framework](https://www.django-rest-framework.org/), which like the rest of Django, is opinionated in how it does things. In these cases, it's much easier for me to implement the endpoint with DRF, see what the output looks like (for example, how are many-to-many fields represented), then set that format in stone with a unit test after the fact.

On that same note, TDD requires a much deeper understanding of the framework and language. When writing after-the-fact unit tests, I often find myself testing out the application in a console to test how exactly to write my test - something that is not possible with TDD. After-the-fact unit tests give you greater flexibility to write code, which is often preferred in an agile environment.