# Cloud Native App Architecture Walkthrough : L100

## Overview

Contoso Traders is one of the leading E-Commerce platforms with a wide range of electronic products like desktops and laptops, mobile phones, gaming console accessories, and monitors. This includes a wide range of international brands like Microsoft Surface, XBOX, Samsung, ASUS, DELL etc. Contoso Traders Organization is using Microsoft 365 for their collaboration works internally.

Contoso Traders has different departments like marketing, sales, accounts, HR, and IT. For internal communication, they are using Microsoft Teams and Outlook. In the Contoso Traders organisation, there are various functionalities with the Contoso Traders E-commerce platform like product approval, product price approval, Product price update approval etc. 

## Context

You will explore the Contoso traders code base present in a GitHub repository which contains all the files related to the application’s UI, backend APIs, deployment files, GitHub workflows, and deployment guides. You will also launch the application and review the functionalities of it.

## Solution Architecture

Contoso Traders is a 2 tier application and consists of Client tier.

Presentation tier conatins the React JS application that acts as a client, collects the the information given by the user and passes it to Database tier. It consists of a collection of small, autonomous services. Each service is self-contained and should implement a single business capability within a bounded context. A bounded context is a natural division within a business and provides an explicit boundary within which a domain model exists.

Backend tier consists of 3 API components that are containerized.

1. Shopping Cart: An Azure containerized app 
2. Produtcs &Inventory: Contains a kubernetes cluster
3. Image Search: Containerized app service.

The workflow named Contoso-traders-infra-provisioning.yml will invoke the Bicep template that deploys the ACI app and AKS cluster.

### MICROSERVICES

Microservices are a popular architectural style for building applications that are resilient, highly scalable, independently deployable, and able to evolve quickly. It consists of a collection of small, autonomous services. Each service is self-contained and should implement a single business capability within a bounded context. A bounded context is a natural division within a business and provides an explicit boundary within which a domain model exists.

 * Shopping Cart: A place on a website that keeps a record of the items that you have chosen to buy from the website, until you pay for it.
   - Azure Container App: Fully managed serverless container service for building and deploying modern apps at scale which helps in deploying containerised apps without managing complex infrastructure.
   - Azure Cosmos DB: A fully managed NoSQL and relational database for modern app development.

 * Products and Stocks/Inventory: A product is any item or service you sell to serve a customer's need or want. Inventory refers to a company's goods and products that are ready to sell, along with the raw materials that are used to produce them.
   - Azure Kubernetes service: Simplifies deploying a managed Kubernetes cluster in Azure by offloading the operational overhead to Azure. Controller commands, Service layer repositories and Data Model encapsulated in AKS.
   - Azure SQL: Azure SQL Database is an always-up-to-date, fully managed relational database service built for the cloud. Build your next app with the simplicity and flexibility of a multi-model database that scales to meet demand. Here, in this application azure sql holds the data of products.
   - Azure Cosmos DB: It offers single-digit millisecond response times, automatic and instant scalability, along with guarantee speed at any scale. Here, in this application Cosmos DB holds the data of Stocks/Inventory.

 * Image Search: An image search engine is a tool that helps you find appropriate images to use in your online store.
   - App Service (Containerized): A service that enables a developer to deploy containers on the Microsoft Azure public cloud without having to provision or manage any underlying infrastructure.
   - Cognitive Service (Computer Vision): An AI service that analyzes content in images and video. The Computer Vision service provides developers with access to advanced algorithms for processing images and returning information.
   - Storage Account: The storage account provides a unique namespace which provides highly available, durable, scalable and redundant storage. Here, in this application storage accounts stores the images of the products available in the application.


![](https://raw.githubusercontent.com/microsoft/ContosoTraders/main/docs/architecture/contoso-traders-enhancements.drawio.png)


## Steps

1. Open browser, using a new tab navigate to https://github.com/CloudLabs-AI/ContosoTraders GitHub repository. This repository conatins all the neccessary files and documents which will guide you to host the contoso traders application from the scratch.

1. Navigate to github/workflows folder, it contains the workflow YAML files using which you can the deployment resources. Please see the individual workflows for more information.

1. contoso-traders-infra-deployment.yml will deploy the infrastructure into Azure which includes resource groups, resources, sets access policies to key vaults, and seeds the database from storage accounts into an Azure SQL database.

1. contoso-traders-app-deployment.yml deploys the application to Azure cloud. The application is configured to use the pre-deployed resources.

1. contoso-traders-load-testing.yml configures the load testing for the application.

