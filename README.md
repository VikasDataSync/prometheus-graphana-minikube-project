# 📊 Observability in Microservices

## 📌 Why Observability Matters
Microservices architectures are distributed, making debugging and performance tracking complex.

Observability provides insight into system behavior using:
- **Metrics** → numerical performance data  
- **Logs** → event records  
- **Traces** → request flow across services  

It helps:
- Identify bottlenecks  
- Detect failures  
- Improve reliability and performance  

---

## 🔍 Monitoring Basics

**Monitoring** is the process of collecting and visualizing system data over time.

### Key Questions:
- Is the service running?
- Is it functioning correctly?
- Is it within acceptable thresholds?

---

## ⚖️ Monitoring vs Observability

| Monitoring | Observability |
|-----------|--------------|
| Tracks predefined metrics | Explores unknown issues |
| Answers "What is happening?" | Answers "Why is it happening?" |
| Reactive | Investigative & diagnostic |

> Observability builds on monitoring — it does not replace it.

---

## 📡 Telemetry Data

- **Metrics** → Time-series numeric data (CPU, latency, request rate)  
- **Logs** → Event records  
- **Traces** → Request lifecycle across services  

---

## ⚙️ Metrics Collection Methods

### 1. Scrape (Pull Model) ✅
- Prometheus pulls metrics via `/metrics` endpoint

**Pros:**
- Centralized control  
- Loose coupling  

**Cons:**
- Requires exposed endpoints  

---

### 2. Push Model ⚠️
- Uses Pushgateway  
- Only for short-lived jobs (cron jobs, batch jobs)

**Pros:**
- Works for ephemeral services  

**Cons:**
- Not for long-running services  
- Risk of stale metrics  

---

## 📦 Exporter vs Pushgateway

### Exporter
- Exposes metrics in Prometheus format  
- Example: Node Exporter (CPU, memory)

### Pushgateway
- Temporary storage for short-lived job metrics  
- Prometheus scrapes Pushgateway  

---

## 📊 Prometheus Data Model

Each time series includes:
- Metric name  
- Labels (key-value pairs)  
- Timestamp + value  

### Example:
```promql
http_requests_total{status="200"}
http_request_duration_seconds 0.45