---
title: "How to Install SonarQube on Ubuntu 24.04"
datePublished: Fri May 23 2025 11:24:21 GMT+0000 (Coordinated Universal Time)
cuid: cmb0pqwbe001d09l7geri0w75
slug: how-to-install-sonarqube-on-ubuntu-2404
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1747999351600/36a41223-c78d-4c0e-b754-09b174474194.jpeg
tags: aws, security, sonarqube, devops, ci-cd

---

Learn to install SonarQube on Ubuntu 24.04, enhancing code quality and security with detailed insights and static analysis.

**Contents**

* [Prerequisites](https://docs.vultr.com/how-to-install-sonarqube-on-ubuntu-24-04#prerequisites)
    
* [Set Up a PostgreSQL Database for SonarQube](https://docs.vultr.com/how-to-install-sonarqube-on-ubuntu-24-04#set-up-a-postgresql-database-for-sonarqube)
    
* [Install SonarQube](https://docs.vultr.com/how-to-install-sonarqube-on-ubuntu-24-04#install-sonarqube)
    
* [Configure SonarQube](https://docs.vultr.com/how-to-install-sonarqube-on-ubuntu-24-04#configure-sonarqube)
    
* [Access SonarQube](https://docs.vultr.com/how-to-install-sonarqube-on-ubuntu-24-04#access-sonarqube)
    
* [Scan SonarQube Example Projects](https://docs.vultr.com/how-to-install-sonarqube-on-ubuntu-24-04#scan-sonarqube-example-projects)
    

SonarQube is an open-source platform used to continuously inspect code quality and manage code quality. It detects bugs, vulnerabilities, and tracks code quality through static analysis with detailed reports. SonarQube supports multiple programming languages and improves code quality, maintainability, and security by offering actionable insights with two editions, community and enterprise.

This article explains how to Install SonarQube on Ubuntu 24.04. You will install SonarQube and use it to inspect code quality with example projects on your workstation.

## **Prerequisites**

Before you begin, you need to:

* Have access to an [Ubuntu 24.04 instance](https://www.vultr.com/servers/ubuntu/) as a non-root sudo user.
    

## **Set Up a PostgreSQL Database for SonarQube**

SonarQube requires a PostgreSQL database to store data. PostgreSQL is available in the default package repositories on Ubuntu. Follow the steps below to install PostgreSQL and create a new database to use with SonarQube.

1. Install the PostgreSQL if it's not installed on your Ubuntu 24.04 workstation.
    
    ```plaintext
    $ sudo apt install -y postgresql-common postgresql -y
    ```
    
2. Enable the PostgreSQL database server to automatically start at boot.
    
    ```plaintext
    $ sudo systemctl enable postgresql
    ```
    
    Output:
    
    ```plaintext
    Synchronizing state of postgresql.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
    Executing: /usr/lib/systemd/systemd-sysv-install enable postgresql
    ```
    
3. Start the PostgreSQL database server.
    
    ```plaintext
    $ sudo systemctl start postgresql
    ```
    
4. Log in to the PostgreSQL database server as the `postgres` user.
    
    ```plaintext
    $ sudo -u postgres psql
    ```
    
5. Create a new `sonaruser` PostgreSQL role with a strong password to use with SonarQube. Replace `your_password` with your desired password.
    
    ```plaintext
    postgres=# CREATE ROLE sonaruser WITH LOGIN ENCRYPTED PASSWORD 'your_password';
    ```
    
6. Create a new `sonarqube` database.
    
    ```plaintext
    postgres=# CREATE DATABASE sonarqube;
    ```
    
7. Grant the `sonaruser` role full privileges to the `sonarqube` database.
    
    ```plaintext
    postgres=# GRANT ALL PRIVILEGES ON DATABASE sonarqube TO sonaruser;
    ```
    
8. Switch to the `sonarqube` database.
    
    ```plaintext
    postgres=# \c sonarqube
    ```
    
    Output:
    
    ```plaintext
    You are now connected to database "sonarqube" as user "postgres".
    ```
    
9. Grant the `sonaruser` role full privileges to the public schema.
    
    ```plaintext
    postgres=# GRANT ALL PRIVILEGES ON SCHEMA public TO sonaruser;
    ```
    
10. Exit the PostgreSQL database console.
    
    ```plaintext
    postgres=# \q
    ```
    

## **Install SonarQube**

SonarQube is not available in the default package repositories on Ubuntu 24.04 and requires OpenJDK 17 to run. Follow the steps below to download the latest SonarQube release file and install SonarQube.

1. Update the server's APT package index.
    
    ```plaintext
    $ sudo apt update
    ```
    
2. Install OpenJDK 17.
    
    ```plaintext
    $ sudo apt install openjdk-17-jdk -y
    ```
    
3. Install Unzip to extract files from the SonarQube archive.
    
    ```plaintext
    $ sudo apt install unzip
    ```
    
4. Verify the installed `java` version.
    
    ```plaintext
    $ java -version
    ```
    
    Your output should be similar to the one below:
    
    ```plaintext
    openjdk version "17.0.14" 2025-01-21
    OpenJDK Runtime Environment (build 17.0.14+7-Ubuntu-124.04)
    OpenJDK 64-Bit Server VM (build 17.0.14+7-Ubuntu-124.04, mixed mode, sharing)
    ```
    
5. Visit the [SonarQube releases page](https://binaries.sonarsource.com/?prefix=Distribution/sonarqube/) and verify the latest version to download. For example, `sonarqube-25.2.0.102705.zip`.
    
6. Download the latest SonarQube archive.
    
    ```plaintext
    $ sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-25.2.0.102705.zip
    ```
    
7. Extract files from the downloaded archive using Unzip.
    
    ```plaintext
    $ unzip sonarqube-25.2.0.102705.zip
    ```
    
8. Move the extracted files to a systemwide directory such as `/opt`.
    
    ```plaintext
    $ sudo mv sonarqube-25.2.0.102705/ /opt/sonarqube
    ```
    
9. Create a dedicated `sonarqube` system user without login privileges and a home directory.
    
    ```plaintext
    $ sudo adduser --system --no-create-home --group --disabled-login sonarqube
    ```
    
10. Grant the `sonarqube` user full privileges to the `/opt/sonarqube` directory.
    
    ```plaintext
    $ sudo chown -R sonarqube:sonarqube /opt/sonarqube
    ```
    

### **Install SonarScanner CLI**

SonarQube uses code scanners depending on the target programming language to scan and analyze code quality. SonarScanner CLI is the default scanner if no specific scanner is specified on your system. Follow the steps below to install the SonarScanner CLI to analyze code on your workstation.

1. [Visit the SonarScanner CLI page](https://github.com/SonarSource/sonar-scanner-cli/releases) and verify the latest version to download. For example, run the following command to download the SonarScanner CLI version `7.0.1`
    
    ```plaintext
    $ wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-7.0.1.4817-linux-x64.zip
    ```
    
2. Extract files from the archive depending on the downloaded version.
    
    ```plaintext
    $ unzip sonar-scanner-cli-7.0.1.4817-linux-x64.zip
    ```
    
3. Move the extracted directory to `/opt/sonarscanner`.
    
    ```plaintext
    $ sudo mv sonar-scanner-7.0.1.4817-linux-x64/  /opt/sonarscanner
    ```
    
4. Open the `sonar-scanner.properties` configuration file.
    
    ```plaintext
    $ sudo nano /opt/sonarscanner/conf/sonar-scanner.properties
    ```
    
5. Find the following `sonar.host.url` directive and change the default `https://mycompany.com/sonarqube` value to `127.0.0.1`.
    
    ```plaintext
    ...
    sonar.host.url=127.0.0.1
    ...
    ```
    
    Save and close the file.
    
    The above Sonar Host directive specifies the SonarQube server URL to use while performing code scans.
    
6. Enable execute permissions on the `sonar-scanner` binary.
    
    ```plaintext
    $ sudo chmod +x /opt/sonarscanner/bin/sonar-scanner
    ```
    
7. Link the `sonar-scanner` binary to the `/usr/local/bin` directory to enable it as a system-wide command.
    
    ```plaintext
    $ sudo ln -s /opt/sonarscanner/bin/sonar-scanner /usr/local/bin/sonar-scanner
    ```
    
8. View the installed SonarScanner version.
    
    ```plaintext
    $ sonar-scanner -v
    ```
    
    Your output should be similar to the one below.
    
    ```plaintext
    ........
    13:33:31.946 INFO  SonarScanner CLI 7.0.1.4817
    13:33:31.950 INFO  Java 17.0.13 Eclipse Adoptium (64-bit)
    13:33:31.951 INFO  Linux 6.8.0-51-generic amd64
    ```
    

## **Configure SonarQube**

SonarQube requires specific configurations for optimal performance, including database connections, Java runtime options, system resource limits, and user permissions. Follow the steps below to configure SonarQube to run on your server.

1. Open the main `sonar.properties` Sonarqube configuration file.
    
    ```plaintext
    $ sudo nano /opt/sonarqube/conf/sonar.properties
    ```
    
2. Add the following configurations at the end of the file. Replace `sonaruser` and `your_password` with actual PostgreSQL database user details.
    
    ```plaintext
    sonar.jdbc.username=sonaruser
    sonar.jdbc.password=your_password
    sonar.jdbc.url=jdbc:postgresql://localhost:5432/sonarqube
    sonar.web.javaAdditionalOpts=-server
    sonar.web.host=0.0.0.0
    sonar.web.port=9000
    ```
    
    Save and close the file.
    
    The above custom configuration directives enable SonarQube to access the PostgreSQL database, and listen for connections on the TCP port `9000` from all network addresses `0.0.0.0`.
    
3. Open the `sysctl.config` configuration file to modify the system memory limits.
    
    ```plaintext
    $ sudo nano /etc/sysctl.conf
    ```
    
4. Add the following directives at the end of the file.
    
    ```plaintext
    vm.max_map_count=524288
    fs.file-max=131072
    ```
    
    Save and close the file.
    
    Within the above configuration:
    
    * `vm.max_map_count=524288`: Increases the number of memory maps Elasticsearch can use, allowing it to handle large datasets.
        
    * `fs.file-max=131072`: Increases the maximum number of files Elasticsearch can open, allowing it to run efficiently.
        
    
    SonarQube uses Elasticsearch to store indices in a memory-mapped file system. Adjusting the system limits for virtual memory mapping and file handling ensures better stability and performance for SonarQube.
    
5. Create a new `/etc/security/limits.d/99-sonarqube.conf` file to create a resource limits configuration for SonarQube.
    
    ```plaintext
    $ sudo nano /etc/security/limits.d/99-sonarqube.conf
    ```
    
6. Add the following directives to increase the file descriptor and process limits for SonarQube.
    
    ```plaintext
    sonarqube   -   nofile   131072
    sonarqube   -   nproc    8192
    ```
    
    Save and close the file.
    
    Within the configuration:
    
    * `nofile=131072`: Increases the number of open file descriptors, allowing SonarQube to handle large workloads.
        
    * `nproc=8192`: Raises the process limit to prevent failures under high concurrency.
        
7. Allow network connections to the SonarQube port `9000`.
    
    ```plaintext
    $ sudo ufw allow 9000/tcp
    ```
    
    * Run the following command to install UFW and allow SSH connections if it's unavailable.
        
    
    ```plaintext
    $ sudo apt install ufw -y && sudo ufw allow 22/tcp
    ```
    
8. Reload UFW to apply the firewall configurations.
    
    ```plaintext
    $ sudo ufw reload
    ```
    
9. View the UFW status and verify that below are the only active firewall rules.
    
    ```plaintext
    $ sudo ufw status
    ```
    
    Your output should be similar to the one below:
    
    ```plaintext
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22/tcp                     ALLOW       Anywhere
    9000/tcp                   ALLOW       Anywhere
    22/tcp (v6)                ALLOW       Anywhere (v6)
    9000/tcp (v6)              ALLOW       Anywhere (v6)
    ```
    

### **Set Up SonarQube as a System Service**

Follow the steps below to set up a new system service for SonarQube to manage the application processes on your server.

1. Create a new `sonarqube.service` file.
    
    ```plaintext
    $ sudo nano /etc/systemd/system/sonarqube.service
    ```
    
2. Add the following configurations to the file.
    
    ```plaintext
    [Unit]
    Description=SonarQube service
    After=syslog.target network.target
    
    [Service]
    Type=forking
    
    ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
    ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop
    
    User=sonarqube
    Group=sonarqube
    PermissionsStartOnly=true
    Restart=always
    
    StandardOutput=syslog
    LimitNOFILE=131072
    LimitNPROC=8192
    TimeoutStartSec=5
    SuccessExitStatus=143
    
    [Install]
    WantedBy=multi-user.target
    ```
    
    Save and close the file.
    
    The above configuration creates a new SonarQube system service to monitor and manage the application processes.
    
3. Reload systemd to apply the service changes.
    
    ```plaintext
    $ sudo systemctl daemon-reload
    ```
    
4. Enable SonarQube to start at boot.
    
    ```plaintext
    $ sudo systemctl enable sonarqube
    ```
    
5. Start the SonarQube service.
    
    ```plaintext
    $ sudo systemctl start sonarqube
    ```
    
6. View the SonarQube service status and verify that it's running.
    
    ```plaintext
    $ sudo systemctl status sonarqube
    ```
    
    Your output should be similar to the one below:
    
    ```plaintext
    ● sonarqube.service - SonarQube service
         Loaded: loaded (/etc/systemd/system/sonarqube.service; enabled; preset: enabled)
         Active: active (running) since Thu 2024-12-26 14:12:47 WAT; 2h 54min ago
        Process: 1085 ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start (code=exited, status=0/SUCCESS)
       Main PID: 1108 (java)
    ```
    
7. Restart the server to apply the SonarQube installation changes.
    
    ```plaintext
    $ sudo reboot now
    ```
    

## **Access SonarQube**

SonarQube includes a graphical web-based interface for managing code quality, projects, issues, and security. Follow the steps below to access the SonarQube web interface, update the default administrator password and create a dedicated user for code scanning.

1. Access the SonarQube port `9000` using your server IP or domain name.
    
2. Log in to SonarQube with the following credentials when prompted.
    
    * **Username:** `admin`
        
    * **Password:** `admin`
        
    
    ![Sonar-Qube-login.png](https://i.postimg.cc/sD1Mvf6C/Sonar-Qube-login.png align="left")
    
    * Change the default administrator password when prompted.
        
3. Click **Administration** within the SonarQube interface, select **Security** from the list of options, and click the **Users** dropdown option.
    
    ![create-user.png](https://sjc1.vultrobjects.com/docs-main-doc-assets-1/2102/3411381a-e6b6-48b4-b748-e75a77571cf5.png align="left")
    
4. Click **Create User** to add a new user for code scanning.
    
    ![sonar-user.png](https://sjc1.vultrobjects.com/docs-main-doc-assets-1/2102/9d6c9ddc-adf0-4da4-89f6-514576afd75a.png align="left")
    
5. Click the options symbol in the **Tokens** column within the new user's row to generate a token.
    
6. Enter the token name, select its expiry period, and click **Generate**.
    
    ![sonar-user-token.png](https://sjc1.vultrobjects.com/docs-main-doc-assets-1/2102/4badefcd-c24a-4ffe-9e72-e9c910c0adb0.png align="left")
    
7. Copy the generated token in your output to use it with code scanning.
    

## **Scan SonarQube Example Projects**

Follow the steps below to test the default SonarQube scanner using an example project.

1. Switch to your user's home directory.
    
    ```plaintext
    $ cd
    ```
    
2. Create a new sample `sonar-example-test` project directory.
    
    ```plaintext
    $ mkdir sonar-example-test
    ```
    
3. Switch to the `sonar-example-test` directory.
    
    ```plaintext
    $ cd sonar-example-test
    ```
    
4. Download the SonarQube example project archive.
    
    ```plaintext
    $ wget https://github.com/SonarSource/sonar-scanning-examples/archive/master.zip
    ```
    
5. Extract files from the downloaded archive.
    
    ```plaintext
    $ unzip master.zip
    ```
    
6. Switch to the examples directory.
    
    ```plaintext
    $ cd sonar-scanning-examples-master
    ```
    
7. Switch to the example `sonar-scanner` directory.
    
    ```plaintext
    $ cd sonar-scanner
    ```
    
8. Scan the code in the entire directory using SonarScanner. Replace `user-sonar_token` with the user token you generated earlier.
    
    ```plaintext
    $ sonar-scanner -D sonar.token=user-sonar_token
    ```
    
    Your output should be similar to the one below:
    
    ```plaintext
    INFO  Analysis total time: 22.116 s
    INFO  SonarScanner Engine completed successfully
    INFO  EXECUTION SUCCESS
    INFO  Total time: 26.095s
    ```
    
9. Visit the SonarQube dashboard to view the scan results and the entire project report.
    
    ![scan-result.png](https://sjc1.vultrobjects.com/docs-main-doc-assets-1/2102/13f907c1-edf1-4c51-ba3a-4a2f4326e0a0.png align="left")
    

### **Scan Multiple Projects**

Follow the steps below to set up your custom code projects to scan using SonarQube on your workstation.

1. Navigate to your existing project's root directory. For example, `myproject`.
    
    ```plaintext
    $ cd myproject
    ```
    
2. Create a new `sonar-project.properties` configuration.
    
    ```plaintext
    $ nano sonar-project.properties
    ```
    
3. Add the following configurations to the file to define your project settings. Replace the example values with your actual project values.
    
    ```plaintext
    # Unique identifier for the project
    sonar.projectKey=MyProject:Key1   
    
    # Display name in SonarQube UI  
    sonar.projectName=First Project  
    
    # Version number being analyzed
    sonar.projectVersion=1.0      
    
    # Brief description of the project
    sonar.projectDescription=My First Project   
    
    # Code directory to analyze
    sonar.sources=src
    ```
    
    Save and close the file.
    
    The above project configuration specifies your project settings and a target directory with the code to scan.
    
4. Run the SonarScanner CLI to scan the code in your project and access its report in the SonarQube web dashboard.
    
    ```plaintext
    $ sonar-scanner -D sonar.token=<sonar_token>
    ```