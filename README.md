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


5. We can go ahead and commit, you can create a new branch or just commit to the main branch i'm going to commit to the main branch


![Screenshot 2024-01-31 at 13 23 36](https://github.com/julien-muke/mygitactions/assets/110755734/85fa7f14-7ff6-4bb6-944e-6fd2d04361a6)


NOTE: This directory structure needs to be exactly like this if your workflow is not triggering it's probably because the directory structure isn't named correctly

6. Let's go back to the main repository click "Code" and you should notice that there's this little status icon and you can see it's yellow, basically what this is saying is it's currently running the workflow and checking the code if all the checks pass then this is going to turn green, if the checks fail then it's going to turn red, click "Actions" tab

![Screenshot 2024-01-31 at 13 25 34](https://github.com/julien-muke/mygitactions/assets/110755734/cd788f0f-52a3-46fa-859b-85bcd4cabc3f)


7. It will take few seconds and run the workflow, and the workflow that it's running is super linter, it will:

Set up the job
Pull the code from GitHub Super Linter
Checkout the code
Run Super-Linter
Post Chechout code
Complete job


![Screenshot 2024-01-31 at 13 30 18](https://github.com/julien-muke/mygitactions/assets/110755734/22dbf8bc-ccf3-413a-a00c-3988ff684231)


8. If we head on back to code here we can see we get a nice little check mark to show that all the workflow checks have passed



![Screenshot 2024-01-31 at 13 32 24](https://github.com/julien-muke/mygitactions/assets/110755734/135b4f2c-5832-48dd-bad6-7dafeb963db9)



NOTE: This is another really cool thing that you can actually use downstream you could have your servers monitor the
GitHub API and just check the status of the repository, if the status was a green check mark it could automatically go to that
repository and pull down your code and implement it into staging or production or whatever you want.


## Step 2️⃣ : Let's test and push some code that we know is going to generate some Linting Errors

1. Go to "Add file" then click "Create new file"
2. Let's name it `main.py`
3. Copy and paste this simple python code below:

NOTE: There's some syntax problems with this code that is not going to pass the Linting
check (for example, there should actually be two lines between each function, the code style isn't very consistent this is what's considered messy code and the Linter is not gonna like, it it's gonna fail it )


```py
    def hello():
         print("hi")

def bye():
  print("bye")

print(hello())
```

4. Let's go ahead and save this commit it and watch to see what the Linter does
5. Let's refresh and we can see that it is triggered now if we just click the yellow icon, you can it's in progress check and we can just go details

![Screenshot 2024-01-31 at 13 43 23](https://github.com/julien-muke/mygitactions/assets/110755734/74d6d885-080c-463f-a061-0d54ef884a2d)


6. Our Super-Linter has run and we can see that there is an error in our workflow right here on the run Super-Linter, let's go into it and i'll show you sort of how to troubleshoot these errors


![Screenshot 2024-01-31 at 13 56 47](https://github.com/julien-muke/mygitactions/assets/110755734/c789cb1f-b460-4971-ab6d-c0d6bdc594eb)


7. Basically the code and the `+` are the lines that it would add and the `-` are the lines it would remove.


![Screenshot 2024-01-31 at 13 56 47](https://github.com/julien-muke/mygitactions/assets/110755734/6caa73d5-10b2-4596-9637-f784d2660780)


8. Let's check and fix the Errors, go to "Edit"

```py
    def hello():
    print("hi")


def bye():
    print("bye")


print(hello())
```


9. We can see that everything passed, if you go to actions and check the details of the latest job and you can see that the Super Linter ran and everything looks good.


![Screenshot 2024-01-31 at 14 06 26](https://github.com/julien-muke/mygitactions/assets/110755734/3f3ee412-ad28-4c1c-a800-c10912a825a3)


10. Let's just explore the GitHub actions a little bit more we'll go up to "Actions" and you can see that we have a history of all our workflow jobs, first one was our first run successfully and other one was the second run we added the python file with the bad formatting and then last one after that we fixed the errors.


![Screenshot 2024-01-31 at 14 08 52](https://github.com/julien-muke/mygitactions/assets/110755734/ad2fac8e-8628-48be-8fa2-4584d2c69fa3)



NOTE: if you wanted to go through a guided setup instead of just writing your file from scratch like we did you can go new workflow right here and you can see that there's a lot of templated options. There's a marketplace with a lot of canned workflows that you can just grab and then you can just modify the file to meet your needs so that's a really good option


![Screenshot 2024-01-31 at 14 10 08](https://github.com/julien-muke/mygitactions/assets/110755734/eecefbde-8658-45df-af8d-f723bb56c33f)
