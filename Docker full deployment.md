# formsflow.ai - Docker Setup

This page elaborates how to setup the overall solution using docker.


## Table of Contents
1. [Application Setup](#application-setup)
   * [Step 1 : Installation Steps](#installation-steps)
   * [Step 2 : Running the Application](#running-the-application)
   * [Step 3 : Health Check](#health-check)
2. [Usage Instructions](#usage-instructions)

## Application Setup

* The application will be installed in the following order.
* Some of the services have dependencies, mentioned below.

 Srl No | Service Name | Usage | Access | Dependency | Details |
--- | --- | --- | --- | --- | ---
1|`Keycloak`|Authentication|`http://localhost:8080`||[Keycloak](../../forms-flow-idm/keycloak/README.md)
2|`forms-flow-forms`|form.io form building. This must be started earlier for resource role id's creation|`http:/localhost:3001`||[forms-flow-forms](../../forms-flow-forms/README.md)
3|`forms-flow-analytics`|Redash analytics server, This must be started earlier for redash key creation|`http://localhost:7000`|`Keycloak`|[forms-flow-analytics](../../forms-flow-analytics/README.md)
4|`forms-flow-web`|formsflow Landing web app|`http://localhost:3000`|`Keycloak`, `forms-flow-forms`, `forms-flow-analytics`|[forms-flow-web](../../forms-flow-web/README.md)
5|`forms-flow-api`|API services|`http://localhost:5000`|`Keycloak`|[forms-flow-api](../../forms-flow-api/README.md)
6|`forms-flow-bpm`|Camunda integration|`http://localhost:8000/camunda`|`Keycloak`|[forms-flow-bpm](../../forms-flow-bpm/README.md)

### Installation Steps

> Make sure you have a Docker machine up and running.

#### Keycloak Setup

Follow the instructions given [here](https://github.com/athira-aot/athira-aot.github.io/blob/main/keycloak%20setup.md)

#### forms-flow-analytics Setup
------------------------------

Start the **analytics server** by following the instructions given [here](../../forms-flow-analytics/README.md)
   
#### forms-flow-forms Setup       
---------------------------
Follow the steps [here](../../forms-flow-analytics/README.md)

#### forms-flow-web, forms-flow-bpm & forms-flow-api Setup

  Follow the steps [here](../../forms-flow-analytics/README.md)
### Health Check
* Analytics should be up and available for use at port defaulted to 7000 i.e. http://localhost:7000/
* Business Process Engine should be up and available for use at port defaulted to 8000 i.e. http://localhost:8000/camunda/
* FormIO should be up and available for use at port defaulted to 3001 i.e. http://localhost:3001/
* formsflow.ai Rest API should be up and available for use at port defaulted to 5000 i.e. http://localhost:5000/checkpoint
* formsflow.ai web application should be up and available for use at port defaulted to 3000 i.e. http://localhost:3000/
* Access credentials are mentioned [here](../README.md#verifying-the-installation-status).
* 
### Docker based full installation is completed now.

### Usage Instructions

> End to end usage of formsflow.ai is mentioned in this section with sample forms and workflows.

* The complete usage instructions with examples are mentioned [here](./../../USAGE.md).
