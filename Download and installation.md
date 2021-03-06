# Download and Installation

In the following document, we’ll describe about the different project dependencies, and the installation options being supported.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Download the formsflow.ai](#download-the-formsflowai)
3. [Installation](#installation)
   * [Docker](#docker-based-installation)
   * [Openshift](#openshift-based-installation)
4. [Verifying the Installation Status](#verifying-the-installation-status)


## Prerequisites

* Admin access to a local or remote server (can be local Windows PC or Mac provided it is **64**-bit with at least **16GB** RAM and **25GB** HDD) 
* For docker based installation [Docker](https://docker.com) needs to be installed.
  * For **Mac**, make sure the [docker for mac](https://docs.docker.com/docker-for-mac/#resources) memory allocation is set to at least **16GB**. 



## Download the formsflow.ai

* Clone this github repo:  https://github.com/AOT-Technologies/forms-flow-ai
* If deploying to a remote server, you can use nginx as a reverse proxy and SSL engine. To help you, follow the instructions in the nginx [README](./server/nginx/README.md)

## Installation

There are multiple options for installing formsflow.ai. They are given below

- Docker Based installation
  - [Docker single click installation](#docker-single-click-installation)
  - [Docker Full Deployment](#Docker-Full-Deployment)
  - [Docker Individual Service Deployment](#Docker-Individual-Service-Deployment)
- Openshift Based Installation
  - [Openshift Full Deployment](#Openshift-Full-Deployment)

### Docker Based Installation

------------------
#### Docker single click installation

Download the compressed [bundle](./docker/bundle/bundle.zip/?raw=true) and follow the instructions from [readme](https://github.com/athira-aot/athira-aot.github.io/blob/main/Quick%20Installation.md).

#### Docker Full Deployment

Follow the instructions on [docker installation guide](./docker)
 
#### Docker Individual Service Deployment

Install the components in the listed order. *(NOTE: Keycloak, form.io and redash dependencies are used on other components)*
 * [Keycloak](../forms-flow-idm/keycloak) Identity keycloak components
 * [forms-flow-forms](../forms-flow-forms) formsflow.ai integration with form.io
 * [forms-flow-analytics](../forms-flow-analytics) Redash analytics components
 * [forms-flow-bpm](../forms-flow-bpm) Camunda Workflow deployment and integration
 * [forms-flow-api](../forms-flow-api) REST API of formsflow.ai
 * [forms-flow-web](../forms-flow-web) formsflow.ai integration web UI
 
### Openshift Based Installation

------------------
#### Openshift Full Deployment

 Follow the instructions on [openshift installation guide](https://github.com/athira-aot/athira-aot.github.io/blob/main/openshift%20installation%20.md)
