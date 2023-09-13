# java_sql




**Application Setup:**
- I  Configured the Employee Management System application.

**AWS EC2 Instance Creation:**

- An AWS EC2 instance was created for hosting the database server (PostgreSql)
- 
- Also its security groups were configured 

**PostgreSQL Installation and Configuration:**
 
- PostgreSQL was installed on the EC2 instance.
- I set up a password for the PostgreSQL user "postgres."
- The "employee_app" database was created to support the application.
- Within the "employee_app" database, i defined a table named "employees" with attributes like id, firstname, lastname, and email.
- Configured the psql for listening to the public ip addresses to get the remote requests
<img src="https://github.com/j-rin/java_sql/blob/main/new/Screenshot%20from%202023-09-13%2017-05-54.png" width="600" height="300">

**EBS Volume Addition:**


<img src="https://github.com/j-rin/java_sql/blob/main/new/Screenshot%20from%202023-09-13%2017-07-58.png" width="600" height="300">

- For the data reliability, i attached an additional Elastic Block Store (EBS) volume (/dev/xvdfa) to the EC2 instance and configured the necessary mounting(/mnt/my_ebs_volume).
  
- Automation of backups was implemented using crontab, with the bash script ,It is also given in the github .And tested for its working by running the bashscript and the backup file was generated with the details of database 


  
<img src="https://github.com/j-rin/java_sql/blob/main/new/Screenshot%20from%202023-09-13%2021-29-46.png" width="600" height="300">

**Configuration:**
- Configuration details, including the database URL, username, and password, were added to the application.properties to the java application .This is done so that application connects correctly and the data is fetched from the database  

**Maven Build:**

- The application was packaged into a JAR file using Maven.
  
- java version 17 was also installed for running it and configured the path

**Docker**

- I created a Dockerfile to generate a Docker image from the application.

- Dockerfile is given in the files

- The Docker image was pushed to Docker Hub for convenient sharing and distribution ,(jerinpaul/java-app:latest)

<img src="https://github.com/j-rin/java_sql/blob/main/new/Screenshot%20from%202023-09-13%2021-36-12.png" width="600" height="300">

**Kubernetes**

- A Kubernetes cluster was established using kubeadm, featuring two worker nodes.

- All  of the default pods within the Kubernetes cluster were working properly by checking the pods using kubectl commands.

- Deployment and Service files were applied to Kubernetes using kubectl with necessary details  to deploy the application.These files are also given in repo

<img src="https://github.com/j-rin/java_sql/blob/main/new/WhatsApp%20Image%202023-09-13%20at%204.39.54%20PM.jpeg" width="600" height="300">

**AWS**

- I configured an AWS target group to manage traffic routing to the application for the worker nodes .

- An AWS Application Load Balancer was created and linked to the target group to distribute traffic effectively.

- Created the security group that aws needeed for the application
<img src="https://github.com/j-rin/java_sql/blob/main/new/WhatsApp%20Image%202023-09-13%20at%204.39.53%20PM.jpeg" width="600" height="300">

**Jenkins Pipeline**
   
<img src="https://github.com/j-rin/java_sql/blob/main/new/Screenshot%20from%202023-09-13%2017-02-26.png" width="600" height="300">

- Automation was introduced via a Jenkins pipeline using a declarative pipeline script.

  **GitHub Repository Integration:**
      - The pipeline was set up to clone my GitHub repository.

  **Build and Packaging:**
      - Maven was employed within the pipeline for building the project using "mvn clean package."

   **Docker Image Creation and Push:**
      - The pipeline included the creation of a Docker image from the Dockerfile and its subsequent push to Docker Hub.

   **Integration with Sonarqube:**
      - Sonarqube was integrated into the pipeline to perform code analysis.

   **Docker Deployment in Tomcat:**
      - Docker was used to deploy the application within a Tomcat container.
