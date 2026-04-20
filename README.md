# SDN Static Routing using Ryu Controller

**Name:** Hansika R
**SRN:** PES2UG24CS178

---

##  Problem Statement

This project demonstrates the implementation of static routing using a Software Defined Networking (SDN) controller. Using Mininet and the Ryu controller, routing paths are manually defined and enforced using flow rules. The system showcases controlled packet forwarding and selective path usage.

---

## Objective

* Implement static routing using controller-installed flow rules
* Define routing paths manually
* Validate packet delivery
* Demonstrate controlled network behavior using SDN

---

##  Network Topology

The network consists of:

* 3 Switches: s1, s2, s3
* 3 Hosts: h1, h2, h3

Allowed Path:
h1 → s1 → s3 → h3

Blocked Path:
h1 → s1 → s2 → h2

---

##  Tools & Technologies

* Mininet
* Ryu Controller
* OpenFlow
* iperf

---

##  Setup & Execution

### Step 1: Start Ryu Controller

```
ryu-manager static_routing.py
```

### Step 2: Run Mininet Topology

```
sudo python3 topo.py
```

### Step 3: Test Connectivity

#### Allowed Communication

```
h1 ping h3
```

#### Blocked Communication

```
h1 ping h2
```

---

##  Expected Output

* h1 → h3 → 0% packet loss (Successful)
* h1 → h2 → 100% packet loss (Blocked)

---

##  Test Scenarios

### Scenario 1: Allowed Traffic

h1 ping h3 → Successful communication

### Scenario 2: Blocked Traffic

h1 ping h2 → Communication blocked

---

##  Performance Analysis

### Latency

* Average latency ≈ 3 ms

### Throughput (iperf)

* Bandwidth ≈ 30 Gbps
* High-speed and stable transmission
* No packet loss observed

---

##  Flow Table Rules

### Switch s1

* in_port=1 → output=3
* in_port=3 → output=1

### Switch s3

* in_port=1 → output=2
* in_port=2 → output=1

---

##  Observations

* Static routing successfully implemented
* Controller enforces specific paths
* Blocking achieved by not installing rules

---

##  Limitations

* Static routing is not adaptive
* Requires manual configuration
* Limited scalability

---

##  Conclusion

This project demonstrates how SDN can be used to implement static routing and control network traffic. The controller effectively manages packet forwarding, allowing selective communication and blocking unwanted paths.

---

##  Proof of Execution

(Add screenshots here in your GitHub repo)

* Ping success (h1 → h3)
  ![ping_success](https://github.com/user-attachments/assets/ac745683-ce90-441b-83d4-95d7be9653a2)
  
* Ping failure (h1 → h2)
  ![ping_failure](https://github.com/user-attachments/assets/08c65a87-085e-46f7-add7-cf1457e002c1)
  
* Latency
  The latency measured using ping shows minimal delay, indicating efficient packet forwarding.
  
  ![latency](https://github.com/user-attachments/assets/f7dc6b25-9b85-426a-b10a-5e38ef7cec2f)
  Latency (avg): 3.175 ms
  942 Mbits/sec

* iperf results
  Throughput measured using iperf confirms successful data transfer between hosts. Flow table inspection shows that packets follow the intended path via switch s3, while no rules are installed on s2, effectively blocking that path.
  ![THROOUGHPUT](https://github.com/user-attachments/assets/4ebccc16-8c8b-4303-8a59-e9c94225aecd)
  Transfer: 35.3 GBytes  
  Bandwidth: 30.3 Gbits/sec
  
  Bandwidth:
    •	Data is transferred at very high speed 
    •	Network path (h1 → s1 → s3 → h3) is efficient
  
  Transfer Size:
    •	Continuous, stable transmission 
    •	No packet drops or interruptions 

  
* Flow table output
  ![flow_table](https://github.com/user-attachments/assets/c6947d3a-ecc2-4945-a32a-52124e1c60b3)
  
---

## References

* Ryu Documentation
* Mininet Documentation
* OpenFlow Specification

---
