# CampusTalk: A Secure VoIP Platform using Asterisk

## 🚀 Project Overview
CampusTalk is a **secure VoIP communication platform** built using **Asterisk**, designed to enhance **internal organizational communication**. This project aims to provide a **cost-effective, feature-rich, and highly secure VoIP solution** to address the challenges associated with **traditional PBX systems**, such as high costs, limited scalability, and security vulnerabilities.

By leveraging **Asterisk’s open-source telephony framework**, CampusTalk enables **SIP-based voice communication, voicemail services, IVR, call queuing, and advanced security mechanisms**, ensuring reliable and encrypted voice transmission over the network.

---

## 🔧 Key Features
### ✅ SIP-based VoIP Calls
- Users register as **SIP clients** and communicate over a **secure network**.
- Supports **multiple SIP clients** (Zoiper5, CSipSimple, Softphone) for **cross-platform** communication.

### ✅ Multi-server Architecture
- Two **Asterisk servers deployed on Ubuntu and Kali Linux** simulate a distributed VoIP infrastructure.
- Enables **cross-network communication** between different servers while ensuring **low latency**.

### ✅ Advanced Security Mechanisms
- **TLS encryption & SRTP protocol** ensure end-to-end **secure voice transmission**.
- **MD5 hashing** is used for **secure SIP authentication**.
- **Firewall and access control rules** protect against **unauthorized access and SIP attacks**.

### ✅ Voicemail & IVR
- **Custom voicemail system** with **email notifications** for missed calls.
- **Interactive Voice Response (IVR)** for automated call handling, allowing users to navigate options.

### ✅ Call Routing & Queuing
- **Custom call forwarding** and **call transfer (blind & attended)** improve call management.
- **Call queuing system** ensures **efficient customer support handling**.
- **Time-based call restrictions** for enhanced control over call availability.

### ✅ Scalability & Optimization
- Designed for **low-latency communication** with **efficient call routing and media transmission using SIP and RTP protocols**.
- Supports **multiple concurrent connections** while maintaining **high availability**.

---

## 🖥️ Technologies Used
- **Asterisk 20.2.0** – Open-source VoIP framework
- **Ubuntu 20.2 & Kali Linux** – Server deployment
- **Zoiper5, CSipSimple, Softphone** – SIP clients for testing
- **MD5, TLS, SRTP** – Encryption & security protocols
- **Bash scripting & Asterisk configuration** – Custom call handling

---

## 📌 Installation & Setup
### 🔹 Prerequisites
1. **Linux-based operating system** (Ubuntu 20.2 or Kali Linux)
2. **Asterisk 20.2.0** installed
3. **SIP clients** (Zoiper5, CSipSimple, Softphone)
4. **Network configuration** (firewall and routing setup)

### 🔹 Step-by-Step Installation
1. **Install Asterisk**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   sudo apt install asterisk -y
   ```
2. **Configure SIP Clients**:
   - Add users to `sip.conf`:
   ```ini
   [natnael]
   type=peer
   context=phones
   allow=ulaw,alaw
   md5secret=your_md5_hashed_password
   host=dynamic
   transport=udp,tls,tcp
   ```
3. **Configure Call Routing in `extensions.conf`**:
   ```ini
   [phones]
   exten => 100,1,Dial(SIP/natnael,10,T)
   same => n,Voicemail(${EXTEN},b)
   ```
4. **Enable Security Measures**:
   ```bash
   sudo ufw allow 5060/udp
   sudo ufw allow 10000:20000/udp
   ```
5. **Start Asterisk CLI**:
   ```bash
   sudo asterisk -rvvv
   ```

---

## 📌 Code Structure & Configuration Files
### 📂 **Key Configuration Files**
- `sip.conf`: Defines SIP clients and servers.
- `extensions.conf`: Manages call routing and dialing rules.
- `voicemail.conf`: Handles voicemail services and email notifications.
- `queues.conf`: Configures call queuing for customer support.
- `features.conf`: Defines call transfer, forwarding, and security policies.

---

## 📌 Testing & Validation
### ✅ Functional Testing
- **Registration Test**: Ensured successful SIP client registration using `sip show peers`.
- **Call Test**: Verified **successful call establishment** between users.
- **Voicemail Test**: Checked **voicemail recording and email notifications**.
- **IVR Test**: Simulated **menu selection in the interactive voice response system**.

### ✅ Security Testing
- **SIP Authentication**: Tested **MD5 encryption and TLS secure connections**.
- **Penetration Testing**: Used **Kali Linux tools to assess security vulnerabilities**.
- **Firewall Rules**: Ensured **restricted access to unauthorized users**.

---

## 📌 Future Enhancements
🔹 **AI-based Call Analytics**: Implement **machine learning models** to analyze call patterns and optimize network performance.
🔹 **Cloud Deployment**: Host the platform on **AWS or Azure** for better scalability and global accessibility.
🔹 **Integration with WebRTC**: Enable **browser-based VoIP calling** for improved accessibility.
🔹 **Enhanced Security Measures**: Implement **end-to-end encryption with Zero Trust Architecture**.

---

## Authors
📌  Horieb Mesfun 
📌  Natnael Haile 
📌  Siem Hagos
