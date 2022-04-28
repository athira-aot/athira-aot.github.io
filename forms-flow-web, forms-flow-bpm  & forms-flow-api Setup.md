#### forms-flow-web, forms-flow-bpm & forms-flow-api Setup

 Make sure your current working directory is "/forms-flow-ai/deployment/docker".
Modify the environment variables inside .env file if needed. Environment variables are given below

###formsflow.ai keycloak variable settings

![image](https://user-images.githubusercontent.com/86649870/165292594-9f275114-916d-4519-8ff1-ac9eace3b7b5.png)

###formsflow.ai analytics variable settings
![image](https://user-images.githubusercontent.com/86649870/165292745-d5d6f96c-7ded-4b6e-aa06-dcf28919a9b6.png)

##### formsflow.ai analytics variable settings
![image](https://user-images.githubusercontent.com/86649870/165293246-da9c7fd2-067e-4d6c-a9c8-8460bb3ea461.png)


Get the Get the Redash API Key' steps from `[here](https://github.com/athira-aot/athira-aot.github.io/blob/main/Get%20Redash%20API%20key.md)
##### formsflow.ai forms variable settings
-----------------------------------

Getting **ROLE_ID** and **RESOURCE_ID** are mandatory for role based access. 
To generate ID go to ["Formsflow-forms user/role API"](https://github.com/athira-aot/athira-aot.github.io/blob/main/forms%20user%20or%20role%20API.md) and follow the steps.

##### formsflow.ai Datastore variable settings
-----------------------------------
![image](https://user-images.githubusercontent.com/86649870/165462763-bd72c319-8800-46bc-b531-fba62e2bbfaf.png)
##### formsflow.ai Integration variable settings
--------------------------------------

Variable name | Meaning | Possible values | Default value |
--- | --- | --- | ---
`NODE_ENV`| Define project level configuration | `development, test, production` | `development`
`APPLICATION_NAME`| Application_Name | eg: formsflow.ai| `formsflow.ai`
`WEB_BASE_CUSTOM_URL`| Custom_URL | eg: https://formsflow.ai| `custom url`
`FORMSFLOW_API_CORS_ORIGINS`| formsflow.ai Rest API allowed origins, for allowing multiple origins you can separate host address using a comma seperated string or use * to allow all origins |eg:`host1, host2, host3`| `*`
`CAMUNDA_API_URL` :triangular_flag_on_post: |Camunda Rest API URL||`http://{your-ip-address}:8000/camunda`
`FORMSFLOW_API_URL`:triangular_flag_on_post:|formsflow.ai Rest API URL||`http://{your-ip-address}:5000`
`USER_ACCESS_PERMISSIONS`| JSON formatted permissions to enable / disable few access on user login.|| `{"accessAllowApplications":false,"accessAllowSubmissions":false}`

* NOTE - While configuring USER_ACCESS_PERMISSIONS the accessAllowApplications will hide / show application tab, the same way accessAllowSubmissions does for viewSubmission button. To enable this feature you need to add access-allow-applications, access-allow-submissions with the respective user group in keycloak.

##### CAMUNDA_JDBC : Dedicated camunda database.
--------------------------------------

   Variable name | Meaning | Possible values | Default value |
 --- | --- | --- | ---
 `CAMUNDA_JDBC_DB_NAME`|Postgres JDBC DB Name|Used on installation to create the database. Choose your own|`formsflow-bpm`
 `CAMUNDA_JDBC_URL`|Postgres JDBC DB Connection URL|Used on installation to create the database. Choose your own|`jdbc:postgresql://forms-flow-bpm-db:5432/formsflow-bpm`
 `CAMUNDA_JDBC_DRIVER`|Postgres JDBC Database Driver||`org.postgresql.Driver`
 `CAMUNDA_JDBC_USER`|Postgres Database Username|Used on installation to create the database. Choose your own|`admin`
 `CAMUNDA_JDBC_PASSWORD`|Postgres Database Password|Used on installation to create the database. Choose your own|`changeme`
 `CAMUNDA_HIKARI_CONN_TIMEOUT`|Hikari Connection optimization setting||`30000`
 `CAMUNDA_HIKARI_IDLE_TIMEOUT`|Hikari Connection optimization setting||`600000`
 `CAMUNDA_HIKARI_MAX_POOLSIZE`|Hikari Connection optimization setting||`10`
 `CAMUNDA_HIKARI_VALID_TIMEOUT`|Hikari Connection optimization setting||`5000`

##### Camunda System Tuning  
----------------------------

Variable name | Meaning | Possible values | Default value |
--- | --- | --- | ---
`CAMUNDA_JOB_CORE_POOL_SIZE`|Job-Executor Configuration Properties||`10`
`CAMUNDA_JOB_MAX_POOL_SIZE`|Job-Executor Configuration Properties||`20`
`CAMUNDA_JOB_QUEUE_SIZE`|Job-Executor Configuration Properties||`10`
`CAMUNDA_JOB_LOCK_TIME_MILLIS`|Job-Executor Configuration Properties||`300000`
`CAMUNDA_JOB_MAXJOBS_PER_ACQUISITION`|Job-Executor Configuration Properties||`10`
`CAMUNDA_JOB_WAIT_TIME_MILLIS`|Job-Executor Configuration Properties||`5000`
`CAMUNDA_JOB_MAX_WAIT`|Job-Executor Configuration Properties||`60000`
`CAMUNDA_METRICS_FLAG`|Job-Executor Configuration Properties||`false`
  
##### Camunda formsflow.ai Integration variable settings  
------------------------------------------------

Variable name | Meaning | Possible values | Default value |
--- | --- | --- | ---
`WEBSOCKET_SECURITY_ORIGIN` :triangular_flag_on_post:|Camunda task event streaming. Origin setting, for multiple origins you can separate host address using a comma |eg:`host1, host2`|`http://{your-ip-address}:3000`
`WEBSOCKET_MESSAGE_TYPE`|Camunda task event streaming. Message type ||`TASK_EVENT`
`WEBSOCKET_ENCRYPT_KEY`|Camunda task event streaming. AES encryption of token||`giert989jkwrgb@DR55`
 
```
Modify the file **mail-config.properties** (under `forms-flow-bpm/src/main/resources/`). The default settings provided are for the Gmail server, and you need to change the credentials at the bottom of the file. Note that you want to configure your own Gmail setting to allow unsecure apps first. 
```

##### Camunda - General variable settings  
-------------------------------

   Variable name | Meaning | Possible values | Default value |
 --- | --- | --- | ---
 `APP_SECURITY_ORIGIN`|CORS setup, for multiple origins you can separate host address using a comma |eg:`host1, host2`| `*` 
 `CAMUNDA_APP_ROOT_LOG_FLAG`|Log level setting||`error` 
 `DATA_BUFFER_SIZE`|Configure a limit on the number of bytes that can be buffered for webclient||`2 (In MB)`
 `IDENTITY_PROVIDER_MAX_RESULT_SIZE`|Maximum result size for Keycloak user queries||`250`
 `BPM_CLIENT_CONN_TIMEOUT`|Webclient Connection timeout in milli seconds||`5000`

### Running the application
* For Linux,
   * Run `docker-compose -f docker-compose-linux.yml up -d` to start.
* For Windows,
   * Run `docker-compose -f docker-compose-windows.yml up -d` to start.
   
*NOTE: Use --build command with the start command to reflect any future **.env** / code changes eg : `docker-compose -f docker-compose-windows.yml up --build -d`*

#### To stop the application
* For Linux,
  * Run `docker-compose -f docker-compose-linux.yml stop` to stop.
* For Windows,
  * Run `docker-compose -f docker-compose-windows.yml stop` to stop.
  

