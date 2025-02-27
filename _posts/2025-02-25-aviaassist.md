---
layout: post
title: "AviaAssist: A Pilot Assistance Tool"
date: 2025-02-25
projects: true
permalink: /projects/aviaassist
hidden: false
star: true
image: "/assets/images/aviaassist_thumbnail.png"
video: "/assets/aviaassist-demo.mp4"
tags: ["iOS", "Swift", "Firebase", "Aviation", "Turkish Airlines"]
---
# AviaAssist ✈️  
<img src="/assets/images/aviaassist_thumbnail.png" alt="AviaAssist Screenshot" width="600" height = "200">
### **An Intelligent Flight Assistant for Turkish Airlines Pilots**  

AviaAssist is a **Swift-based** mobile application developed in collaboration with **Turkish Airlines pilots** and a **UI/UX designer** to improve operational efficiency in aviation. The app is designed to assist pilots with **flight calculations, procedural briefings, and real-time data access**.

### **🌟 Key Features**
#### **🕒 Resting Time Calculator**
- Ensures fair **flight time distribution** among pilots by calculating **resting periods** based on their duty schedules.
- Helps comply with **aviation regulations** and prevents fatigue-related errors.

#### **❄️ Cold Temperature Correction (CTC)**
- Adjusts altitude values based on **outside air temperature**.
- **Why is this important?**  
  - Air is **denser in colder temperatures**, causing altimeters to **overestimate altitude**.  
  - **Correction is required** to ensure aircraft maintain safe separation from terrain and obstacles, especially during winter approaches.  
  - **Formula Used:** ICAO Cold Temperature Altitude Correction Table.

#### **📜 Briefing Scripts (English & Turkish)**
- Provides structured **pre-flight and in-flight briefing scripts**.  
- **Includes Turkish versions**, specifically tailored for **Turkish Airlines pilots**.

#### **📦 Cargo IMP Codes (Powered by Firebase)**
- Uses **Firebase Realtime Database** to:
  - Decode **Cargo Interchange Message Procedure (IMP) Codes**.  
  - Provide instant translations for Turkish Airlines’ cargo operations.

#### **🛫 CTOT (Calculated Time of Takeoff)**
- Displays the **optimized takeoff time** based on airport regulations and air traffic restrictions.

#### **📲 Automated CFR Check-In**
- Generates a **modified phone number** that **automatically checks in** Turkish Airlines employees without manual input.

#### **📍 Simulator Registrations**
- **Tracks and displays** simulator locations based on **aircraft type and simulator number**.  
- Helps Turkish Airlines employees locate **assigned simulators** for training.

---

### **🛠️ Tech Stack**
- **Swift**: iOS development  
- **Firebase Realtime Database**: Storing & retrieving **Cargo IMP codes**  
- **Firebase Authentication**: Secure login for Turkish Airlines employees  
- **UI/UX Designed with Pilots**: Optimized for fast, in-flight usability  

---

### 🎥 **Video Demonstration**
<video width="600" controls>
    <source src="{{ site.url }}/assets/aviaassist-demo.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

---

### **🔗 Links**
- 📂 **GitHub Repository**: [AviaAssist](https://github.com/aydaruya/AviaAssist)  
