# 🎡 Shared Infrastructure (Kafka)

This repository contains the central messaging infrastructure for the **Food Delivery System**. It provides the **Apache Kafka** broker and **Kafka-UI** for real-time monitoring of events between microservices.

Using **Kafka KRaft mode** (No Zookeeper required).

---

## 🌐 Microservices Ecosystem

This service is part of a larger **Food Delivery System**. You can explore the other components of the architecture below:

| Service | Responsibility | Repository |
| :--- | :--- | :--- |
| **🍴 Restaurant Service** | Manages restaurant profiles, menus, and slots. | [View Repo](https://github.com/nelsonalmeida2/restaurant-service) |
| **📅 Reservation Service** | Handles table bookings and real-time availability. | [View Repo](https://github.com/nelsonalmeida2/reservation-service) |
| **💳 Payment Service** | Processes transactions and manages payment states. | [View Repo](https://github.com/nelsonalmeida2/payment-service) |
| **🔔 Notification Service** | Dispatches Email/SMS notifications via Kafka events. | [View Repo](https://github.com/nelsonalmeida2/notification-service) |
| **🎡 Shared Infra** | Central Kafka broker and infrastructure setup. | [View Repo](https://github.com/nelsonalmeida2/food-delivery-infra) |

---

## 🛠️ Components

- **Apache Kafka**: The event streaming platform.
- **Kafka-UI**: A web interface to manage topics, messages, and consumer groups.
- **Docker Network**: All services must connect to the shared `store-network`.

---

## 🚀 Setup & Execution

### 1. Create the External Network

This is a mandatory step. All microservices (Notification, Restaurant, etc.) depend on this shared network to communicate.

```bash
docker network create store-network
```

### 2. Start Infrastructure

Run the following command to start the Kafka broker and the management UI:

```bash
docker compose up -d
```

### 📦 Services & Access

| Service | URL / Access | Description |
|---------|--------------|------------|
| Kafka Broker | kafka:9092 | Internal address for microservices |
| Kafka UI | http://localhost:8090 | Web dashboard to monitor events |

### How to use Kafka-UI

Access [http://localhost:8090](http://localhost:8090). You can view all created topics (e.g., `reservation-created-events-topic`) and inspect live messages being exchanged between your services.

### ⚙️ Configuration Details

- Port 9092: Main listener for internal traffic.
- Auto-Topic Creation: Enabled (`true`) for easier development.
- Cluster ID: Fixed as `5L6g3nShT-eMCtK--X86sw`.

---

👤 **Author:** Nelson Almeida  
🌐 **Website:** [nelsonalmeida.pt](https://nelsonalmeida.pt)  
🐙 **GitHub:** [nelsonalmeida2](https://github.com/nelsonalmeida2)

> Note: Start this infrastructure before launching the microservices to avoid connection errors during service startup.

