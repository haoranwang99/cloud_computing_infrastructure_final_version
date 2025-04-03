
# ☁️ Cloud Computing Mini Infrastructure

This project simulates a lightweight cloud computing infrastructure with features like load balancing, resource elasticity, user simulation, and a visual dashboard. It’s built in Python and designed for educational and experimental use in cloud architecture and distributed systems.

---

## 🧱 Architecture Overview

The system consists of **three core components**:

1. **End Users** – Simulated users sending jobs to the system
2. **Cloud Manager** – Manages resource allocation, monitoring, and load balancing
3. **Proxies (Pods)** – Virtual machines grouped by workload types (light, medium, heavy)

A live **dashboard** (HTML/Flask) monitors the active status of each VM node across pods.

---

## 📦 Project Structure

```
cloud_infrastructure_project/
├── cloud_user.py              # Simulates a single user submitting jobs
├── auto_user.py               # Auto-generates user requests over time

├── resource_manager.py        # Manages VM pool, spawns/kills proxies
├── load_balancer.py           # Routes requests to appropriate proxy pods
├── elastic_monitor.py         # Scales pods based on load
├── haproxy.cfg                # HAProxy configuration file (for load balancing)

├── light_proxy.py             # VM node for handling light tasks
├── medium_proxy.py            # VM node for medium tasks
├── heavy_proxy.py            # VM node for heavy tasks

├── index.html                 # Dashboard UI to monitor all VM nodes
```

---

## 🚦 System Flow

1. **`cloud_user.py` / `auto_user.py`**: Emulates end users generating job requests.
2. **`load_balancer.py`**: Receives jobs and forwards them to the best-fit pod (light/medium/heavy).
3. **`resource_manager.py`**: Creates or removes VM nodes (proxies) as needed.
4. **`elastic_monitor.py`**: Monitors node load and activates auto-scaling.
5. **`*_proxy.py`**: Executes the actual task and returns the result.
6. **`index.html`**: Visual dashboard showing current status of VMs and pods.

---

## 🛠 Technologies Used

- **Python** – Core logic for user simulation, proxies, management
- **Flask / Jinja2** – For rendering the dashboard
- **HAProxy** – Load balancing
- **HTML/CSS** – Dashboard frontend
- **Linux / Subprocess / OS** – Process management and shell execution
- **Threading / Queues** – Asynchronous task handling

---

## 🚀 How to Run the Project

> Run each component in separate terminals or use a process manager like `tmux` or `screen`.

### 1. Start the core components

```bash
python3 load_balancer.py
python3 resource_manager.py
python3 elastic_monitor.py
```

### 2. Start proxies (you can scale manually or via monitor)

```bash
python3 light_proxy.py
python3 medium_proxy.py
python3 heavy_proxy.py
```

### 3. Run user simulation

```bash
python3 cloud_user.py
# or
python3 auto_user.py
```

### 4. Launch the dashboard

Serve `index.html` via a Flask app or open it if statically rendered:
```bash
http://localhost:5000
```

---

## 📊 Dashboard

The dashboard (`index.html`) shows:

- Live pod statuses (Light, Medium, Heavy)
- Number of active VMs
- VM status (Online or New)
- Link to job/request monitor

---

## 🎯 Features

- ✅ Load balancing by request type
- ✅ Auto-scaling of VM nodes
- ✅ Dashboard for real-time status
- ✅ Lightweight and modular codebase
- ✅ End-to-end cloud-like simulation

---

## 🧠 Learning Objectives

- Understand cloud resource provisioning and elasticity
- Build load-balancing logic
- Explore user/job simulation at scale
- Practice managing distributed services with Python

---

## 👤 Author

Created by **Haoran Wang**  
GitHub: [@haoranwang99](https://github.com/haoranwang99)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
