---
layout: post
title: Open Data Portal - Part 1
date: 2022-02-22 19:20
tags: open-data
---

Looking into options for standing up an open data portal, hosting datasets, etc.  Things I'm looking at:

* CKAN - It's in python. I haven't really looked into what development looks like.
* JKAN - The simplicity is very appealing but it hasn't been actively developed in a while.  Even a Bootstrap 4 update is stuck and not merged into the main codebase.
* Qri.io - They responded to my questions on Discord. It seems like it's more for individual datasets, like a single table of data.  Cool concept though and has a GitHub-esque online component.
* Datasette - This looks like something I could start with.

I'm realizing I've got a lot of anxiety around running these python projects as production websites. It's uncharted territory for me because I usually only play with them locally. Datasette has a Docker image available, which I'm pretty sure is a good thing. I'm still working on wrapping my head around how to use Docker and the best way to do that is to jump right in. Pandemic has really raised my anxiety in all this because I don't have a community of peers I can easily tap into as a resource.  I'm working on leaning on my friends but it doesn't come naturally. Anyways...

The [Datasette Installation Guide](https://docs.datasette.io/en/latest/installation.html) provides instructions for running via Docker.

## Get the Image

Since I've got Docker already installed on my Windows machine, I'm able to open PowerShell and just run the `> docker pull ...` command for the image to show up in the Docker Desktop application.

## Run a Container

The installation guide gives a command with options to spin up a container. The question now is how do I get Docker Desktop to run those options.  I don't see any place to enter the commands.  Looking at the Docker documentation, it looks like I can probably just run the `> docker run ...` command in PowerShell but I need to change the directory syntax for Windows.  I still couldn't get it to work in a way where the page would show up in the browser so I just ran the command using WSL and it worked *like that*.

## Development

I don't think I'm supposed to do my development on the Docker container itself...?  It looks like the container ran the application and as the host I'm able to pass it whatever data source I want.  However if I want to change the code for the application itself (to change the CSS for example) I'll need to probably clone the repo and then re-dockerize it.  Do I need to dockerize it if I'm only deploying it for myself?  Can I deploy the code to Heroku or something?  Maybe it makes sense to dockerize if I'm deploying to AWS. I'll need to figure out how to create the database file.
