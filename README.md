# Introduction
In this file we have documented all the labs of Software course.

There are a total of 12 videos in this course and there are 11 labs.

Detailed steps of each lab is written in the respective files.

## Create a new Zynq Project
1.	Launch Vivado application
2.	Click on Create Project
3.	Upon clicking Next, Name your Project file and location. Important Note: Keep it saved in a non-administrative access location as this will be your <Local Project> location.
4.	Choose RTL-based project as your project type and click Next
5.	Select Vivado as Target Language and click Next for the next 2 times.
6.	To choose target device choose the following options to work on MiniZed : - 
    Product category: General Purpose ~~ Family:  Zynq-7000 ~~ Package: clg225 (MiniZed) ~~ Speed grade -1 ~~ Temp grade: Leave empty ~~ select the xc7z007sclg225-1
7.	Click Next and then Finish.

## Create Block Design
1.	Select Create Block Design under IP Integrator panel to the left
2.	Enter Design name and click OK
3.	And to add an IP, Select ‘+’ and search for Zynq and select it.
4.	Run block Automation (This is done to perform the tasks on the processor’s core)
5.	Click on Ok in the pop up window after checking Cross Trigger In & out as Disable. (This is done to connect external devices.

    Note: Save your progress when any changes are made so as to not lose progress.

## Enabling Specific Peripherals
1.	To configure the PS, Double click on the IP block allowing you to customize the PS features.
2.	Note: a ✓ along the blocks shows if they are enabled or not.
    To configure a peripheral, click on the peripheral or go to MIO config on the Page navigator panel to the left.
3.	In the config window, set Bank 0 &1 I/O voltage as LVCMDS 3.3V if using a MiniZed Board.
4.	Listed below are the peripherals, and select the specific one that you require by selecting the check box.
5.	You can verify your selection in the block design with a ✓.

## Configuring Memory and Clocks
1.	Click on clock Config in navigation panel
2.	Verify if Input freq is 33.33 MHz, CPU is 666.66 MHz and DDR is 533.33 MHz.
3.	If not using any PL. disable the FCLK_CLK under PL Fabric Clock in clock configuration and disable M AXI GP0 Interface under PS-PL Configuration -> AXI Non   Secure Enablement -> GP Master AXI Interface section -> M AXI GP0 Interface.
4.	Click on DDR config under the page navigator and check Enable DDR.
5.	Select the specific parameters as follows: Memory Type: DDR3 (LV), Memory Part: MT41K256M16RE-125.
6.	Under custom verify if the the DRAM Bus is 16 bits for MiniZed. Make sure Internal Vref is unchecked.
7.	Check Write leveling, Read gate, and Read data eye options
8.	Click OK.

## Build the hardware platform and export to SDK
1.	In the Diagram window of the Zynq Block Design click on the Validate Design 🗹.
2.	After a successful validation, in the block design window click on Sources (Its beside the Flow Navigator).
3.	Right-Click on your Project and select Create HDL Wrapper and select OK.
4.	To build the design click on Generate Bitstream from the Flow Navigator panel.
5.	In the Launch Runs window, change Number of jobs to 1 under Launch runs on local host.
6.	After it loads click OK for open Implemented design.
7.	To export the Project, File -> Export -> Export Hardware, and check Include bitstream and click OK.
    Note: Keep it saved in a non-administrative access location as this will be your <Local Project> location.
8.	Click on Launch SDK and accept after choosing the Project location.
 
## Create and running an Application
1.	Launch SDK from Vivado or Open the application Xilinx SDK.
2.	Click on File -> New -> Board Support Package. Accept default settings and Click Finish. If an error prompt comes up stating no Hardware Project found, click OK and continue and select the HDF file save from your <Local Project Location> you’ve saved in and click Finish.
3.	Click standalone in the Board Support Package window and click OK to the default settings.
4.	Once the BSP is added to the project, select File -> New -> Application Project.
5.	In the application project window, Name your project and under BSP select Use Existing. Click Next and choose your template and click Finish. (Example Hello World).
6.	Important: Don’t forget to select the Serial Port in the SDK Terminal before running any application.

## Enabling and Mapping all PS Peripherals
1.	In Block design, go to MIO configurations in the navigation pane.
2.	Check the QSPI checkbox, and check Feedback Clock under it and choose MIO 8 as I/O
3.	If using Ethernet map into EMIO otherwise check USB0 and enable it. But to set a Reset option, select GPIO -> USB Reset and expand it and set USB0 Reset to MIO 7. 
4.	Cross check the peripherals enabled in the Block diagram.

## Setting PS and PLL clocks
1.	In the block design window, select Clock config in the Page Navigator panel.
2.	Make sure the QSPI peripheral uses the IO peripheral as its clock source. Set the QSPI input clock to 200MHz.
3.	Change SDIO to 25MHz
4.	(IF you’re using an PL, then enable the following
    • FCLK_CLK0 to 100 MHz
    • FCLK_CLK1 to 150 MHz
    • FCLK_CLK2 to 50 MHz
    • FCLK_CLK3 to 25 MHz
    Keep PL Fabric Clocks disabled if you’re not using any PL)
5.	Click OK and Validate the Block Design🗹. Save Progress.
6.	Under Design Sources, right- click and select Reset Output Products (   )
7.	Click Reset.
8.	Right-click again and select Generate Output Products. Select Global and click Generate.
9.	Generate Bitstream as done before.


## Creating and Running test Applications ( Memory & Peripheral tests)
1.	Open Vivado and Export hardware to <Local Project> as before (Recommended). Important: Include Bitstream
2.	Then Launch SDK from File tab.
3.	Repeat Step 2-4 in Create and Running an Application.
4.	FOR MEMORY TEST. Name the Project as Memory_test and click Next. Select Memory Tests Template and then select Finish.
5.	Important: Don’t forget to select the Serial Port in the SDK Terminal.
6.	Right-click on Memory_Tester, select Run As  Run Configurations
7.	Select Xilinx C/C++ Application (System Debugger), then New Configuration icon in the top left of the options
8.	Open Terminal, such as GTKTerm, and set the COM port to active COM setting
9.	for your board and set the Baud Rate to 115,200
10.	Click Run
11.	FOR PERIPHERAL TESTS: Repeat the same above procedure except instead of choosing Memory test template, choose Peripheral Test template.
12.	 The Passed result will be seen in the  SDK Terminal if the tests are successful. 

## Using PL-based BRAM (Used to buffer data btw PS and PL)
__A.__
   1.	Open Block design and select Add IP ‘+’.
   2.	Search for BRAM and select AXI BRAM Controller.
   3.	A Block diagram of the AXI BRAM Controller will be added to the design window. Double click on it and make sure the data Width is set to 64 bits.
   4.	Set AXI Narrow Bursts to Manual and Select OK.
   5.	When any changes are made to the BLock Design View, if Designer Assistance is available, Select Run Connection Automation and select All automation. (This allows the software to make automatic connections based on the presets and preferences set).
 
__B.__ (Connecting to PL. Must enable Fabric Clock)
   1.	In the Zynq Overview block Diagram, click on PS-PL Config ->GP Master Axi Interface -> M AXI GP0 Interface. (Remember we had disabled this earlier as we had no PL to connect to).
   2.	In Clock Config, Set Fabric Clock -> FCLK_CLK0 to 50MHz.
      (As we have enabled PL settings, THE PS block has PL connections.)
   3.	Run Connection Automation. Make sure to check All Automation.
   4.	Cross check if the following connections have been made:
       •	BRAM Controller S_AXI to AXI Interconnect M_AXI
       •	 AXI Interconnect S_AXI to PS7 M_AXI
       •	 PS7’s FCLK_CLK0 in 6 locations
       •	 PS7’s FCLK_RESET0_N to the Processor System Reset
       •	 Processor System Reset then resets the AXI Interconnect and BRAM Controller
   5.	Validate Design 🗹
   6.	Double click on the block design to view their properties.
   7.	Save the design and Reset and then generate the Output Products by right-clicking on the 
   Z_system_i under Sources.
   8.	Generate Bitstream and select Yes for Launch Synthesis and Implementation.

__C.__ Testing the PS DMA Controller
   1.	Export Hardware. Don’t forget to select Include Bitstream while doing it.
   2.	Launch SDK. Set up Board Support Package.
   3.	To import, go to File-> Import. Select General -> Existing Projects into Workspace.
   4.	Go to the created ZynqDesign.lab3  directory and select OK.Check the box Copy projects into Workspace and select all the three applications and click Finish.
   5.	Create a new Application Project and name it as BRAM_DMA_Test and select use existing BSP. Click Finish instead of next as you are selecting an Empty Application.
   6.	In the Project panel in the left, Under BRAM_DMA_Test, right click on src and choose Import.
   7.	In the Import window, browse to <Local Project
