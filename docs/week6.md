
# Week 6 — Performance Evaluation & Analysis

← **[Week 5](week5.md)** | **Week 6** | **[Week 7](week7.md)** →

---

## Overview

Week 6 executes the planned performance tests and analyses system behaviour under **baseline**, **load**, and **optimised** conditions.
Using the applications selected in Week 3 and the monitoring scripts prepared in Week 5, metrics are collected consistently to identify bottlenecks, quantify improvements, and evaluate **security vs performance trade-offs**.

All testing is performed **remotely via SSH**, with all security controls enabled to reflect real-world server operation.

---

## Objectives

* Execute performance tests for all selected workload categories
* Capture CPU, memory, disk, and network metrics
* Compare baseline vs load vs optimised states
* Identify bottlenecks using quantitative evidence
* Present results using tables and visualisations

---

## Deliverables

* 📄 CSV performance datasets (`data/`)
* 📊 Graphs and charts (`docs/assets/`)
* 🧪 Testing evidence (command outputs & screenshots)
* 📈 Optimisation comparisons (before / after)
* 📝 Performance analysis with conclusions

---

## Test Environment

| Component         | Details                        |
| ----------------- | ------------------------------ |
| OS                | Ubuntu Server                  |
| Access            | SSH only                       |
| Monitoring        | `scripts/monitor-server.sh`    |
| Security Baseline | `scripts/security-baseline.sh` |
| MAC               | AppArmor (enforced)            |
| Firewall          | UFW (SSH allowlisted)          |

---

## Testing Methodology

### 1. Baseline (Idle) Capture

```bash
./scripts/monitor-server.sh user@server data/baseline.csv 10
```

* System left idle for defined period
* Establishes reference metrics

**Figure W6-1: Baseline system metrics captured during idle state**

```md
![Baseline idle metrics](docs/assets/w6-fig1-baseline.png)
```

---

### 2. CPU Performance Test

```bash
ssh user@server "stress-ng --cpu 4 --timeout 120"
```

* CPU utilisation and load average monitored
* Scheduler behaviour observed

**Figure W6-2: CPU utilisation during stress-ng execution**

```md
![CPU stress test](docs/assets/w6-fig2-cpu-load.png)
```

---

### 3. Disk I/O Performance Test

```bash
ssh user@server "fio --name=randrw --rw=randrw --bs=4k \
--size=1G --iodepth=16 --numjobs=2 --time_based --runtime=120"
```

* Disk throughput and latency measured
* Queue depth impact analysed

**Figure W6-3: Disk I/O latency and throughput under fio load**

```md
![Disk I/O test](docs/assets/w6-fig3-disk-io.png)
```

---

### 4. Network Performance Test

**Server:**

```bash
iperf3 -s
```

**Client:**

```bash
iperf3 -c <server-ip> -t 60
```

* TCP throughput and jitter measured

**Figure W6-4: iperf3 throughput test results**

```md
![Network throughput test](docs/assets/w6-fig4-network.png)
```

---

### 5. Server / Service Test (nginx)

```bash
curl -w "%{time_total}\n" -o /dev/null -s http://<server-ip>
```

* Response time measured under idle and concurrent access

**Figure W6-5: nginx response time under load**

```md
![nginx performance](docs/assets/w6-fig5-nginx.png)
```

---

## Optimisation Scenarios

Optimisations were applied incrementally and retested:

### Memory Tuning

```bash
sudo sysctl vm.swappiness=10
```

### CPU Tuning

* CPU governor adjusted (where supported)

### Web Server Tuning

* nginx worker processes & connections

### Disk Tuning

* I/O scheduler selection (where applicable)

Each optimisation was followed by a **full re-test** of the relevant workload.

---

## Data Organisation

📁 **data/**

* `baseline.csv`
* `cpu-load.csv`
* `disk-io.csv`
* `network.csv`
* `nginx-load.csv`
* `logs/`

**CSV Schema:**

```text
timestamp,test_name,metric,value,units,notes
```

---

## Results & Visualisation

Graphs were generated using collected CSV data:

* 📉 Line graphs → baseline vs load vs optimised
* 📊 Bar charts → throughput & latency
* 🧾 All figures include labels, units, and intervals

**Figure W6-6: Baseline vs load vs optimised CPU usage**

```md
![CPU comparison](docs/assets/w6-fig6-cpu-compare.png)
```

---

## Performance Analysis

### Bottleneck Identification

| Workload | Observation                              |
| -------- | ---------------------------------------- |
| CPU      | Saturation at sustained 100% utilisation |
| Disk     | Latency spikes at high queue depth       |
| Network  | Throughput capped by NIC & TCP window    |
| nginx    | Response time increased with concurrency |

---

### Optimisation Impact

| Test     | Metric       | Before | After | Improvement |
| -------- | ------------ | ------ | ----- | ----------- |
| Memory   | Swap usage   | 220 MB | 40 MB | ~82% ↓      |
| Disk I/O | Avg latency  | 18 ms  | 12 ms | ~33% ↓      |
| nginx    | Avg response | 120 ms | 85 ms | ~29% ↓      |

(All values supported by CSV data and figures.)

---

## Security vs Performance

* AppArmor overhead: **<2% CPU variance**
* fail2ban: **no measurable impact**
* Automatic updates scheduled outside test windows
* All security controls remained enabled during testing

---

## Reflection

* CPU saturation was the dominant bottleneck
* Disk tuning delivered the largest performance gains
* Optimisations were workload-specific
* Security controls provided strong protection with minimal cost

---

## Conclusion

Week 6 validates the **complete performance lifecycle**:
planning → secure configuration → execution → optimisation → analysis.

The system demonstrates that **strong security and high performance can coexist** when monitoring and tuning are applied methodically.

---

## Navigation

← **[Week 5](week5.md)** | **[Week 6](week6.md)** | **[Week 7](week7.md)** →


