# ![image](https://github.com/julien-muke/mygitactions/assets/110755734/6f563446-e59e-44c5-b977-b0e16ddc7edc) Github Actions CI/CD


![actions-logo](https://github.com/julien-muke/mygitactions/assets/110755734/aeb3b495-b4e2-4981-bd75-240593ce5f69)


## 🤖 Introduction

Github Actions is the built-in CI/CD tool for Github, CI/CD stands for Continuous Integration and Continuous Delivery, essentially it allows us to automate the testing of our code to make sure it meets certain criteria after all the tests are passed you can enable actions to automate the delivery of your code this can significantly reduce the time it takes for you to deliver updates to your application which allows developers to focus more of their time on the code itself.

In this tutorial, i'm going to go over all the theory you need to know to understand the github action workflow.

## 	📝  Overview

In the lab portion of this tutorial we'll go over how to implement our own Github action and implement a Linter that will run checks against our code to make sure that it meets specific criteria.

* First is obviously the API gateway service itself which is used to set up the application 
* And will be connected to three different lambdas to perform three different actions to establish connection to send messages  
* Finally to disconnect then we have a dynamodb table which keeps track of all the current connections.

## 🚨 AWS Services Used

* Amazon API Gateway
* AWS Lambda
* Amazon DynamoDB