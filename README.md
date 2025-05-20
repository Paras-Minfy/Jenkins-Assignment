# 🛠️ Jenkins Assignment: Create and Monitor a Basic Jenkins Pipeline

## 📋 Assignment Overview

This assignment focuses on creating a simple Jenkins pipeline and understanding core concepts such as the Jenkins UI, pipeline stages, build monitoring, and job configuration.

### 🎯 Objectives

- Set up a basic Jenkins pipeline job  
- Navigate key components of the Jenkins dashboard  
- Monitor build status, logs, and stage visualization  
- Make simple pipeline modifications  

---

## ✍️ Summary: (Describing what I have learned about Jenkins navigation)

> During this assignment, I learned how to navigate the Jenkins dashboard and its key components such as the jobs list, build queue, and executor status. I created a pipeline job and understood how different stages like Build, Test, and Deploy work in sequence. Monitoring builds using console logs and visualizing them through the Stage View helped reinforce how Jenkins handles CI pipelines. Modifying and re-running the job taught me how easy it is to iterate and improve workflows in Jenkins.

---

## ✅ Completion Status

* [x] Pipeline created and executed
* [x] Pipeline modified with a new stage
* [x] Screenshots captured
* [x] Summary written

---

## 📂 Screenshots
---
Dashboard:
* ![Dashboard Screenshot](https://github.com/Paras-Minfy/Jenkins-Assignment/blob/main/screenshots/Dashboard.png)
---
* Stage View 1:
* ![Stage View 1 Screenshot](https://github.com/Paras-Minfy/Jenkins-Assignment/blob/main/screenshots/stage%20view%201.png)
* Console Output 1:
* ![Console Output 1 Screenshot](https://github.com/Paras-Minfy/Jenkins-Assignment/blob/main/screenshots/console%20output%201.png)
---
* Stage View 2:
* ![Stage View 2 Screenshot](https://github.com/Paras-Minfy/Jenkins-Assignment/blob/main/screenshots/stage%20view%202.png)
* Console Output 2:
* ![Console Output 2 Screenshot](https://github.com/Paras-Minfy/Jenkins-Assignment/blob/main/screenshots/console%20output%202.png)
---

## 📌 Notes

* Ensure Jenkins is up and running locally or on a VM/container.
  > You can check this with: `docker ps`
  > If Jenkins is not running, you can start it with: `docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts`
* If using Docker for Jenkins, remember to mount volumes for persistence.
  > Which is this: `-v jenkins_home:/var/jenkins_home`

---

## 🧭 Assignment Details & Step-by-Step Instructions

### 1️⃣ Access Jenkins and Explore the Dashboard

- Log in to your Jenkins instance (e.g., `http://localhost:8080`)
- Familiarize yourself with:
  - Jobs list
  - Build queue
  - Build executor status
- Navigate between available views, if applicable

---

### 2️⃣ Create a Pipeline Job

- Go to the Jenkins dashboard
- Click **New Item** → Enter name: `HelloJenkins`
- Select **Pipeline** as the job type
- Scroll to the **Pipeline** section and add the following script:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'sleep 5' // Simulate build time
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'sleep 3' // Simulate test time
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh 'sleep 2' // Simulate deployment
            }
        }
    }
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
```

* Click **Save**

---

### 3️⃣ Run and Monitor the Pipeline

* Click **Build Now**
* Navigate to the build under **Build History**
* Click **Console Output** to view logs
* Observe the **Stage View** visualization of the pipeline execution

---

### 4️⃣ Modify the Pipeline

* Go to **Configure** for the `HelloJenkins` job
* Add a new stage at the end (e.g., `Cleanup`):

```groovy
stage('Cleanup') {
    steps {
        echo 'Cleaning up...'
        sh 'sleep 1'
    }
}
```

* Save and build again
* Review updated pipeline and console logs

---
