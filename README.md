# ![image](https://github.com/julien-muke/mygitactions/assets/110755734/6f563446-e59e-44c5-b977-b0e16ddc7edc) GitHub Actions CI/CD


![actions-logo](https://github.com/julien-muke/mygitactions/assets/110755734/aeb3b495-b4e2-4981-bd75-240593ce5f69)


## 🤖 Introduction

GitHub Actions is the built-in CI/CD tool for GitHub, CI/CD stands for Continuous Integration and Continuous Delivery, allows us to automate the testing of our code to make sure it meets certain criteria after all the tests are passed you can enable actions to automate the delivery of your code this can significantly reduce the time it takes for you to deliver updates to your application.

## 📝 Overview

In the lab portion of this tutorial we'll go over how to implement our own GitHub action and implement a Linter that will run checks against our code to make sure that it meets specific criteria.


## GitHub actions workflow file walkthrough

Let's go over the terminology you need to know to understand a GitHub actions workflow file so we have a workflow yaml file GitHub actions workflow file walkthrough which specifies `events` `jobs` `runners` `steps` and `actions`.

![Blank diagram-13-2](https://github.com/julien-muke/mygitactions/assets/110755734/c3a3543d-1288-445d-bfb6-8808ff2acd06)


* On the event that someone pushes new code it's going to run the job Super-lint
* That job is going to run on ubuntu container hosted on github.com
* And then it's going to go through two steps:tThe first step is to check out the code and the next step is to run the linter 
  
NOTE: Linter is it's just something that we use to check to make sure that our code is conforming to certain standards super linter is made up of multiple linters so it doesn't matter which code you use in your repository superlinter is going to understand it and make sure you conform to the standards of that language.


## Step 1️⃣ : Github actions Lab - Creating Repo and setting up Action