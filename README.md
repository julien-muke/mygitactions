# ![image](https://github.com/julien-muke/mygitactions/assets/110755734/6f563446-e59e-44c5-b977-b0e16ddc7edc) GitHub Actions CI/CD


![actions-logo](https://github.com/julien-muke/mygitactions/assets/110755734/aeb3b495-b4e2-4981-bd75-240593ce5f69)


## 🤖 Introduction

GitHub Actions is the built-in CI/CD tool for GitHub, CI/CD stands for Continuous Integration and Continuous Delivery, allows us to automate the testing of our code to make sure it meets certain criteria after all the tests are passed you can enable actions to automate the delivery of your code this can significantly reduce the time it takes for you to deliver updates to your application.

## 📝 Overview

In the lab portion of this tutorial we'll go over how to implement our own GitHub action and implement a Linter that will run checks against our code to make sure that it meets specific criteria.


## GitHub actions workflow file walkthrough

Let's go over the terminology you need to know to understand a GitHub actions workflow file so we have a workflow yaml file GitHub actions workflow file walkthrough which specifies `events` `jobs` `runners` `steps` and `actions`.

![Blank diagram-13-2](https://github.com/julien-muke/mygitactions/assets/110755734/c3a3543d-1288-445d-bfb6-8808ff2acd06)


On the event that someone pushes new code it's going to run the job Super-lint,
That job is going to run on ubuntu container hosted on GitHub,
Then it's going to go through two steps: the first step is to check out the code and the next step is to run the Linter.
  
NOTE: Linter is it's just something that we use to check to make sure that our code is conforming to certain standards super linter is made up of multiple linters so it doesn't matter which code you use in your repository superlinter is going to understand it and make sure you conform to the standards of that language.


## Step 1️⃣ : GitHub actions Lab - Creating Repository and setting up Action

1. Create a new repository

Navigate to your GitHub account (if you don't have one, go to github.com and create an account), go to "Repository" and click "New"

![Screenshot 2024-01-31 at 13 14 02](https://github.com/julien-muke/mygitactions/assets/110755734/38952beb-aae7-4a4f-aac2-766ed417fb3c)


2. We can call this whatever we want, i'll name it `mygetactions` and then scroll down and let's add a README.md file just to have a file to work with and then "Create repository"


![Screenshot 2024-01-31 at 13 16 31](https://github.com/julien-muke/mygitactions/assets/110755734/d2eebbf3-1f75-49f6-a011-5f9554554519)



3. The next thing we want to do is create a workflow, to do that just go "Add file" and click "Create new file"


![Screenshot 2024-01-31 at 13 17 25](https://github.com/julien-muke/mygitactions/assets/110755734/15498530-ee16-4c4e-833b-1950864db961)


4. We need to be very specific with our naming, the proper directory structure for your workflow files needs to be first `.github/workflows` and then you can name your file whatever you want, i'll name it `superlinter.yml`

![Screenshot 2024-01-31 at 13 20 50](https://github.com/julien-muke/mygitactions/assets/110755734/22226004-c25a-4514-88dc-cf080ef2a60c)




4. Then i'm going to copy and paste the code, you can see this is the code that we went over earlier, basically it's listening for a `push` event and when the push event happens it's going to first check out our code and then run the superlinter against it to make sure that it conforms to the linting standards

```yml
name: Super-Linter

on: push

jobs:
  super-lint:
    name: Lint code base
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Run Super-Linter
        uses: github/super-linter@v4
        env:
          DEFAULT_BRANCH: main
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```


![Screenshot 2024-01-31 at 13 21 59](https://github.com/julien-muke/mygitactions/assets/110755734/ef603b83-7ec9-488d-95cf-8f559a8a1b1f)
