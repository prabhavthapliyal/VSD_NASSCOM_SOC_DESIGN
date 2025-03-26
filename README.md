# Digital VLSI Design & SoC Planning Workshop  
### Hosted by **VSD & NASSCOM**  

📅 **Workshop Duration:** *March 26, 2025 – April 8, 2025*  

This README serves as a structured **log of progress, learnings, and hands-on work** completed during the **5-day intensive workshop** on **Digital VLSI Design & SoC Planning**. Conducted by **VLSI System Design (VSD) and NASSCOM**, this program covers key aspects of digital design, including **RTL design, synthesis, and physical implementation**.  

---

## 📌 Day 1: Introduction & Synthesis  
### 🔹 Topics Covered:  
✅ Introduction to **open-source SoC design tools** and key stakeholders  
✅ Overview of the **OpenLane flow**  
✅ **Tool installation** and setup  
✅ Exploring the **OpenLane tool directory**  
✅ Running the tool in **interactive mode**  
✅ Preparing a **design (prep command)**  
✅ Running **synthesis** and analyzing output files  
✅ 📌 **Assignment:** *Calculate the Flop Ratio*  

---

### 💻 **Commands Used:**  
```sh
docker
pwd
ls -ltr
./flow.tcl -interactive 
package require openlane 0.9
prep -design picorv32a
run_synthesis
```  

---

### 🗸 **Screenshots & Results:**  

#### 🔹 OpenLane Interactive Flow  
![Exploring OpenLane directory](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/8ce08aee64387274c2da66eaf86e9c52f80dfbc8/01_ss.png)  

#### 🔹 Exploring OpenLane Directory  
![Synthesis result](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/8ce08aee64387274c2da66eaf86e9c52f80dfbc8/02.png)  

#### 🔹 Synthesis Result  
![Synthesis resultant files exploration](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/8ce08aee64387274c2da66eaf86e9c52f80dfbc8/03.png)  

#### 🔹 Synthesis Resultant Files  
![Synthesis resultant files exploration](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/8ce08aee64387274c2da66eaf86e9c52f80dfbc8/04_result.png)  

---

### 📝 **Assignment 1: Flop Ratio Calculation**  
📌 *Formula:*  
```
Flop Ratio = (Number of D Flip Flops) / (Total Number of Cells)
Percentage of DFF's = Flop Ratio * 100
```

📌 *Values from synthesis statistics:*  
```
Flop Ratio = 1613 / 14876 = 0.1084
Percentage of FF's = 0.1084 * 100 = 10.84%
```

---

🚀 **End of Day 1 Summary**  
