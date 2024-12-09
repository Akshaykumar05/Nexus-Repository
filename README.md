# Sonatype Nexus Repository
This repo contain details about Sonatype Nexus Repository, its local installation and use cases for DevOps methodology.

![image](https://github.com/user-attachments/assets/cb569e6b-633e-44f6-9530-858ee4b86c0d)


Sonatype Nexus Repository is a powerful tool for DevOps engineers and organizations practicing DevOps methodologies. It serves as a repository manager that enables teams to store, manage, and distribute software components efficiently throughout the software development lifecycle.

## Key Features of Nexus Repository:
1. Centralized Storage:
 * Acts as a single source of truth for managing binaries, artifacts, and dependencies.
 * Supports multiple formats like Maven, npm, Python (PyPI), Docker, Helm, RubyGems, NuGet, and more.
  
2. Integration with DevOps Pipelines:
 * Seamlessly integrates with CI/CD tools like Jenkins, GitLab CI/CD, GitHub Actions, and others.
 * Ensures faster builds by caching dependencies locally.
    
3. Repository Types:

 * **Hosted Repositories**: Store your organization's proprietary components.
 * **Proxy Repositories**: Cache and proxy external repositories like Maven Central or npmjs.org.
 * **Group Repositories**: Combine multiple repositories into a single endpoint for easier access.

4. Scalability and High Availability:

 * Scales to meet the needs of large teams and enterprises.
 * Provides high availability with clustering support.

5. Access Control and Security:
 * Granular user and role-based access control to secure your artifacts.
 * Supports integration with LDAP, SSO, and other identity providers.

6. Artifact Promotion:

 * Allows promoting artifacts across different stages (e.g., development, testing, staging, and production).

7. Support for Docker Images:

 * Can be used as a Docker registry (both private and public).
 * Manages Docker image lifecycle and optimizes storage.

8. Component Analysis (with Sonatype Nexus Lifecycle):

 * Tracks and monitors open-source components for vulnerabilities and license compliance issues.
 * Helps maintain secure software supply chains.

## Why Nexus Repository is Important for DevOps Engineers:
1. Dependency Management:

  * Speeds up builds by caching dependencies, reducing external downloads.
  * Ensures consistent versions of dependencies across environments.

2. Improved Workflow:

  * Simplifies artifact distribution across teams and environments.
  * Integrates with container orchestration tools like Kubernetes and Helm.

3. Enhanced Security:

  * Ensures only approved and secure components are used in builds.
  * Helps prevent supply chain attacks by providing detailed insights into vulnerabilities.

4. Efficiency and Traceability:

  * Tracks artifact versions and history, enabling rollback when needed.
  * Ensures compliance by keeping detailed metadata about artifacts.

5. Time Savings:

  * Reduces build times and manual management of dependencies.
  * Automates artifact promotion and clean-up tasks.

## Use Case Example:
A DevOps engineer working on a microservices architecture can use Nexus Repository to:

1. Host Docker images for services in a private Docker repository.
2. Proxy external Maven repositories to cache Java dependencies locally.
3. Manage Helm charts for deploying services to Kubernetes.
4. Monitor open-source dependencies for security vulnerabilities.

## Deployment Options:
1. Self-hosted: Install on your on-premises infrastructure.
2. Cloud-hosted: Available as SaaS to reduce operational overhead.
   
By incorporating Nexus Repository into your DevOps workflow, you gain control over your software supply chain, enhance build efficiency, and improve overall security posture.

-------------------
## LocaL Installation:
* Create a 'nexus' directory inside opt:
  ```
  cd /opt
  ```
  ```
  mkdir nexus
  ```
* Edit the yml file with following code:
  ```
  vim docker-compose.yml
  ```
  ```
  version: "3"
  services:
   nexus:
    image: sonatype/nexus3
    restart: always
    volumes:
      - "nexus-data:/sonatype-work"
    ports:
      - "8081:8081"
      - "8085:8085"
  volumes:
    nexus-data: {}
  ```

* Now open the nexus on browser using localhost/localIP and default port (8081)
  ```
  localhost:8081
  ```
  ![image](https://github.com/user-attachments/assets/15ec27f0-59f1-46ee-a0e9-c049cf512f6d)

* To login use the credentials
  - Username: admin
  - Password: you will get by following command
    ```
    docker exec -it container_id /bin/bash
    ```
    ```
    cat /nexus-data/admin.password
    ```
    
  ![nexus_pass](https://github.com/user-attachments/assets/dafec889-3afd-4e5f-b4e3-c14a0e90dcd5)

  - After login, we'll get the page
    ![Nexus_login](https://github.com/user-attachments/assets/994d489f-6d41-4b5c-a883-1845389fdefe)

* Now you can create repository and other task as per your demands.

------------
--------------
  
   

  
