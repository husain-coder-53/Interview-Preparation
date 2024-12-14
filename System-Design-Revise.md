# Revise System Design

# Determining Resources for Vertical Scaling

## 1. Identify Bottlenecks
- **CPU-bound**:
  - **Symptom**: High CPU utilization (>75%) during peak loads.
  - **Solution**: Upgrade to a machine with more CPU cores or higher clock speed.
- **Memory-bound**:
  - **Symptom**: Memory usage consistently exceeds available memory, causing swapping or out-of-memory errors.
  - **Solution**: Increase RAM to handle larger data sets or more concurrent processes.
- **Disk I/O-bound**:
  - **Symptom**: Slow read/write speeds, high disk queue length, or excessive storage usage.
  - **Solution**: Use SSDs instead of HDDs or increase storage capacity.

---

## 2. Monitor Application Performance
- Use tools like:
  - **Linux**: `top`, `htop`, `iostat`, `vmstat`.
  - **Cloud**: AWS CloudWatch, Azure Monitor.
  - **APM Tools**: Datadog, New Relic, or Dynatrace.
- Focus on:
  - Request latency.
  - Throughput.
  - Resource usage during peak and average loads.

---

## 3. Test Resource Limits
- Simulate load using tools like:
  - Apache JMeter, Locust, or k6.
- Identify the specific resource (CPU, memory, disk, or network) that fails first under load.

---

## 4. Match Resource Allocation to Workload
- **Web servers**: Benefit from more CPU cores for handling concurrent requests.
- **Databases**: Require more memory for caching or faster disks for write-heavy workloads.
- **Video encoding**: Needs high CPU/GPU power for processing.

---

## 5. Consider Application Type
- **Compute-intensive**: Focus on CPU cores and speed (e.g., ML models, video processing).
- **Memory-intensive**: Add RAM for in-memory caching or large datasets (e.g., Redis, databases).
- **Storage-intensive**: Upgrade to SSDs or distributed storage (e.g., Elasticsearch).

---

## 6. Plan for Growth
- Choose resources that handle peak loads with a buffer for future growth (e.g., 20–30% extra capacity).
- Use auto-scaling tools (e.g., AWS EC2 instance resizing) to simplify upgrades.


# Fullstack and DevOps Frameworks/Apps/Libraries/Platforms

## 1. Fullstack Frameworks
### **1.1. Node.js**
- **Type**: Backend runtime for JavaScript.
- **Resource Intensity**:
  - **Compute**: Medium (async operations are CPU efficient).
  - **Memory**: Moderate (depends on the number of connections and libraries used).
  - **Storage**: Low (stateless by design, uses databases for storage).
- **Ideal Machine**: Multi-core CPU with 2-4GB RAM for small apps, scale up for enterprise.
- **Use Cases**: APIs, microservices, real-time applications.

### **1.2. Next.js**
- **Type**: React-based fullstack framework (SSR, SSG).
- **Resource Intensity**:
  - **Compute**: Medium to high (SSR is CPU-intensive).
  - **Memory**: Medium (stateful rendering requires caching).
  - **Storage**: Low (static assets offloaded to CDNs).
- **Ideal Machine**: At least 4-core CPU, 8GB RAM for development, scale horizontally for production.
- **Use Cases**: SEO-friendly web apps, e-commerce sites.

### **1.3. Django**
- **Type**: Python-based backend framework.
- **Resource Intensity**:
  - **Compute**: Medium (higher for complex queries).
  - **Memory**: Medium (depends on caching strategies).
  - **Storage**: Low (uses databases for persistent storage).
- **Ideal Machine**: 4-core CPU, 4-8GB RAM.
- **Use Cases**: Content-heavy web apps, APIs.

## 1.4. Go (Golang)
- **Type**: Programming language for backend, networking, and cloud-native applications.
- **Resource Intensity**:
  - **Compute**: Medium (highly optimized runtime).
  - **Memory**: Low to medium (efficient garbage collection and lightweight goroutines).
  - **Storage**: Low (binaries are statically compiled and small).
- **Ideal Machine**: Multi-core CPU, 2-4GB RAM for small apps, scales horizontally for large systems.
- **Use Cases**:
  - Web APIs (e.g., using frameworks like Gin or Echo).
  - Cloud-native apps (e.g., Kubernetes components are written in Go).
  - Networking and real-time systems (e.g., high-performance proxies like Traefik).
- **Advantages**:
  - Built-in concurrency with goroutines for handling parallel tasks efficiently.
  - Single binary output for easy deployment.
- **Scaling**:
  - Horizontal scaling with load balancers.
  - Leverage lightweight goroutines for high concurrency.

---

## 1.5. PHP
- **Type**: Server-side scripting language for web development.
- **Resource Intensity**:
  - **Compute**: Medium (CPU load increases with complex logic).
  - **Memory**: Low to medium (depends on frameworks like Laravel or WordPress plugins).
  - **Storage**: Medium (file-based caching, logs, uploaded files).
- **Ideal Machine**: 4-core CPU, 4-8GB RAM for small to medium websites, scale up for high-traffic sites.
- **Use Cases**:
  - Content management systems (e.g., WordPress, Drupal).
  - Web frameworks (e.g., Laravel, Symfony).
  - E-commerce platforms (e.g., Magento).
- **Advantages**:
  - Easy to learn and deploy, large community support.
  - Integration with Apache or Nginx for serving web applications.
- **Scaling**:
  - Vertical scaling for small apps (increase CPU/RAM).
  - Horizontal scaling using PHP-FPM with load balancers for large-scale apps.
  - Offload static assets to CDNs.

---
# Comparison Table: Go vs PHP vs Node.js

| Feature              | **Go**                             | **PHP**                            | **Node.js**                          |
|----------------------|-------------------------------------|-------------------------------------|---------------------------------------|
| **Type**             | Compiled, statically typed language | Server-side scripting language      | Runtime for JavaScript (event-driven) |
| **Performance**      | High (optimized for concurrency)    | Moderate (varies with workload)     | High (non-blocking I/O, async)        |
| **Concurrency**      | Lightweight goroutines for parallelism | Limited concurrency, synchronous by default | Event loop, async with Promises       |
| **Memory Usage**     | Low to medium                      | Low to medium                      | Medium (depends on libraries used)    |
| **Compute Intensity**| High (efficient runtime)            | Medium (relies on frameworks/plugins) | Medium (optimized for async tasks)    |
| **Ease of Deployment** | Easy (single binary)              | Easy (integrates with Apache/Nginx) | Easy (npm and modular architecture)   |
| **Ecosystem**        | Moderate (growing cloud tools)      | Extensive (CMS, e-commerce tools)  | Extensive (npm, largest library registry) |
| **Use Cases**        | High-performance APIs, real-time systems | CMS, e-commerce, content-heavy sites | APIs, SPAs, real-time apps, microservices |
| **Community Support**| Moderate                           | Extensive                          | Extensive                             |
| **Scalability**      | Horizontal scaling with goroutines  | Vertical for small apps, horizontal for high traffic | Horizontal scaling with clustering/load balancers |
| **Development Speed**| Moderate (requires setup and knowledge) | Fast (beginner-friendly)           | Fast (JavaScript knowledge suffices)  |
| **Frameworks**       | Gin, Echo, Fiber                   | Laravel, Symfony, CodeIgniter      | Express, Koa, NestJS                  |
| **Learning Curve**   | Steep (statically typed, requires setup) | Easy (ideal for beginners)         | Easy to moderate (JavaScript familiarity) |
| **Best Fit**         | Microservices, networking tools     | Content-heavy websites, CMS        | Real-time apps, APIs, fullstack projects |



---

## 2. DevOps Platforms
### **2.1. Docker**
- **Type**: Containerization platform.
- **Resource Intensity**:
  - **Compute**: Low to high (depends on the workload inside containers).
  - **Memory**: Medium (containers run isolated processes).
  - **Storage**: Medium to high (images and volumes consume disk space).
- **Ideal Machine**: Multi-core CPU, 8-16GB RAM, SSD for faster image I/O.
- **Use Cases**: CI/CD pipelines, microservices deployment.

### **2.2. Kubernetes**
- **Type**: Container orchestration platform.
- **Resource Intensity**:
  - **Compute**: High (manages clusters and resource allocation).
  - **Memory**: High (requires significant overhead for cluster management).
  - **Storage**: Medium (persistent storage for workloads).
- **Ideal Machine**: Multi-node cluster with 16+GB RAM and multiple CPUs.
- **Use Cases**: Large-scale container orchestration.

### **2.3. Jenkins**
- **Type**: CI/CD automation server.
- **Resource Intensity**:
  - **Compute**: Medium (builds and deployments use CPU heavily).
  - **Memory**: Medium (parallel pipelines consume memory).
  - **Storage**: Medium (build artifacts and logs).
- **Ideal Machine**: 4-core CPU, 8GB RAM, SSD.
- **Use Cases**: Build automation, deployment pipelines.

---

## 3. Libraries
### **3.1. Redis**
- **Type**: In-memory data store.
- **Resource Intensity**:
  - **Compute**: Low (lightweight).
  - **Memory**: High (stores data entirely in memory).
  - **Storage**: Optional (for snapshots and persistence).
- **Ideal Machine**: High-memory instance (16+GB RAM for production).
- **Use Cases**: Caching, session storage.

### **3.2. Nginx**
- **Type**: Web server/load balancer.
- **Resource Intensity**:
  - **Compute**: Low to medium (scales with request load).
  - **Memory**: Low (lightweight worker processes).
  - **Storage**: Low (logs and configuration files).
- **Ideal Machine**: 2-core CPU, 2GB RAM.
- **Use Cases**: Reverse proxy, static file serving.

---

## 4. Cloud Platforms
### **4.1. AWS (EC2, S3, Lambda)**
- **Type**: Cloud compute and storage services.
- **Resource Intensity**:
  - **Compute**: Varies by workload.
  - **Memory**: Configurable per instance.
  - **Storage**: High (for S3, data lakes, etc.).
- **Ideal Machine**: Configurable; choose instances based on workload (e.g., `t3.medium` for light workloads, `m5.large` for medium apps).
- **Use Cases**: Scalable web apps, serverless architectures.

### **4.2. Google Cloud (GKE, Cloud Functions)**
- **Type**: Cloud compute and container orchestration.
- **Resource Intensity**:
  - **Compute**: Varies by workload.
  - **Memory**: Configurable per instance.
  - **Storage**: High (object storage, persistent disks).
- **Ideal Machine**: Tailored to workload; use preemptible VMs for cost efficiency.
- **Use Cases**: Big data, ML pipelines, containerized apps.

---

## Decision-Making Notes
1. **Compute-Intensive**:
   - Ideal for applications with heavy processing tasks (e.g., video encoding, ML models).
   - Prioritize multi-core CPUs and GPUs.

2. **Memory-Intensive**:
   - Choose for in-memory databases, caching, or applications requiring large stateful storage.
   - Prioritize high-RAM instances (e.g., Redis, in-memory ML pipelines).

3. **Storage-Intensive**:
   - Needed for databases, file storage systems, and analytics platforms.
   - Prioritize SSDs for faster I/O.

4. **Scalability**:
   - Opt for containerized apps with Docker and Kubernetes for flexibility.
   - Use cloud platforms (AWS, GCP) for easy scaling and failover.


