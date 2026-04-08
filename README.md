# 🚀 Jenkins Master-Agent CI Pipeline (Distributed Build Architecture)

---

## 📌 Project Overview

This project demonstrates a **Jenkins Master–Agent (Slave) architecture** for executing CI pipelines in a distributed environment.

It showcases how Jenkins offloads build workloads from the master node to agent nodes, improving scalability, performance, and reliability — similar to real-world production CI/CD systems.

---

## 🏗️ Architecture Diagram

```
                +----------------------+
                |    Jenkins Master    |
                |  (Controller Node)   |
                +----------+-----------+
                           |
                           |  (SSH / JNLP Connection)
                           v
                +----------------------+
                |   Jenkins Agent      |
                |      (node-1)        |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |   Build Execution    |
                |  (Pipeline Stages)   |
                +----------------------+
```

---

## ⚙️ Tech Stack

* Jenkins (v2.541.3)
* AWS EC2 (Ubuntu)
* Linux (amd64)
* Jenkins Agent (node-1)
* Groovy (Pipeline scripting)

---

## 🚀 Implementation Steps

---

### 🔹 1. Setup Jenkins Master

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
sudo apt install jenkins -y
```

Access Jenkins:

```
http://<EC2-IP>:8080
```

---

### 🔹 2. Configure Jenkins Agent (node-1)

* Created a new node: `node-1`
* Configured as **permanent agent**
* Connected using SSH/JNLP
* Verified status: ✅ **Online**

---

### 🔹 3. Node Verification

* Built-in node (master)
* External agent node (`node-1`)
* Resource monitoring available (CPU, Disk, Response Time)

---

### 🔹 4. Create Pipeline Job

Example pipeline:

```groovy
pipeline {
    agent { label 'node-1' }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```

---

### 🔹 5. Pipeline Execution

* Job triggered successfully
* Executed on agent (`node-1`)
* Output verified via console logs
* Stage visualization completed

---

## 📸 Screenshots

### 🔹 Jenkins Dashboard

![Dashboard](screenshots/jenkins-dashboard.png)

### 🔹 Jenkins Agent (node-1)

![Agent](screenshots/jenkins-node.png)

### 🔹 Pipeline Execution

![Pipeline](screenshots/jenkins-pipeline.png)

### 🔹 Console Output

![Console](screenshots/jenkins-console.png)

### 🔹 Nodes Overview

![Nodes](screenshots/jenkins-nodes.png)

---

## 🔥 Key Features

* Distributed Build Architecture
* Jenkins Master–Agent Setup
* Agent-based Pipeline Execution
* Pipeline Stage Visualization
* Real-time Console Logs
* Scalable CI Infrastructure

---

## ⚠️ Challenges Faced

* Agent connection issues (SSH/JNLP)
* Node configuration troubleshooting
* Pipeline execution on specific node
* Resource allocation on agent

---

## 📈 Future Enhancements

* Add Docker build stage
* Integrate GitHub Webhooks
* Add parallel pipeline execution
* Integrate with Kubernetes (Jenkins agents as pods)
* Add CI/CD integration with ArgoCD

---

## 👨‍💻 Author

**Rushikesh Sutar**
DevOps Engineer | CI/CD | Kubernetes | Cloud

---

## ⭐ Support

If you found this project useful, give it a ⭐ on GitHub!
