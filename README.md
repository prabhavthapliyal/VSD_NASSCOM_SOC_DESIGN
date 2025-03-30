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

### 1️⃣ Clone the Custom Inverter Standard Cell Design  
### 2️⃣ Load the Custom Inverter Layout in Magic  
### 3️⃣ Spice Extraction of Inverter in Magic  
### 4️⃣ Edit the SPICE Model File for Analysis  
### 5️⃣ Run Post-Layout ngspice Simulations  
### 6️⃣ Fix DRC Issues in the Old Magic Tech File  
  
   
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

Rise transition time calculation

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V

20% screenshots
![19_20%graphriseVirtualBox_vsdworkshop_29_03_2025_19_39_40.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/19_20%25graphriseVirtualBox_vsdworkshop_29_03_2025_19_39_40.png)

![20_20%_output_readingVirtualBox_vsdworkshop_29_03_2025_19_21_58.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/20_20%25_output_readingVirtualBox_vsdworkshop_29_03_2025_19_21_58.png)

80% screenshots
![21_80%outputgraph.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/21_80%25outputgraph.png)

![22_rise_80calcVirtualBox_vsdworkshop_29_03_2025_19_32_29.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/22_rise_80calcVirtualBox_vsdworkshop_29_03_2025_19_32_29.png)

```math
Rise\ transition\ time = 2.24577 - 2.18214 = 0.06363\ ns = 63.63\ ps
``

Fall transition time calculation

```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V

20% screenshots

![23_falltime_20%graphVirtualBox_vsdworkshop_29_03_2025_19_44_12.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/23_falltime_20%25graphVirtualBox_vsdworkshop_29_03_2025_19_44_12.png)
![24_falltime20%readingVirtualBox_vsdworkshop_29_03_2025_19_44_41.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/24_falltime20%25readingVirtualBox_vsdworkshop_29_03_2025_19_44_41.png)

80%screenshots
![25_falltime_80$graphVirtualBox_vsdworkshop_29_03_2025_19_46_26.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/25_falltime_80%24graphVirtualBox_vsdworkshop_29_03_2025_19_46_26.png)
![26__falltime_80$calcVirtualBox_vsdworkshop_29_03_2025_19_47_00.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/26__falltime_80%24calcVirtualBox_vsdworkshop_29_03_2025_19_47_00.png)

```math
Fall\ transition\ time = 4.095 - 4.05927  = 0.03573\ ns = 35.73\ ps

```Rise Cell Delay Calculation

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```
50% screenshots
![27_risecellelaygraph50%VirtualBox_vsdworkshop_29_03_2025_19_58_31.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/27_risecellelaygraph50%25VirtualBox_vsdworkshop_29_03_2025_19_58_31.png)
![28_risecelldelaycalc50%VirtualBox_vsdworkshop_29_03_2025_19_57_58.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/28_risecelldelaycalc50%25VirtualBox_vsdworkshop_29_03_2025_19_57_58.png)

```math
Rise\ Cell\ Delay = 2.21069 - 2.14977 = 0.06092\ ns = 60.92\ ps
```

Fall Cell Delay Calculation

```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```
50% screenshots
![29_fallcell50%graphVirtualBox_vsdworkshop_29_03_2025_20_00_21.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/29_fallcell50%25graphVirtualBox_vsdworkshop_29_03_2025_20_00_21.png)
![31_fallcellcalc50%VirtualBox_vsdworkshop_29_03_2025_20_01_17.png](https://raw.githubusercontent.com/prabhavthapliyal/VSD_NASSCOM_SOC_DESIGN/main/DAY_3/31_fallcellcalc50%25VirtualBox_vsdworkshop_29_03_2025_20_01_17.png)

```math
Fall\ Cell\ Delay = 4.07717 - 4.04957 = 0.0276\ ns = 27.96\ ps
```

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


## Section 4 - Pre-layout timing analysis and importance of good clock tree 
