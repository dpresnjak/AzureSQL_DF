# Overview
This template deploys the following resources:
* SQL Server/s
* SQL Database
* Storage Account
* Storage Container
* EventHub with Capture
* Key Vault
* Data Factory

This branch also has lines referring to an existing virtual network which is not created in this template. In this case there are already existing virtual desktops setup for accessing resources within the vNet.

Depending on the environment, for Production, it will deploy two SQL Servers in a Failover Group with replication. Otherwise only one SQL Server will be deployed. Production environment also has additional auditing setup, automatic ledger digest enabled. All authentication is done through Entra ID with a couple of Role Assignments being created, although this assumes there are sufficient privileges to create resources in a chosen Resource Group.


# Template parameters
Parameters are specified in the first section of the deployment ARM template, and they are used to avoid hard-coding information into the template. Parameters are also used to make this template environment-agnostic, meaning that it can be used across different environments, Resource Groups, or Subscriptions.

Every parameter has a description that can be read by hovering over the information icon which helps with understanding different options, along with set default values.

###Formatting expressions explanation:
* [format('**{0}***{1}*{2}', **dpres-sql**', *parameters('env')*, '01')]
* This means that the value inside the format() method will be formatted according to the first segment ({0}{1}{2}), with segment numbering starting after the first segment.
* The above expression would evaluate to *dpres-sql-dev-01*, if the env parameter is set to dev for the development environment.

