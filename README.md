# Cloud Native App Architecture Walkthrough : L100

## Overview

Contoso Traders is one of the leading E-Commerce platforms with a wide range of electronic products like desktops and laptops, mobile phones, gaming console accessories, and monitors. This includes a wide range of international brands like Microsoft Surface, XBOX, Samsung, ASUS, DELL etc. Contoso Traders Organization is using Microsoft 365 for their collaboration works internally.

Contoso Traders has different departments like marketing, sales, accounts, HR, and IT. For internal communication, they are using Microsoft Teams and Outlook. In the Contoso Traders organisation, there are various functionalities with the Contoso Traders E-commerce platform like product approval, product price approval, Product price update approval etc. 

## Context

You will explore the Contoso traders code base present in a GitHub repository which contains all the files related to the application’s UI, backend APIs, deployment files, GitHub workflows, and deployment guides. You will also launch the application and review the functionalities of it.

## Solution Architecture

Contoso Traders is a 2 tier application and consists of Client tier

Presentation tier conatins the React JS application that acts as a client, collects the the information given by the user and passes it to Database tier.

Backend tier consists of 3 API components that are containerized.

1. Shopping Cart: An Azure containerized app 
2. Produtcs &Inventory: Contains a kubernetes cluster
3. Image Search: Containerized app service.

The workflow named Contoso-traders-infra-provisioning.yml will invoke the Bicep template that deploys the ACI app and AKS cluster.


## Steps

1. Open browser, using a new tab navigate to https://github.com/CloudLabs-AI/ContosoTraders GitHub repository. This repository conatins all the neccessary files and documents which will guide you to host the contoso traders application from the scratch.

1. Navigate to github/workflows folder, it contains the workflow YAML files using which you can the deployment resources. Please see the individual workflows for more information.

1. Contoso-traders-infra-deployment.yml will deploy the infrastructure into Azure which includes resource groups, resources, sets access policies to key vaults, and seeds the database from storage accounts into an Azure SQL database.

1. contoso-traders-app-deployment.yml deploys the application to Azure cloud. The application is configured to use the pre-deployed resources.

1. contoso-traders-load-testing.yml configures the load testing for the application.
