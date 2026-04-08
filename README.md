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

<img width="1920" height="1080" alt="Screenshot 2026-04-08 113924" src="https://github.com/user-attachments/assets/cdddc465-e4e4-4dc1-bdc0-78509540a1ce" />


### 🔹 Jenkins Agent (node-1)

<img width="1920" height="1080" alt="Screenshot 2026-04-08 114033" src="https://github.com/user-attachments/assets/7b35e6b5-93b2-44eb-af2b-365f1201b1dd" />


### 🔹 Pipeline Execution

<img width="1920" height="1080" alt="Screenshot 2026-04-08 114001" src="https://github.com/user-attachments/assets/e1512ff0-a0c2-44c6-82e1-503ff884e6c2" />


### 🔹 Console Output

<img width="1920" height="1080" alt="Screenshot 2026-04-08 114015" src="https://github.com/user-attachments/assets/40dbd3cd-db23-4c77-a091-5e99a11f6294" />


### 🔹 Nodes Overview

<img width="1920" height="1080" alt="Screenshot 2026-04-08 113941" src="https://github.com/user-attachments/assets/af65175b-1f57-496e-8ffb-ca0b62de2cb3" />


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
