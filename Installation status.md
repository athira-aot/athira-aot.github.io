## Verifying the Installation status

> The following applications will be started and can be accessed in your browser.

 Srl No | Service Name | Usage | Access | Default credentials (userName / Password)|
--- | --- | --- | --- | --- 
1|`Keycloak`|Authentication|`http://localhost:8080`| `admin/changeme`
2|`forms-flow-forms`|form.io form building. This must be started earlier for resource role id's creation|`http://localhost:3001`|`admin@example.com/changeme`
3|`forms-flow-analytics`|Redash analytics server, This must be started earlier for redash key creation|`http://localhost:7000`|Use the credentials used for registration / [Default user credentials](../forms-flow-idm/keycloak/README.md#formsflow-ai-user-credentials)
4|`forms-flow-web`|formsflow Landing web app|`http://localhost:3000`|[Default user credentials](../forms-flow-idm/keycloak/README.md#formsflow-ai-user-credentials)
5|`forms-flow-api`|API services|`http://localhost:5000`|`Authorization tocken from keycloak role based user credentials`
6|`forms-flow-bpm`|Camunda integration|`http://localhost:8000/camunda`| [Default user credentials](../forms-flow-idm/keycloak/README.md#formsflow-ai-user-credentials) 
