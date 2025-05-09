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

Section 2 tasks:- 
1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
2. Calculate the die area in microns from the values in floorplan def.
3. Load generated floorplan def in magic tool and explore the floorplan.
4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
5. Load generated placement def in magic tool and explore the placement.

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

# 📌 Section 3 - Design Library Cell using Magic Layout and ngspice Characterization


## 🛠️ Implementation

## ✅ Section 3 Tasks

 **1. Clone the Custom Inverter Standard Cell Design**  
 **2. Load the Custom Inverter Layout in Magic**  
 **3. Spice Extraction of Inverter in Magic**  
 **4. Edit the SPICE Model File for Analysis**  
 **5. Run Post-Layout ngspice Simulations**  
 **6. Fix DRC Issues in the Old Magic Tech File**  
     
---

#### 1. Clone custom inverter standard cell design from github repository

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```
Screenshot of commands run

![05_git_clone_VirtualBox_vsdworkshop_28_03_2025_14_06_38.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/05_git_clone_VirtualBox_vsdworkshop_28_03_2025_14_06_38.png)

#### 2. Load the custom inverter layout in magic and explore.

Screenshot of custom inverter layout in magic

![06_layoutVirtualBox_vsdworkshop_28_03_2025_21_39_20.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/06_layoutVirtualBox_vsdworkshop_28_03_2025_21_39_20.png)
NMOS and PMOS identified
Layout showing NMOS
![07_layout_showing_nmosVirtualBox_vsdworkshop_29_03_2025_13_21_55.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/07_layout_showing_nmosVirtualBox_vsdworkshop_29_03_2025_13_21_55.png)

Layout showing PMOS
![08_layoutshowingpmosVirtualBox_vsdworkshop_29_03_2025_13_22_47.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/08_layoutshowingpmosVirtualBox_vsdworkshop_29_03_2025_13_22_47.png)

Output Y connectivity to PMOS and NMOS drain verified
![09_ouputconnectivity_d-dVirtualBox_vsdworkshop_29_03_2025_13_28_37.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/09_ouputconnectivity_d-dVirtualBox_vsdworkshop_29_03_2025_13_28_37.png)

PMOS source connectivity to VDD (here VPWR) verified
![10_sourceofpmos_vddVirtualBox_vsdworkshop_29_03_2025_13_30_25.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/10_sourceofpmos_vddVirtualBox_vsdworkshop_29_03_2025_13_30_25.png)

NMOS source connectivity to VSS (here VGND) verified
![11_sourcenmostogndVirtualBox_vsdworkshop_29_03_2025_13_30_53.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/11_sourcenmostogndVirtualBox_vsdworkshop_29_03_2025_13_30_53.png)

Deleting necessary layout part to see DRC error
![12_drcerrorVirtualBox_vsdworkshop_29_03_2025_14_06_34.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/12_drcerrorVirtualBox_vsdworkshop_29_03_2025_14_06_34.png)  

#### 3. Spice extraction of inverter in magic.

Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic

```tcl
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```

Screenshot of tkcon window after running above commands
![13_SpicwfilecreationVirtualBox_vsdworkshop_29_03_2025_14_18_27.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/13_SpicwfilecreationVirtualBox_vsdworkshop_29_03_2025_14_18_27.png)

Screenshot of created spice file
![14_spice createdVirtualBox_vsdworkshop_29_03_2025_14_21_05.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/14_spice%20createdVirtualBox_vsdworkshop_29_03_2025_14_21_05.png)

#### 4. Editing the spice model file for analysis through simulation.

Measuring unit distance in layout grid
![15_BoxdimensionVirtualBox_vsdworkshop_29_03_2025_18_13_34.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/15_BoxdimensionVirtualBox_vsdworkshop_29_03_2025_18_13_34.png)

Final edited spice file ready for ngspice simulation
![16_editingspice_deck_VirtualBox_vsdworkshop_29_03_2025_18_33_35.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/16_editingspice_deck_VirtualBox_vsdworkshop_29_03_2025_18_33_35.png)

#### 5. Post-layout ngspice simulations
Commands for ngspice simulation

```bash
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
```
Screenshots of ngspice run
![18_plot_1_VirtualBox_vsdworkshop_29_03_2025_18_52_20.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/18_plot_1_VirtualBox_vsdworkshop_29_03_2025_18_52_20.png)

Screenshot of generated plot
![17_transientVirtualBox_vsdworkshop_29_03_2025_19_51_17.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/17_transientVirtualBox_vsdworkshop_29_03_2025_19_51_17.png)

## ⚡ Rise Transition Time Calculation

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```

```math
20\%\ of\ output = 660\ mV
```

```math
80\%\ of\ output = 2.64\ V
```

### 📈 20% Screenshots
![19_20%graphriseVirtualBox_vsdworkshop_29_03_2025_19_39_40.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/19_20%25graphriseVirtualBox_vsdworkshop_29_03_2025_19_39_40.png)

![20_20%_output_readingVirtualBox_vsdworkshop_29_03_2025_19_21_58.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/20_20%25_output_readingVirtualBox_vsdworkshop_29_03_2025_19_21_58.png)

### 📊 80% Screenshots
![21_80%outputgraph.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/21_80%25outputgraph.png)

![22_rise_80calcVirtualBox_vsdworkshop_29_03_2025_19_32_29.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/22_rise_80calcVirtualBox_vsdworkshop_29_03_2025_19_32_29.png)

```math
Rise\ transition\ time = 2.24577 - 2.18214 = 0.06363\ ns = 63.63\ ps
```

---

## 🔻 Fall Transition Time Calculation

```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```

```math
20\%\ of\ output = 660\ mV
```

```math
80\%\ of\ output = 2.64\ V
```

### 📉 20% Screenshots
![23_falltime_20%graphVirtualBox_vsdworkshop_29_03_2025_19_44_12.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/23_falltime_20%25graphVirtualBox_vsdworkshop_29_03_2025_19_44_12.png)

![24_falltime20%readingVirtualBox_vsdworkshop_29_03_2025_19_44_41.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/24_falltime20%25readingVirtualBox_vsdworkshop_29_03_2025_19_44_41.png)

### 📉 80% Screenshots
![25_falltime_80$graphVirtualBox_vsdworkshop_29_03_2025_19_46_26.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/25_falltime_80%24graphVirtualBox_vsdworkshop_29_03_2025_19_46_26.png)

![26__falltime_80$calcVirtualBox_vsdworkshop_29_03_2025_19_47_00.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/26__falltime_80%24calcVirtualBox_vsdworkshop_29_03_2025_19_47_00.png)

```math
Fall\ transition\ time = 4.095 - 4.05927 = 0.03573\ ns = 35.73\ ps
```

---

## ⏫ Rise Cell Delay Calculation

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```

```math
50\%\ of\ 3.3\ V = 1.65\ V
```

### ⏳ 50% Screenshots
![27_risecellelaygraph50%VirtualBox_vsdworkshop_29_03_2025_19_58_31.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/27_risecellelaygraph50%25VirtualBox_vsdworkshop_29_03_2025_19_58_31.png)

![28_risecelldelaycalc50%VirtualBox_vsdworkshop_29_03_2025_19_57_58.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/28_risecelldelaycalc50%25VirtualBox_vsdworkshop_29_03_2025_19_57_58.png)

```math
Rise\ Cell\ Delay = 2.21069 - 2.14977 = 0.06092\ ns = 60.92\ ps
```

---

## ⏬ Fall Cell Delay Calculation

```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```

```math
50\%\ of\ 3.3\ V = 1.65\ V
```

### ⏳ 50% Screenshots
![29_fallcell50%graphVirtualBox_vsdworkshop_29_03_2025_20_00_21.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/29_fallcell50%25graphVirtualBox_vsdworkshop_29_03_2025_20_00_21.png)

![31_fallcellcalc50%VirtualBox_vsdworkshop_29_03_2025_20_01_17.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/31_fallcellcalc50%25VirtualBox_vsdworkshop_29_03_2025_20_01_17.png)

```math
Fall\ Cell\ Delay = 4.07717 - 4.04957 = 0.0276\ ns = 27.96\ ps
```
---
#### 6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Link to Sky130 Periphery rules: [https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html](https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html)

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```bash
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
```

Screenshots of commands run
![32_drc_1VirtualBox_vsdworkshop_30_03_2025_01_14_38.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/32_drc_1VirtualBox_vsdworkshop_30_03_2025_01_14_38.png)

Checking DRC errors

![33_drc_2met3VirtualBox_vsdworkshop_30_03_2025_01_14_38.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/33_drc_2met3VirtualBox_vsdworkshop_30_03_2025_01_14_38.png)
![34_drc_whyVirtualBox_vsdworkshop_30_03_2025_01_25_11.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/34_drc_whyVirtualBox_vsdworkshop_30_03_2025_01_25_11.png)

Modifying .magicrc file for extra rule implementation and then checking errors

![35_rulesdrcScreenshot 2025-03-30 015323.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/35_rulesdrcScreenshot%202025-03-30%20015323.png)

![36_ruleviolationpoly9VirtualBox_vsdworkshop_30_03_2025_01_52_05.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/36_ruleviolationpoly9VirtualBox_vsdworkshop_30_03_2025_01_52_05.png)

![37_polynonresVirtualBox_vsdworkshop_30_03_2025_02_16_17.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/37_polynonresVirtualBox_vsdworkshop_30_03_2025_02_16_17.png)

![38_drc_nowshowingerrorVirtualBox_vsdworkshop_30_03_2025_02_18_35.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/38_drc_nowshowingerrorVirtualBox_vsdworkshop_30_03_2025_02_18_35.png)

![39_diffnprres_EquisdistatmodecheckVirtualBox_vsdworkshop_28_03_2025_12_07_40.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/39_diffnprres_EquisdistatmodecheckVirtualBox_vsdworkshop_28_03_2025_12_07_40.png)

![40_drccheck2caseVirtualBox_vsdworkshop_30_03_2025_03_15_36.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/40_drccheck2caseVirtualBox_vsdworkshop_30_03_2025_03_15_36.png)


Incorrectly implemented nwell rule
![42_nwellVirtualBox_vsdworkshop_30_03_2025_03_27_46.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/42_nwellVirtualBox_vsdworkshop_30_03_2025_03_27_46.png)

Adding contact
![43_nsubstratencontactVirtualBox_vsdworkshop_30_03_2025_03_32_33.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/43_nsubstratencontactVirtualBox_vsdworkshop_30_03_2025_03_32_33.png)

 New commands inserted in sky130A.tech file to update drc
![44_changesinfileVirtualBox_vsdworkshop_30_03_2025_03_45_52.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/44_changesinfileVirtualBox_vsdworkshop_30_03_2025_03_45_52.png)
![45_changesmoreVirtualBox_vsdworkshop_30_03_2025_03_47_44.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/45_changesmoreVirtualBox_vsdworkshop_30_03_2025_03_47_44.png)

Again checking DRC
![46_finalVirtualBox_vsdworkshop_30_03_2025_04_00_38.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/46_finalVirtualBox_vsdworkshop_30_03_2025_04_00_38.png)

---  


# 📌 Section 4 - Pre-layout Timing Analysis & Importance of a Good Clock Tree ⏱️

## 📖 Theory

## 🛠️ Implementation

### ✅ Section 4 Tasks:

* Section 4 tasks:-
1. Verify the design is ready to be inserted into our flow.
2. Save the finalized layout with custom name and open it.
3. Generate lef from the layout.
4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
6. Run openlane flow synthesis with newly inserted custom inverter cell.
7. Reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. New netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.


#### 1. Verify the design is ready to be inserted into our flow.

Commands to open the custom inverter layout

```bash
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd
![01_trackinfocommand where they areVirtualBox_vsdworkshop_31_03_2025_11_43_49.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/01_trackinfocommand%20where%20they%20areVirtualBox_vsdworkshop_31_03_2025_11_43_49.png)

![02_trackinfoVirtualBox_vsdworkshop_31_03_2025_11_38_50.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/02_trackinfoVirtualBox_vsdworkshop_31_03_2025_11_38_50.png)

Commands for tkcon window to set grid as tracks of locali layer

```tcl
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```
Screenshot of commands run
![03_ssrunning_gridVirtualBox_vsdworkshop_31_03_2025_12_34_44.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/03_ssrunning_gridVirtualBox_vsdworkshop_31_03_2025_12_34_44.png)

Veryifying Conditions
![04_firstcondnverifiedVirtualBox_vsdworkshop_31_03_2025_12_35_57.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/04_firstcondnverifiedVirtualBox_vsdworkshop_31_03_2025_12_35_57.png)

#### 2. Save the finalized layout with custom name and open it.

Command for tkcon window to save the layout with custom name

```tcl
# Command to save as
save sky130_vsdinv.mag
```

Command to open the newly saved layout

```bash
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
```
Screenshot of commands
![05_running command and seeing newlycreatedfile and loading in magic.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/05_running%20command%20and%20seeing%20newlycreatedfile%20and%20loading%20in%20magic.png)

Screenshot of newly saved layout
![06_lefwriteVirtualBox_vsdworkshop_31_03_2025_13_06_55.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/06_lefwriteVirtualBox_vsdworkshop_31_03_2025_13_06_55.png)
#### 3. Generate lef from the layout.

Command for tkcon window to write lef

```tcl
# lef command
lef write
```

Screenshot of command run

![06_lefwriteVirtualBox_vsdworkshop_31_03_2025_13_06_55.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/06_lefwriteVirtualBox_vsdworkshop_31_03_2025_13_06_55.png)

Screenshot of newly created lef file

![07_newelylefVirtualBox_vsdworkshop_31_03_2025_13_10_22.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/07_newelylefVirtualBox_vsdworkshop_31_03_2025_13_10_22.png)

#### 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory

```bash
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Screenshot of commands run
![08_allcopy(lef_fast_slow).png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/08_allcopy(lef_fast_slow).png)

#### 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow

```tcl
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory
![09_configtclfilemodVirtualBox_vsdworkshop_31_03_2025_13_38_41.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/09_configtclfilemodVirtualBox_vsdworkshop_31_03_2025_13_38_41.png)

#### 6. Run openlane flow synthesis with newly inserted custom inverter cell.

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshots of commands run

![10_allcommands screenshotsVirtualBox_vsdworkshop_31_03_2025_13_57_54.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/10_allcommands%20screenshotsVirtualBox_vsdworkshop_31_03_2025_13_57_54.png)

#### 7. Reeduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

Noting down current design values generated before modifying parameters to improve timing

![11_chipareaVirtualBox_vsdworkshop_31_03_2025_14_03_26.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/11_chipareaVirtualBox_vsdworkshop_31_03_2025_14_03_26.png)

![12_tns_wnsVirtualBox_vsdworkshop_31_03_2025_14_09_09.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/12_tns_wnsVirtualBox_vsdworkshop_31_03_2025_14_09_09.png)

Commands to view and change parameters to improve timing and run synthesis

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 31-03_08-21 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
Screenshots of commands run
![Changing strategy](<https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/13_changing%20strategyandrunningsynthesis%2Bsynth%20strat.png>)


#### 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command

```tcl
# Now we can run floorplan
run_floorplan
```

Screenshots of command run
![14_run_floorplanfailedVirtualBox_vsdworkshop_31_03_2025_16_01_46.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/14_run_floorplanfailedVirtualBox_vsdworkshop_31_03_2025_16_01_46.png)

Since we are facing unexpected un-explainable error while using `run_floorplan` command, we can instead use the following set of commands available based on information from `Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl` and also based on `Floorplan Commands` section in `Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md`

```tcl
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```

Screenshots of commands run

![15_FLOORPLAN(SS)VirtualBox_vsdworkshop_31_03_2025_16_03_35.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/15_FLOORPLAN(SS)VirtualBox_vsdworkshop_31_03_2025_16_03_35.png)

![16_floorplanssVirtualBox_vsdworkshop_31_03_2025_16_03_57.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/16_floorplanssVirtualBox_vsdworkshop_31_03_2025_16_03_57.png)

Now that floorplan is done we can do placement using following command

```tcl
# Now we are ready to run placement
run_placement
```

Screenshots of command run
![17_placementdoneVirtualBox_vsdworkshop_31_03_2025_16_05_57.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/17_placementdoneVirtualBox_vsdworkshop_31_03_2025_16_05_57.png)

Commands to load placement def in magic in another terminal

```bash
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-03_08-21/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
Screenshot of commands run
![18_commandtoloadmagicVirtualBox_vsdworkshop_31_03_2025_16_07_33.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/18_commandtoloadmagicVirtualBox_vsdworkshop_31_03_2025_16_07_33.png)

Screenshot of placement def in magic
![19_placementdefmagicVirtualBox_vsdworkshop_31_03_2025_16_08_36.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/19_placementdefmagicVirtualBox_vsdworkshop_31_03_2025_16_08_36.png)

Screenshot of custom inverter inserted in placement def with proper abutment
![20_ourcustomcellVirtualBox_vsdworkshop_31_03_2025_16_16_41.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/20_ourcustomcellVirtualBox_vsdworkshop_31_03_2025_16_16_41.png)

Command for tkcon window to view internal layers of cells

```tcl
# Command to view internal connectivity layers
expand
```
![21_expandcommandVirtualBox_vsdworkshop_31_03_2025_16_17_24.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/21_expandcommandVirtualBox_vsdworkshop_31_03_2025_16_17_24.png)

Abutment of power pins with other cell from library clearly visible
![22_VirtualBox_vsdworkshop_31_03_2025_16_18_53.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/22_VirtualBox_vsdworkshop_31_03_2025_16_18_53.png)

#### 9. Do Post-Synthesis timing analysis with OpenSTA tool.

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
Commands run final screenshot
![](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/8a2a194b76bf2a8d6bc2fb9f0f7c75e79ad70466/DAY_3/runsynthesisdelay3.png)

We created `pre_sta.conf` for STA analysis in `openlane` directory
![23_newpreconstaVirtualBox_vsdworkshop_31_03_2025_17_06_51.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/23_newpreconstaVirtualBox_vsdworkshop_31_03_2025_17_06_51.png)

We created `my_base.sdc` for STA analysis in `openlane/designs/picorv32a/src` directory based on the file `openlane/scripts/base.sdc`

![SDC file screenshot](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/24_sdcfileVirtualBox_vsdworkshop_31_03_2025_18_38_20.png)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

![25_runstaVirtualBox_vsdworkshop_31_03_2025_18_39_00.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/25_runstaVirtualBox_vsdworkshop_31_03_2025_18_39_00.png)

![26_tnswnsafterstaVirtualBox_vsdworkshop_31_03_2025_18_39_38.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/26_tnswnsafterstaVirtualBox_vsdworkshop_31_03_2025_18_39_38.png)

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis 

```tcl
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 31-03_08-21 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot
![27_SYNTHMAXFANOUTVirtualBox_vsdworkshop_31_03_2025_19_04_15.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/27_SYNTHMAXFANOUTVirtualBox_vsdworkshop_31_03_2025_19_04_15.png)

![28_synthesisafterfanout_VirtualBox_vsdworkshop_31_03_2025_19_09_16.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/28_synthesisafterfanout_VirtualBox_vsdworkshop_31_03_2025_19_09_16.png)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run
![29_sameafterstaVirtualBox_vsdworkshop_31_03_2025_19_12_04.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/29_sameafterstaVirtualBox_vsdworkshop_31_03_2025_19_12_04.png)

#### 10. Make timing ECO fixes to remove all violations.

i) OR gate of drive strength 2 is driving 4 fanouts

![30_orgate4fanout.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/30_orgate4fanout.png)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Screenshot of commands
![31_commandstoreplaceorgatefig.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/31_commandstoreplaceorgatefig.png)

Result - slack reduced

![32_slackreducedhuaiise.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/32_slackreducedhuaiise.png)

---

ii)OR gate of drive strength 2 is driving 4 fanouts

![33_nowimprovingthisor.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/33_nowimprovingthisor.png)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Screenshot of commands
![34_commands_for_replace.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/34_commands_for_replace.png)

Result - slack reduced
![35_slackimprovedagain.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/35_slackimprovedagain.png)

---

iii) Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
![36_changingthisorgate.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/36_changingthisorgate.png)

```tcl
# Reports all the connections to a net
report_net -connections _12150_

# Replacing cell
replace_cell _15168_ sky130_fd_sc_hd__or2_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Running commands
![37_commandsforreplace.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/37_commandsforreplace.png)

Result - slack reduced

![38_slackimproved.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/38_slackimproved.png)

Finally tns/wns improved
![39_finallytns_wns_reduced.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/39_finallytns_wns_reduced.png)

**We started ECO fixes at wns -23.8900 and now we stand at wns -22.9262 we reduced around 0.9638 ns of violation**

---
#### 11. New netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Commands to write verilog

```tcl
# Check syntax

write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-03_08-21/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

Screenshot of commands run
![40_writeverilog_.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/40_writeverilog_.png)

Verified that the netlist is overwritten by checking that instance `_15168_`  is replaced with `sky130_fd_sc_hd__or2_4`
![42_netlistupdateverified(15168).png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/42_netlistupdateverified(15168).png)

Commands load the design and run necessary stages

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 31-03_08-21 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```

Screenshots of commands run

![43_floorplandonewithdiffsteps.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/43_floorplandonewithdiffsteps.png)

![44_runningplacement.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/44_runningplacement.png)

![45_placementrunss.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/45_placementrunss.png)

![46_runcts.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/46_runcts.png)

![47_ctssuccessful.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/47_ctssuccessful.png)

#### 12. Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/31-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/31-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/31-03_08-21/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated
![48_post_cts_openroadcommands.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/48_post_cts_openroadcommands.png)

![49_slackmet.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/49_slackmet.png)

![50_slack_met_2.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/50_slack_met_2.png)

#### 13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing `CTS_CLK_BUFFER_LIST`

```tcl
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/31-03_08-21/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/31-03_08-21/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/31-03_08-21/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/31-03_08-21/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```
Screenshots of commands run and timing report generated

![51_(lreplace_didnt_worked).png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/51_(lreplace_didnt_worked).png)

![52_removingbufferdiffstyle_settingenvvariable_buthaveputwrongdirectory.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/52_removingbufferdiffstyle_settingenvvariable_buthaveputwrongdirectory.png)

![53_rightdirectory_runcts.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/53_rightdirectory_runcts.png)

![54_run_cts_executedVirtualBox_vsdworkshop_02_04_2025_12_02_25.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/54_run_cts_executedVirtualBox_vsdworkshop_02_04_2025_12_02_25.png)

![55_running_again_openroad_updatedbuffer.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/55_running_again_openroad_updatedbuffer.png)

![56_slack_metAGAIN1.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/56_slack_metAGAIN1.png)

![57_(56part2).png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/57_(56part2).png)

![58_slew_hold_slew_setup.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_4/58_slew_hold_slew_setup.png)

---
## Section 5 - Final steps for RTL2GDS using tritonRoute and openSTA 🔚

### Theory 📘

### Implementation 🛠️

* Section 5 tasks:-
1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout 🔌.
2. Perform detailed routing using TritonRoute 🧭.
3. Post-Route parasitic extraction 🧲.
4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route ⏱️.


#### 1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 
```
Screenshots of power distribution network run

Commands to load PDN def in magic in another terminal

```bash
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/04-04_10-10/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```
Screenshots of command run

![01_genpdn.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/01_genpdn.png)


Screenshots of PDN def
![02_pdnsuc.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/02_pdnsuc.png)

![03_pdndef1.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/03_pdndef1.png)

![04_pdndef2.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/04_pdndef2.png)


#### 2. Perfrom detailed routing using TritonRoute and explore the routed layout.

Command to perform routing

```tcl
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```

Screenshots of routing run
![05_runroutcommand.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/05_runroutcommand.png)

![06_routesuccesful.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/06_routesuccesful.png)

Commands to load routed def in magic in another terminal

```bash
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/04-04_10-10/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```

Screenshots of routed def

![07_routeddeffopencommands.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/07_routeddeffopencommands.png)

![08_routteddef_magic.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/08_routteddef_magic.png)

![09_routeddef2.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/09_routeddef2.png)


#### 3. Post-Route parasitic extraction .

Spef file was already present in
```tcl 
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/04-04_10-10/results/routing
```

Screenshot of file
![10_spef_file.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/10_spef_file.png)

#### 4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/04-04_10-10/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/04-04_10-10/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/04-04_10-10/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/04-04_10-10/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![11_lasttimingin_openroad.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/11_lasttimingin_openroad.png)

![12_timgrep1.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/12_timgrep1.png)

![13_timingrep2.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_5/13_timingrep2.png)

---

# Acknowledgements

* [Kunal Ghosh](https://github.com/kunalg123), Co-founder, VSD Corp. Pvt. Ltd.
* [Nickson P Jose](https://github.com/nickson-jose), Physical Design Engineer, Intel Corporation.
* [R. Timothy Edwards](https://github.com/RTimothyEdwards), Senior Vice President of Analog and Design, efabless Corporation.

---
# Certificate
![13_timingrep2.png](https://github.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/blob/0fb0f5c3bfdbe4c3f8ce6df0ae808506d1b1373a/IMG_1020.jpeg)

---









