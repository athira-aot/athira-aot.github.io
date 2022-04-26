#### forms-flow-forms Setup    
Make sure your current working directory is "/forms-flow-ai/deployment/docker".
Rename the file sample.env to .env.
Modify the environment variables in the newly created .env file if needed. Environment variables are given in the table below,
NOTE : {your-ip-address} given inside the .env file should be changed to your host system IP address. 
![image](https://user-images.githubusercontent.com/86649870/165291838-bef2cecb-6870-4506-9fdc-045a7f3f648d.png)
Start the forms-flow-forms service.
     - For Linux
       - Run `docker-compose -f docker-compose-linux.yml up -d forms-flow-forms` to start.  
     - For Windows  
       - Run `docker-compose -f docker-compose-windows.yml up -d forms-flow-forms` to start.  
       
##### Health Check
------------------
   - Access forms-flow-forms at port defaulted to 3001 i.e. http://localhost:3001/ .
   
           Default Login Credentials
           -----------------
           User Name / Email : admin@example.com
           Password  : changeme   
