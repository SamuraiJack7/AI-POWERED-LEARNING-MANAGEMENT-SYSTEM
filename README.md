# AI-Powered Learning Management System (LMS)

A distributed, AI-driven Learning Management System implementing:

- Raft-based consensus for reliability and consistency  
- gRPC-based microservice communication  
- COHERE-powered tutoring services  
- Role-based operations for students and instructors  
- Both CLI and GUI (Tkinter) clients for user interaction  

---

## 1. Important Note (IP Configuration)

**Before running any node, you must update the IP addresses in the code to match your deployment environment.**

- Ensure that:
  - Leader and follower LMS servers point to the correct host/IP and ports
  - Tutoring server address is correctly referenced by the LMS services and clients
- If you only change IP addresses and not the `.proto` definitions:
  - **You do not need to regenerate the gRPC `.proto` files.**

---

## 2. Overview

This project implements an **AI-powered Learning Management System (LMS)** that combines:

- **Distributed Consensus:** Raft algorithm for leader election and replicated logs  
- **Tutoring Services:** Integration with a COHERE-based language model backend  
- **Role-Based Access:** Dedicated workflows for students and instructors  
- **Multi-Interface Access:** Command-line client and Tkinter-based GUI  

The system is built in Python using `grpcio` for RPC communication and integrates with COHERE for intelligent tutoring responses.

---

## 3. Features

### 3.1 Distributed Consensus (Raft)

- Leader election among LMS nodes  
- Log replication across follower nodes  
- Consistent state across the cluster for critical LMS operations  
- Support for multiple LMS nodes:
  - 1 Leader Node
  - Multiple Follower Nodes

### 3.2 AI Tutoring Services

- A dedicated **Tutoring Server** integrated with **COHERE**  
- Handles student queries and provides AI-generated responses  
- Accessible from both CLI and GUI clients

### 3.3 Role-Based User Operations

**Students can:**

- Register and log in
- Submit assignments
- View grades
- Post queries to instructors
- Ask AI-powered tutoring questions

**Instructors can:**

- Register and log in
- Post assignments
- View submitted assignments
- Grade assignments
- Respond to student queries

### 3.4 User Interfaces

- **CLI Client (`lms_client.py`):**
  - Lightweight terminal-based interaction  
  - Supports all core LMS and tutoring operations  

- **GUI Client (`lms_gui.py`):**
  - Built using Tkinter  
  - Menu-based navigation for:
    - Login/registration  
    - Assignment submission and grading  
    - Query posting and viewing grades  
    - COHERE-based tutoring interactions  

### 3.5 Session Management

- Secure login/logout flows  
- Session token usage for authenticated operations  
- Distinct user sessions for students and instructors  

---

## 4. System Architecture

The system consists of the following core components:

1. **LMS Leader Server (`lms_server_leader.py`)**  
   - Acts as the Raft leader  
   - Coordinates log replication and client requests  
   - Manages core LMS operations (assignments, grades, queries)

2. **LMS Follower Servers (`lms_server_follower.py`)**  
   - Participate in the Raft consensus protocol  
   - Replicate logs from the leader  
   - Take over leadership during elections (on leader failure)

3. **Tutoring Server (`tutoring_server.py`)**  
   - COHERE-powered service  
   - Exposes gRPC endpoints for AI-based query answering  

4. **LMS Client (CLI) (`lms_client.py`)**  
   - CLI interface for students and instructors  
   - Connects to LMS leader/followers and tutoring server  

5. **LMS GUI (`lms_gui.py`)**  
   - Tkinter-based graphical interface  
   - Provides a user-friendly way to access LMS features  

> Note: IP addresses and ports for each component must be configured according to your deployment topology.

---

## 5. Prerequisites

- **Python:** 3.9+  
- Recommended: Python virtual environment (e.g., `venv` or Conda)

### 5.1 Core Python Dependencies

Install via `requirements.txt` where possible:

- `grpcio`
- `grpcio-tools`
- `transformers`
- `torch`
- `cohere`
- Other supporting libraries used by the CLI/GUI and server modules

---


