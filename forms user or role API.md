## Formsflow-forms user/role API

There are two ways in which you can access data from the formsflow-forms end points.

* [Using curl command](#using-curl-command)
* [Using POSTMAN API client](#using-postman-api-client)

### Using curl command

* Download and install [curl](https://curl.se/download.html).

* [Step 1](#step-1) Go to `forms-flow-forms/script` directory.
* [Step 2](#step-2)
  * **For windows**
    * Open command prompt and run `resourceId_windows.bat {user email} {password}` eg: `resourceId_windows.bat admin@example.com changeme`
  * **For Linux and Mac**
    * Open command prompt and run `./resourceId_linux.sh {user email} {password}` eg: `./resourceId_linux.sh admin@example.com changeme`
* [Step 3](#step-3) Copy the ID corresponding to Role Name from [Step 2](./README.md#step-2) and paste it against the Environment Variable name from the below table.

|Role Name | Environment Variable Name |
|--- |---
|Administrator | DESIGNER_ROLE_ID
|Anonymous | ANONYMOUS_ID
|formsflow Client | CLIENT_ROLE_ID
|formsflow Reviewer | REVIEWER_ROLE_ID
|User | USER_RESOURCE_ID

> **curl requests are successfully completed. You can skip the remaining sections in this page and continue with other installation steps.**

### Using POSTMAN API client

* Download and install [Postman API client](https://www.postman.com/)
* Import [formsflow-forms-postman-collection.json](./config/formsflow-forms-postman-collection.json) to your postman client.
  * Open Postman -> Go to File
    * Import -> Upload [formsflow-forms-postman-collection.json](./config/formsflow-forms-postman-collection.json) file
    * Import successful.
* Follow the instructions given below to fetch the role id's from [forms-flow-forms](http://localhost:3001)
  * Open Postman ->  Go to Workspaces -> My Workspaces
    * Collections -> Open form.io collection and send the API request in the following order.
       * Get the jwt token using resource **<http://localhost:3001/user/login>**. (*Click on Send to make a server request*)
       * Get the user resource id using resource **<http://localhost:3001/user>**. (*Click on Send to make a server request*)
        * Copy the **_id** from Response body and replace value for **USER_RESOURCE_ID** in the **.env** file.
       * Get the user role id's using resource **<http://localhost:3001/role>**. (*Click on Send to make a server request*)
         Copy the ID's in the .env file

> **Postman API calls are successfully completed
