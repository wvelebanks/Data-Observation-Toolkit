# Deploying in Airflow
This setup serves as a proof-of-concept to demonstrate how Airflow can be configured to run DOT across multiple databases. It is designed to copy data from the **data** database back into the **DOT** database. In a production environment, the flow would instead transfer data from the source production database into the data_ schema of the DOT database. This configuration assumes you have already completed the Docker environment setup, as outlined in the previous section.

## Configuring/Building Airflow Docker environment

#### 🌟 Optional but Highly Recommended 🌟

If you wish to include the user interface (UI) while building the containers for DOT, you will need to add the following code snippet. This snippet can be found in the `docker-compose.yml` file, specifically on lines 31-38. Copy the code and insert it into the `docker-compose-with-airflow.yml` file, ensuring that the code is placed below line 92. Make sure to maintain the proper indentation.

```yaml
appsmith:
  image: index.docker.io/appsmith/appsmith-ce
  container_name: appsmith
  ports:
    - "82:80"
    - "446:443"
  volumes:
    - ./appsmith/stacks:/appsmith-stacks
```
Additionally, in the docker-compose-with-airflow.yml file, remove line 61 as it is redundant. Set the configuration AIRFLOW__CORE__LOAD_EXAMPLES to False as shown below:
```yaml
AIRFLOW__CORE__LOAD_EXAMPLES: 'False'
```
🌟🌟

### Step-by-Step Instructions to Set Up Airflow and Run DOT with Docker
1. Navigate to the Docker directory:
   ```bash
   cd ./docker
   ```
2. Set the PostgreSQL password environment variable:
  ```bash
  export POSTGRES_PASSWORD=<THE PASSWORD YOU USED WHEN BUILDING DOT>
  ```
  Replace <THE PASSWORD YOU USED WHEN BUILDING DOT> with the actual password.

3.  Build the Docker containers using docker-compose-with-airflow.yml:
   ```bash
    docker compose -f docker-compose-with-airflow.yml build
   ```
  _**Note** in case you get an error related to ssh-agent, be sure to use the following:_
      ```eval $(ssh-agent)  ==> for windows users      Or    eval ssh-agent  ==> for Mac/Linux users
      ```
4.  Initialize the Airflow containers:
   ```bash
    docker compose -f docker-compose-with-airflow.yml up airflow-init
   ```
5.  Start the containers in detached mode:
   ```bash
   docker compose -f docker-compose-with-airflow.yml up -d
   ```
6.  Access the Airflow worker container:
   ```bash
   docker exec -it docker-airflow-worker-1 /bin/bash
   ```
7.  Navigate to the dot directory and run the installation script:
   ```bash
    cd /app/dot && ./install_dot.sh
   ```
    
These steps will build and initialize your Docker containers, set up Airflow, and install DOT in the appropriate environment.

### Notes:
- Make sure to replace `<THE PASSWORD YOU USED WHEN BUILDING DOT>` with the actual password used during setup.
- If you face any issues with the container names (like `docker-airflow-worker-1`), check the container name using the `docker ps` command to confirm the exact name.
-** _If using Docker on AWS, you might need to use docker-compose instead of docker compose.**_