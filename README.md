# **Smart Traffic Management System**

This Python project simulates an **intelligent traffic signal control system** that dynamically manages traffic signals based on real-time vehicle flow to optimize traffic movement, reduce congestion, and minimize waiting times at intersections.

## **📌 Steps Involved in the System:**

### **1. Vehicle Generation**  
Vehicles are generated programmatically to simulate traffic entering the intersection. Different vehicle types (e.g., cars, trucks) and directions are randomly created at regular time intervals. This randomness mimics real-world traffic patterns and varying traffic densities. Each vehicle is represented as an object with properties such as speed, direction, and position, allowing individualized behavior during the simulation. This module was implemented using Python’s object-oriented programming concepts.

### **2. Vehicle Detection**  
To simulate real-time traffic data, virtual sensors detect the number of vehicles present in each lane or road segment approaching the intersection. This is done by checking vehicle positions within predefined sensor zones. In a real-world implementation, this module would be replaced with hardware inputs such as cameras or inductive loop sensors. The vehicle counts detected are then forwarded to the signal timing controller to aid decision-making.

### **3. Signal Timing Calculation**  
The core algorithm dynamically calculates the optimal green light duration for each lane based on the detected vehicle counts. Lanes with more vehicles receive longer green phases to reduce waiting times. The algorithm uses a proportional allocation method — the green time for each lane is proportional to its traffic load relative to the total traffic at the intersection. This adaptive timing ensures efficient and fair signal distribution, reducing idle times for low-traffic lanes and overall congestion.

### **4. Signal Switching**  
This module handles the switching of traffic signals between red, green, and yellow states in a **Round Robin manner**. After each lane completes its green phase (as calculated by the Signal Timing module), the control passes to the next lane in a **cyclic order**, ensuring every direction gets a fair turn.

- The order of lanes is predefined (e.g., North → East → South → West), and the system rotates through them continuously.
- The use of **Round Robin scheduling** ensures **non-starvation** of any direction, even during uneven traffic conditions.
- The system integrates this with dynamic green time calculation — meaning each round allocates time **proportionally based on traffic**, but the order of service remains cyclic.

This design balances **fairness (via Round Robin)** with **efficiency (via adaptive timing)**, improving overall traffic throughput and minimizing deadlock or lane starvation.

### **5. Vehicle Movement**  
Vehicles move forward based on the current traffic light status of their lane. This module handles realistic movement features such as acceleration, deceleration, and stopping at red lights. It also includes basic collision avoidance and lane-following logic to mimic real traffic flow. Vehicle positions are updated frame-by-frame within the simulation environment.

### **6. Visualization**  
Using the Pygame library, the entire traffic scenario is graphically rendered in a user-friendly interface. Roads, traffic signals, and moving vehicles are animated in real-time to provide visual feedback of the system’s operation. This visual simulation helps in understanding how the traffic lights adapt and how vehicles respond accordingly.

### **7. Monitoring and Control**  
This module provides user controls to start, pause, and reset the traffic simulation. It also displays live traffic statistics such as vehicle counts per lane, average waiting times, and current signal statuses. These metrics are useful for analyzing the system’s effectiveness and testing different traffic scenarios.

## **🚀 How to Run**  
1. Clone the repository.<br/>
2. Install required dependencies:<br/>
```bash
pip install pygame
