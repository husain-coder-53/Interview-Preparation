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

