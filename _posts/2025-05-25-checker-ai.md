---
layout: post
title: "Checkers AI: Alpha-Beta vs. Reinforcement Learning"
date: 2025-03-29
projects: true
permalink: /projects/checkers-ai
hidden: false
star: false
image: "/assets/images/checkers_thumbnail.png"
video: ""
tags: ["Python", "AI", "Reinforcement Learning", "Alpha-Beta Pruning", "Games"]
---

# Checkers AI ♟️  
<img src="/assets/images/checkers.png" alt="Checkers Game Screenshot" width="600" height="200">

### **A Classic Board Game But With AI Players**

This project implements an intelligent checkers engine where you can:
- Play against another human  
- Play against an Alpha-Beta pruning AI  
- Train and play against a Reinforcement Learning agent  
- Simulate AI vs. AI matches  

It runs fully in the terminal using ASCII graphics, and strictly follows official checkers rules.

---

### **🧠 AI Techniques Implemented**

#### **Alpha-Beta Player**
- Implements depth-limited minimax with alpha-beta pruning.
- Evaluation function values:
  - Normal pieces = 1 point
  - King pieces = 3 points
- Offers consistent, rule-based performance.
- Depth is configurable (default: 4); higher depths slow down execution.

#### **Reinforcement Learning Player (Q-Learning)**
- Learns optimal moves through self-play using Q-learning.
- Reward structure:
  - +1 for win
  - -1 for loss
  - 0 otherwise
- ε-greedy policy for balancing exploration and exploitation.
- Stores training data in a persistent Q-table using `pickle`.

---

### **🎮 Game Mechanics**
- 8x8 board with diagonal movement, forced captures, and king promotion.
- Enforces all official rules including multi-jumps.
- Promotes pawns to kings on the far row, allowing backward movement.
- Auto-executes forced single capture moves for streamlined play.

---

### **📊 Experimental Results**
- Initial results showed ~50/50 win rates between the agents.
- After extended training (e.g., 10,000 episodes), the RL agent outperformed the alpha-beta agent in most matches.
- Deeper alpha-beta search (e.g., depth 10) became computationally expensive and still fell short strategically.
- RL agent proved more adaptable and learned long-term strategies not captured by the evaluation function.

---

### **🔍 Key Takeaways**
- Alpha-beta is fast and consistent, but limited by its static evaluation function.
- Q-learning, while slower to train, adapts better over time and can outperform rule-based agents.
- Training and simulation features are all built-in and can be triggered via the CLI game menu.

---

### **🛠️ Tech Stack**
- **Python**: Game logic, CLI interaction, AI implementation  
- **Q-Learning**: Reinforcement learning algorithm  
- **Pickle**: Persistent Q-table storage  
- **ASCII UI**: Visual board representation in terminal  

---

### **📂 GitHub Repository**
[🔗 View Checkers AI on GitHub](https://github.com/UzayPoyrza/checker-RL)

