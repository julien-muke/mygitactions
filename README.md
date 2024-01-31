# ![image](https://github.com/julien-muke/mygitactions/assets/110755734/6f563446-e59e-44c5-b977-b0e16ddc7edc) Github Actions CI/CD


![actions-logo](https://github.com/julien-muke/mygitactions/assets/110755734/aeb3b495-b4e2-4981-bd75-240593ce5f69)


## 🤖 Introduction

In this tutorial we will discuss about websocket APIs web circuit APIs support two-way communication that is both the users and the back-end can send messages back and forth once connected so it's used in real-time applications like charts broadcast messages or real-time dashboards you can create websocket APIs in AWS using aws API Gateway Service.

## 	📝 Hands-on Overview

The sample use case that we are going to see today is a real-time chat application with few components:

* First is obviously the API gateway service itself which is used to set up the application 
* And will be connected to three different lambdas to perform three different actions to establish connection to send messages  
* Finally to disconnect then we have a dynamodb table which keeps track of all the current connections.

## 🚨 AWS Services Used

* Amazon API Gateway
* AWS Lambda
* Amazon DynamoDB