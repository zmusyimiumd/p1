# P1: Personal Website

## Due: January 20th, by 11:59 PM

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
  - download and install Docker Desktop for your OS
- docker related lectures/notes that can be found on panopto and elms
  - as well as the [`docker-tutorial`](https://github.com/cmsc389t-winter2024/docker-tutorial) i've created for you all

## Introduction

### Github Pages

Github Pages is a service that allows you to host a static website on Github. You can create a website by creating a new repository and naming it `<username>.github.io`. You can then add an `index.html` file to this repository and it will be served at `<username>.github.io`. You can also create a website for a specific repository by creating a `gh-pages` branch and adding an `index.html` file to this branch. This website will be served at `<username>.github.io/<repository_name>`. For more information, see [Github Pages](https://pages.github.com/).

### Docker

Docker is a tool that allows you to run applications in containers. Containers are similar to virtual machines, but they are more lightweight and portable. Docker containers are created from images. Images are read-only templates that contain a set of instructions for creating a container. For more information, see [Docker](https://www.docker.com/).

## Overview

In this project, you will be creating a personal website that you will be served on Github Pages. You will also be dockerizing your web app and running it in the background **locally**.

1. Hosting Website On Github Pages
2. Dockerizing Your WebApp

**Note:** in previous semesters, we deployed the websites to TerpConnect using docker but because TerpConnect requires duo authentication, we are no longer able deploy via docker. However, you *could* still manually deploy your website to TerpConnect if you wanted to.

## Part 1

In this part you will be forking our template repository and editing the provided HTML locally on your own computer. You must complete the basic **required** edits in the index.html file (these are specified within this file as well):

- Name
- Profile Picture
- Introduction/Biography (About Me Page)
- Project 1 Details (can be a school project, club project/activity, internship project or internship experience)
- Project 2 Details (can be a school project, club project/activity, internship project or internship experience)
- Project 3 Details (can be a school project, club project/activity, internship project or internship experience)
- GitHub Profile
- LinkedIn Profile (if you have one)

To get full credit, also make at least one change to the website to personalize it. For example, you could

- Change the style/colors
- Add another social media link
- Add another section

Feel free to add your own touch to the HTML and/or CSS files. Once you've committed your changes, push your repository to remote. Describe what custom change you made on your website repository's README underneath your GitHub Pages Site link.

## Part 2

In this part you will be using Docker to dockerize your web app and run it in the background locally. To do this, you should edit the provided dockerfile and docker-compose.yml templates. The procedure detailed in the Docker Lecture should help you create a simple docker image for your website.

**Important Notes**

- The backend is written in Node.js You should use the "node-10:alpine" image in your dockerfile. This image also comes preconfigured with a "node" user which you can use rather than creating a custom user
- The package.json file includes a list of all dependencies. You will need to copy this and run ```npm install``` when building your image.
- Before you run any commands in your dockerfile (CMD), make sure to ```EXPOSE 8080```. This will expose the port and allow incoming and outgoing traffic flows from your docker container.
- To run a node app, the bash syntax is ```node app.js```
- To test your docker configuration, you can run

```
docker build -t node-web-app .
docker run --name "website" -p 80:8080 -d node-web-app 
Go to localhost:80/
```

- To test your docker-compose configuration, you can run

```
docker-compose up -d --force-recreate
Go to localhost:80/
```

- To remove all containers, you can run

```
docker system prune -af
```

- To remove all volumes, you can run

```
docker volume prune
```

### Submitting

You will be adding links for your Github Pages Site

Please format your `submission.txt` file as follows for Gradescope:

```
GitHub_Username
Repository_Name
```

e.x. if `sagars729` creates a fork titled `CMSC389T-Web-Template` then the `submission.txt` file would be

```
sagars729
CMSC389T-Web-Template
```

**Note:** There *might* be a problem when trying to view your profile pic when running locally, but if the image is showing up on your Github Pages Site, then that is okay and there are no points deducted for this.
