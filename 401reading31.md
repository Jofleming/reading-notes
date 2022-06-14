# Django REST Framework and Docker

## Beginner's Guide to Docker

[Reading](https://wsvincent.com/beginners-guide-to-docker/)

With Docker it doesn't matter if you are using Mac, Windows, or Linux. The entire development enviornment is isolated: programming language, software packages, databases, and more.

No longer need to use virtual enviornments with Docker. Docker can faithfully reproduce a production environment locally. And Docker can be shared among team members so everyone is working on the same setup.

Docker is really just Linux containers which are a type of virtualization.

Virtualization has its roots at the beginning of computer science when large, expensive mainframe computers were the norm. How could multiple programmers use the same single machine? The answer was virtualization and specifically virtual machines which are complete copies of a computer system from the operating system on up.

Images and containers are the two fundamental concepts to grasp when you start with Docker. An image is a snapshot in time of what a project contains. A container is a running instance of the image.

To use images you will need to create custom images and we do so using a `Dockerfile`. We also will use `docker-compose.yml` files to run the containers.

Dockerfiles are read from top-to-bottom. The first instruction must be the `FROM` command which lets us import a base image to use for our image. This base image could be another Docker image or one we create entirely from scratch.


## Django for APIs - Library Website

[Reading](https://djangoforapis.com/library-website-and-api/)

Django REST Framework works alongside the Django web framework to create web APIs. We cannot build a web API with only Django Rest Framework. It always must be added to a project after Django itself has been installed and configured.

The most important takeaway is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

The rest was a walkthrough of pretty much what we have been doing the past couple of days.

[Back](README.md)