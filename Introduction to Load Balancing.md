```
+----------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                        Load Balancing Concept                                                                       |
+----------------------------------------------------------------------------------------------------------------------------------------------------+
|                       +----------------------+                                 +----------------------+                                              |
|     Client 1 -------->|                      |           Distributes           |                      |                                              |
|     Client 2 -------->|    Load Balancer      |------------------------------->|  Backend Server 1     |                                              |
|     Client 3 -------->|                      |                                 |                      |                                              |
|                       +----------------------+                                 +----------------------+                                              |
|                                |                                                      |                                                              |
|                                v                                                      v                                                              |
|                   +----------------------+                                 +----------------------+                                                  |
|                   |   Round Robin        |                                 |  Least Connections    |                                                  |
|                   +----------------------+                                 +----------------------+                                                  |
|                                |                                                      |                                                              |
|                                v                                                      v                                                              |
|                   +----------------------+                                 +----------------------+                                                  |
|                   |     IP Hashing        |                                 |   Server Health Check  |                                                |
|                   +----------------------+                                 +----------------------+                                                  |
|                                |                                                      |                                                              |
|                                v                                                      v                                                              |
|     +--------------------+               +--------------------+             +--------------------+               +--------------------+               |
|     | Server 1 (Active)   |               | Server 2 (Active)   |             | Server 3 (Backup)   |               | Server 4 (Backup)   |               |
|     +--------------------+               +--------------------+             +--------------------+               +--------------------+               |
|       |                            |                     |                             |                     |                             |            |
|       v                            v                     v                             v                     v                             v            |
|  Processes                    Processes             Stays Idle                        Takes Over             Stays Idle                    Takes Over   |
|  Requests                     Requests              Unless Failure                    on Failure             Unless Failure                on Failure   |
+----------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                      Why Use Load Balancing?                                                                        |
+----------------------------------------------------------------------------------------------------------------------------------------------------+
| - Ensures high availability by distributing traffic across multiple servers                                                                          |
| - Improves performance by preventing a single point of failure                                                                                       |
| - Balances the load, reducing latency and increasing responsiveness                                                                                  |
| - Provides failover capabilities with backup servers                                                                                                 |
+----------------------------------------------------------------------------------------------------------------------------------------------------+
```


### Introduction to Load Balancing**  

---

#### **Introduction to Load Balancing**  
Load balancing is a key concept in system design, helping distribute incoming requests evenly across multiple servers. The main goal is to ensure **high availability**, **reliability**, and **performance** by preventing any single server from being overwhelmed or becoming a point of failure.  

Typically, a load balancer acts as a bridge between the **client** and the **server**, accepting incoming traffic and distributing it across multiple backend servers using various algorithms. By doing so, it prevents overload on a single server, maintains **scalability**, and improves **response time**.  

---

#### **Why Do We Need Load Balancing?**  
1. **High Availability:** Ensures that the system remains available, even if one server fails.  
2. **Reliability:** Distributes traffic, so one server failure does not bring down the entire system.  
3. **Performance:** Reduces latency by balancing requests across servers.  
4. **Scalability:** Easily adds more servers to handle increasing loads.  

---

#### **Where to Place Load Balancers?**  
To fully utilize scalability and redundancy, load balancers are strategically placed at:  
1. **Between the client and the web server:** To manage incoming user traffic.  
2. **Between web servers and internal platform layers (like application or cache servers):** To balance internal processing loads.  
3. **Between internal platform layers and the database:** To ensure efficient database query handling.  

---

#### **Key Concepts and Terminology**  
- **Load Balancer:** A device or software that distributes network traffic across multiple servers.  
- **Backend Servers:** Servers that process requests forwarded by the load balancer (also known as a server pool or farm).  
- **Load Balancing Algorithm:** Determines how to allocate incoming traffic to servers (e.g., Round Robin, Least Connections).  
- **Health Checks:** Tests performed periodically to check server availability and performance.  
- **Session Persistence:** Directs repeat requests from the same client to the same server.  
- **SSL/TLS Termination:** Decrypts encrypted traffic at the load balancer, offloading server work.  

---

#### **How Does Load Balancing Work?**  
1. **Client Request:** The load balancer receives a client’s request.  
2. **Server Selection:** Uses an algorithm to decide which server to forward the request to.  
3. **Forwarding:** Sends the request to the selected server.  
4. **Response:** Receives the server response and sends it back to the client.  
5. **Health Monitoring:** Continuously checks server health and removes failing servers from the pool.  

---

#### **Fun Analogy:**  
Imagine you’re at a **busy restaurant** with multiple cashiers. You don’t want to queue up at the one overloaded counter while others are free. The **host** (load balancer) directs you to the cashier with the shortest line, ensuring everyone gets served quickly and efficiently.  

**Mnemonic to Remember:**  
**L-O-A-D**  
- **L:** **L**everage Multiple Servers  
- **O:** **O**ptimize Traffic Distribution  
- **A:** **A**ssure High Availability  
- **D:** **D**etect Failures Quickly  

---

#### **Interview Questions:**  
1. **Q:** What is the main purpose of a load balancer in system design?  
   **A:** The primary purpose of a load balancer is to evenly distribute incoming network traffic across multiple servers to ensure high availability, reliability, and performance.  

2. **Q:** Name three places where load balancers are typically positioned in a system.  
   **A:**  
   - Between the client and web servers.  
   - Between web servers and application/cache servers.  
   - Between application servers and databases.  

3. **Q:** What are some common load balancing algorithms?  
   **A:** Round Robin, Least Connections, IP Hashing, Weighted Round Robin, Least Response Time.  

---

#### **Additional Teaching:**  
Load balancing is not limited to just distributing traffic; it also involves handling **failover**, **session persistence**, and **SSL termination**. Modern systems often utilize **software-based load balancers** (like HAProxy or NGINX) for flexibility or **hardware-based solutions** for performance.  

---

Let me know if you would like to make any adjustments or move on to the next activity! 🚀

### **GitHub Notes (Activity 2): Introduction to Load Balancing**  

---

#### **Introduction to Load Balancing**  
Load balancing is a key concept in system design, helping distribute incoming requests evenly across multiple servers. The main goal is to ensure **high availability**, **reliability**, and **performance** by preventing any single server from being overwhelmed or becoming a point of failure.  

Typically, a load balancer acts as a bridge between the **client** and the **server**, accepting incoming traffic and distributing it across multiple backend servers using various algorithms. By doing so, it prevents overload on a single server, maintains **scalability**, and improves **response time**.  

---

#### **Why Do We Need Load Balancing?**  
1. **High Availability:** Ensures that the system remains available, even if one server fails.  
2. **Reliability:** Distributes traffic, so one server failure does not bring down the entire system.  
3. **Performance:** Reduces latency by balancing requests across servers.  
4. **Scalability:** Easily adds more servers to handle increasing loads.  

---

#### **Where to Place Load Balancers?**  
To fully utilize scalability and redundancy, load balancers are strategically placed at:  
1. **Between the client and the web server:** To manage incoming user traffic.  
2. **Between web servers and internal platform layers (like application or cache servers):** To balance internal processing loads.  
3. **Between internal platform layers and the database:** To ensure efficient database query handling.  

---

#### **Key Concepts and Terminology**  
- **Load Balancer:** A device or software that distributes network traffic across multiple servers.  
- **Backend Servers:** Servers that process requests forwarded by the load balancer (also known as a server pool or farm).  
- **Load Balancing Algorithm:** Determines how to allocate incoming traffic to servers (e.g., Round Robin, Least Connections).  
- **Health Checks:** Tests performed periodically to check server availability and performance.  
- **Session Persistence:** Directs repeat requests from the same client to the same server.  
- **SSL/TLS Termination:** Decrypts encrypted traffic at the load balancer, offloading server work.  

---

#### **How Does Load Balancing Work?**  
1. **Client Request:** The load balancer receives a client’s request.  
2. **Server Selection:** Uses an algorithm to decide which server to forward the request to.  
3. **Forwarding:** Sends the request to the selected server.  
4. **Response:** Receives the server response and sends it back to the client.  
5. **Health Monitoring:** Continuously checks server health and removes failing servers from the pool.  

---

#### **Fun Analogy:**  
Imagine you’re at a **busy restaurant** with multiple cashiers. You don’t want to queue up at the one overloaded counter while others are free. The **host** (load balancer) directs you to the cashier with the shortest line, ensuring everyone gets served quickly and efficiently.  

**Mnemonic to Remember:**  
**L-O-A-D**  
- **L:** **L**everage Multiple Servers  
- **O:** **O**ptimize Traffic Distribution  
- **A:** **A**ssure High Availability  
- **D:** **D**etect Failures Quickly  

---

#### **Interview Questions:**  
1. **Q:** What is the main purpose of a load balancer in system design?  
   **A:** The primary purpose of a load balancer is to evenly distribute incoming network traffic across multiple servers to ensure high availability, reliability, and performance.  

2. **Q:** Name three places where load balancers are typically positioned in a system.  
   **A:**  
   - Between the client and web servers.  
   - Between web servers and application/cache servers.  
   - Between application servers and databases.  

3. **Q:** What are some common load balancing algorithms?  
   **A:** Round Robin, Least Connections, IP Hashing, Weighted Round Robin, Least Response Time.  

---

#### **Additional Teaching:**  
Load balancing is not limited to just distributing traffic; it also involves handling **failover**, **session persistence**, and **SSL termination**. Modern systems often utilize **software-based load balancers** (like HAProxy or NGINX) for flexibility or **hardware-based solutions** for performance.  

---

