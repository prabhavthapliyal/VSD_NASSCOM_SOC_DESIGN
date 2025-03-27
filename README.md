# Digital VLSI Design & SoC Planning Workshop  
### Hosted by **VSD & NASSCOM**  

📅 **Workshop Duration:** *March 26, 2025 – April 8, 2025*  

This README serves as a structured **log of progress, learnings, and hands-on work** completed during the **2-week intensive workshop** on **Digital VLSI Design & SoC Planning**. Conducted by **VLSI System Design (VSD) and NASSCOM**, this program covers key aspects of digital design, including **RTL design, synthesis, and physical implementation**.  

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
vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/openlane
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

# Day 2: Good Floorplan vs Bad Floorplan & Introduction to Library Cells  

## 📌 Floor Planning Process  

After synthesis, we **initiate floor planning** using the following command:  

```sh  
run_floorplan  
```

#### 🔹 Floorplan Initialization  
![Floorplan Initialization](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/01_VirtualBox_vsdworkshop_27_03_2025_13_26_31.png)  

#### 🔹 Floorplan Visualization  
![Floorplan View](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/02_VirtualBox_vsdworkshop_27_03_2025_13_27_06.png)  

---  

## 📏 **Die Area Calculation in Microns**  

### 📝 Viewing the Floorplan Definition  
To check the **floorplan DEF file**, navigate to:  

```sh  
cd /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_19-16/results/floorplan/  
```

![Floorplan DEF File](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/03_VirtualBox_vsdworkshop_27_03_2025_14_09_03.png)  

### Given Data:  
- **1000 Unit Distance:** 1 Micron  
- **Die Width in Unit Distance:** `660685 - 0 = 660685`  
- **Die Height in Unit Distance:** `671405 - 0 = 671405`  

### 📌 **Die Area Calculation:**  

> **Conversion to Microns:**  
> - **Die Width:** `660685 ÷ 1000 = 660.685 µm`  
> - **Die Height:** `671405 ÷ 1000 = 671.405 µm`  
> 
> **Total Die Area:** `443,587.21 µm²`  

---  

## 🖥️ **Visualizing the Floorplan Using Magic**  

### **Importing Floorplan into Magic Tool**  

```sh  
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/27-03_14-26/results/floorplan/  
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &  
```

#### 🔹 Magic Tool View  
![Magic Tool View](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/04_VirtualBox_vsdworkshop_27_03_2025_17_30_40.png)  

### **Zooming into the Die**  

**Steps to zoom into a section:**  
1. Move the cursor over the section.  
2. Press `s` to select the section.  
3. Press `z` to zoom in.  
4. Press `Shift + Z` to zoom out.  

#### 🔹 Equidistant Placement of Ports  
![Port Placement](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/05_VirtualBox_vsdworkshop_27_03_2025_17_34_53.png)  

#### 🔹 Tap Cells Placed Diagonally  
![Tap Cell Placement](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/08_diagonalplacementtapcellVirtualBox_vsdworkshop_27_03_2025_17_45_43.png)  

#### 🔹 Unplaced Standard Cells  
![Unplaced Cells](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/06_layoutVirtualBox_vsdworkshop_27_03_2025_17_29_25.png)  

---  

## 📌 **Placement of Standard Cells**  

### **Running the Placement Command**  

```sh  
run_placement  
```

#### 🔹 Placement Results  
![Placement Results](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/09_run%20placementVirtualBox_vsdworkshop_27_03_2025_20_07_54.png)  

### **Importing Placement DEF into Magic Tool**  

```sh  
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &  
```

#### 🔹 Standard Cells Arranged Within Rows  
![Standard Cell Placement](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/09_placementpicVirtualBox_vsdworkshop_27_03_2025_20_34_48.png)  

#### 🔹 Final Placement View  
![Final Placement View](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/02a1469cdba91de7e38ba84f9607da0cbb5c5a34/DAY_2/10_placpic2VirtualBox_vsdworkshop_27_03_2025_20_36_21.png)  

---  

This concludes **Day 2** of the workshop on **Good vs Bad Floorplanning** and **Library Cells**. ✅  
