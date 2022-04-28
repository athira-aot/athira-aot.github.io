# Analytics Engine

![Redash](https://img.shields.io/badge/Redash-10.1.0-blue)

**formsflow.ai** leverages [Redash](https://github.com/getredash/redash) to build interactive
dashboards and gain insights. To create meaningful visualization for
your use case with formsflow.ai checkout [Redash Knowledge base](https://redash.io/help/).

## Table of Content


1. [Solution Setup](#solution-setup)
   * [Step 1 : Installation](#installation)
   * [Step 2 : Running the application](#running-the-application)
   * [Step 3 : Health Check](#health-check)
   * [Step 4 : Configuration of Keycloak SAML Setup](#configuration-of-keycloak-saml-setup)
3. [Get the Redash API key](## Get the Redash API Key)
4. [Redash how to use guide](#redash-how-to-use-guide)


## Solution Setup

### Installation

* Make sure you have a Docker machine up and running.
* Make sure your current working directory is "forms-flow-ai/forms-flow-analytics".
* Rename the file [sample.env](./sample.env) to **.env**.
* Modify the environment variables inside [.env](./sample.env) file if needed. Environment variables are given  below


![image](https://user-images.githubusercontent.com/86649870/165745594-0248f682-d881-4847-8c5c-79bfdb466cc9.png)
### Running the application

* Analytics service uses port 7000, make sure the port is available.
* `cd {Your Directory}/forms-flow-ai/forms-flow-analytics`

> The forked version of redash is being used to overcome the limited cors support in redash. The forked repo fixes the cors issues. But if the environment is setup in such a way that redash resides in the same url origin as forms web application , redash can be built from any redash images.

* For Linux,
  * Run `docker-compose -f docker-compose-linux.yml run --rm server create_db` to setup database and to create tables.
  * Run `docker-compose -f docker-compose-linux.yml up -d` to start.
* For Windows,
  * Run `docker-compose -f docker-compose-windows.yml run --rm server create_db` to setup database and to create tables.
  * Run `docker-compose -f docker-compose-windows.yml up -d` to start.

### Health Check
click [here](https://github.com/athira-aot/athira-aot.github.io/blob/main/Health%20check.md)

- The application should be up and available for use at port defaulted to 7000 in  <http://localhost:7000/> and register with any valid credentials.
    

### Configuration of Keycloak SAML Setup

* Post registration, login to the application with admin credentials.
* Click the menu icon to the left of the username and navigate to **Edit Profile**.
* Go to tab "Settings", and then navigate to "General". Under "Authentication".
  * Check the option "Enabled(dynamic)".
  * Set the field "SAML Metadata URL" with value of Keycloak SAML descriptor URL. Example. <http://{your-ip-address}:8080/auth/realms/forms-flow-ai/protocol/saml/descriptor>. {your-ip-address} should be changed to your host system IP address. Please take special care to identify the correct IP address if your system has multiple network cards
  * Set the field "SAML Entity ID" value to be `forms-flow-analytics`.
  * Set the field "SAML NameID Format" value to be `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress`.
* Logout and login again using valid formsflow.ai keycloak user credentials. Default user credentials are provided [here](../forms-flow-idm/keycloak/README.md#formsflow-ai-user-credentials).

> forms-flow-analytic (REDASH) setup is successfully completed now. You can skip remaining sections in this page and continue with other installation steps.

## Get the Redash API Key

[here](https://github.com/athira-aot/athira-aot.github.io/blob/main/Get%20Redash%20API%20key.md)

## Redash how to use guide

* Check our guide on [how to configure Redash and come up with awesome visualization using redash](./docs/README.md).

* If you want to visualize based on data in formsflow.ai, [a few sample queries for default forms are available](./docs/sample_queries.md).

