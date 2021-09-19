# Introduction
In this file we have documented all the labs of Software course.

There are a total of 12 videos in this course and there are 11 labs.

**Detailed steps of each lab is written in the respective files.**

### 1. LAB 1

#### Experiment 1: Review the Hardware Platform Archive
1.	By the help of lab1 we can find the exported Zynq hardware Platform within Vivado project directory str.
2.	Following the steps of the lab 1 we can find the folder where the Vivado project writes the hardware platform by default.
3.	All the contents can be found in a single .hdf file, this is a compressed file that contains the. Information to develop software applications within SDK.

### 2. LAB 2

#### Creating a hardware platform 
1: File → new → other
2: Select hardware platform specification under the xillinx tab
3: Specify project name   
4: Add the location of the Z_system_wrapper.hdf file in the target hardware specification text box
5: Click finish 
   A folder with the project name should be visible in the project explorer tab
   
#### Experiment 2: Examine the Hardware Platform
1.	The ZynqHW hardware platform is visible in project structure in the system.hdf file. 
2.	There are two sections for the hardware organized sections. 
3.	In the system.hdf file there is IP blocks present, in design there is IP number which represents the name of the IP design. 
4.	In second column there is the name of the IP.
5.	Name of IP is more relevant.
6.	IP helps for the hardware person.

### 3. LAB 3

#### Creating a BSP( Board Support package) file 
1. File → new → Board Support Package
2. Select the hardware platform for which u want to create a support package
3. Click finish
4. The bsp package setup will open navigate to the standalone tab under the overview file
5. Change the value of stdin and stdout from ps7_uart_0 to ps7_uart_1
6. Click ok 
7. All the necessary drivers would be added to ur program file under the bsp documentation tab

#### Experiment 2: Explore the BSP
1.	We can open the BSP report by clicking system.mss file. 
2.	The generic written in red color indicates that there is no defined driver present. 
3.	Whereas blue means there is a specific driver.
4.	By clicking in the hyperlink for standalone_v6_5, we can open the cortex A9 processor API.
5.	There is each hardware peripheral listed along with the driver associated with that peripheral, by clicking on the documentation we can view the datasheet for the driver.
6.	By clicking on Import examples link next to GPIOPS, a window pops and selecting xspiops_olled_example and clicking on OK we can import a polled example in the workspace.

#### Experiment 3: Library Generator (LibGen)
1.	Library generator was the one that assembled BSP. 
2.	Expanding BSP documentation it shows the link for each peripheral driver.
3.	Expand ps_7_cortexa_9_0 and there will be 4 sub folders. 
4.	The code directory is a repo for SDK executables. 
5.	There is a include folder wich contains C header file which are needed by drivers to run. 
6.	Lib folder contains driver function that a particular processor can access.
7.	Libsrc folder contains intermediate files and make files needed to compile Oss, lib, drivers.
8.	It also contains files to run BSP OS, peripheral specific driver file and more.

### 4. LAB 4

#### Experiment 1: Develop an Application with Example Code

1. Create a new application Project and keep your BSP as existing BSP.
2. After that select empty application and click on finish.
3. Create a source file with the name of .c.
4. The changes of the build will be seen in the console window.
5. There will be a directory with a file of hello world.c open it with gedit.
6. Select the contents of the entire file and paste it in hell_zynq.c file.
7. Now the issue of BSP can also be resolved, generally it fixes itself but in some cases it doesn’t. 
8. In case it doesn’t Select standalone_bsp_0 in Project Explorer. Now select Project -> Clean. 
9. Select the radio button for Clean projects selected below. Check the box for standalone_bsp_0. Click OK. 
10. After cleaning, an automatic rebuild will start which will eliminate the red X from the BSP. 
11. There is a linker script clicking on it, it opens a summary tab. 
12. The tab shows the available memory regions, stack and heap sizes, mapping between application sections and memory regions, the summary section is completely editable.
13. We can also create a new linker script for a project.

#### Experiment 2: Add Peripheral Test

1. Make a new peripheral test application project with existing BSP. 
2. The file has an option to enable I- and D- caches. 
3. Then right click on the function line 63 and 64 and click on open declaration. 
4. The function declaration is displayed in source code file xil_cache.c, which is part of the BSP. 
5. You’ll notice that both CacheEnable() functions include the commands to enable both the L1 and L2 caches.


### 5. LAB 5


#### Experiment 1: Setup Hardware and Download Bitstream

1.	Connect the MiniZed USB-JTAG/UART port J2 to your PC, make the JTAG and serial port available to the Virtual Machine by right clicking on the USB Icon and selecting Xilinx JTAG + Serial option. 
2.	Set the COM port and Baud Port to 115200. In SDK set Xilinx Tools -> Program FPGA.
3.	SDK will already know the correct .bit file since this was imported with the hardware platform. 
4.	Click Program. 
5.	When the DONE LED lights blue, the PL has configured successfully. Look for the message “FPGA configured successfully with bitstream” in the SDK log. 

#### Experiment 2: Running an Application

1.	Run the hello world and test memory application on the MiniZed, right click on Hello_Zynq Application Run As -> Run configuration. 
2.	Then Double click on Xilinx C/C++ Application.
3.	Ensure the connection type is set to Standalone Application Debug. 
4.	Make sure both Run ps7_init and Run ps7_post_config are enabled. 
5.	Ensure the application is set to download your desired application. 
6.	Then go back to SDK and click on Run.

#### Experiment 3: Debug an Application

1.	Right click on Test_peripherals pplication and select Debus As, then select Debug configurations. 
2.	Then select Xilinx C/C++ Application then click on the new icon. 
3.	Then click on Debug. 
4.	Then click on Yes to confirm the perspective switch. 
5.	Make Sure GTK Term is Closed at the bottom of the SDK screen, select the SDK  Terminal tab. 
6.	Click the green “Connect to serial port” icon. 
7.	Change the Settings for 115200 baud, 8 data bits, 1 stop bit, no parity and no flow control. 
8.	Choose the COM port identified previously. 
9.	Click OK. 
10.	On the debug pane click on step over icon to advance the application by one line to code.  
11.	If line numbers are not already shown, select Window -> Preferences. 
12.	Within the Preferences dialog, browse to Genera -> Editors -> Text Editors. 
13.	Click the checkbox for Show line numbers. 
14.	Click OK.
15.	Go on the code line no. 273 double click on the blue line a blue check mark will appear the in the breakpoints tab where u can delete and disable breakpoints, click on resume(Green Arrow).
16.	Under the Debug tab in the upper left-hand corner, right-click on System Debugger using Debug_Test_Peripherals.elf on local (Local) and select Relaunch. 
17.	Click OK. 
18.	To end the debug click on disable option.

### 6. LAB 6

#### Experiment 1: Generate the FSBL

1.	SDK is used to generate First Stage Bootloader Application using a Template.
2.	In SDK, File -> New -> Application Project.
3.	Name it zynq_fsbl_0 and make a new BSP. Then click on next.
4.	Select Zynq FSBL and click on Finish.
5.	Use console output to determine the debug configuration build size. Use linker script to determine target memory.
6.	Setup the stdin and stdout in BSP like that of lab 3.
7.	Right click on the Debug folder underneath the zynq_fsbl_0 application and select properties.
8.	Properties -> Settings -> Optimization and debugging.
9.	For optimization the debug level will be at none and for debugging the level will be maximum.
10.	Click on manage configurations, then select release -> set active -> OK.
11.	Then on the optimization window click Apply -> OK.
12.	If it doesn’t build click on project -> Build All.
13.	A release folder will be created in zynq_fsbl_0.

#### Experiment 2: Investigate the FSBL

1.	Expand zynq_fsbl_0  src. Notice the various .c and .h files that SDK pulled together for the FSBL. 
2.	Double click on the main.c and scroll down the. Code to get an overview.

### 7. LAB 7

  
#### Experiment 1: Create the QSPI Boot Image

1.	We will not be debugging the Test peripheral application, we will change active configuration to active release.
2.	Build Configurations -> Set Active Release.
3.	Force the new configuration build by, Project -> Build All.
4.	Select Test_Peripheral, Xilinx Tools -> Create Boot Image.
5.	If dialog box is not pre populated, click Cancel and then select Clean Project.
6.	Radio Button -> Create a new BIF file, be on Basic tab.
7.	Change the output format to MCS to generate a QSPI image, change file name -> Test_Peripherals.mcs, click create image.

#### Experiment 2: Write and boot from QSPI

1.	Turn on the board, Xilinx Tools -> Program Flash.
2.	Click Browse button, browse to SDK_Workspace\Test_Peripherals\bootimage then select .mcs file and click on Open.
3.	Again, click Browse button and go to SDK_Workspace\Zynq_fsbl-0\Release and then select zynq_fsbl_0_.elf file, click Program.
4.	Power off the board, set MiniZed boot mode switch SW1 to QSPI mode. Close the terminal.
5.	Power on the board by reconnecting USB-JTAG_UART J2 connection, blue light should illuminate.
6.	Launch the terminal program with the 115200/8/n/1/n settings.
7.	Push reset.
8.	Close termina, unplug USB-UART-JTAG cable.

### 8. LAB 8

#### Experiment 1: Create a Complete SDK Project Archive

1.	File -> Export -> General -> Archive File -> Next -> ‘Select all check boxes’ -> Select All -> Browse -> “Lab08_project_export.zip” in ZynqSW\2019_1 -> Save -> Finish.
2.	File -> Export -> Run/Debug -> Launch Configurations -> Next -> Select All -> browse to /home/training/AvnetTTC/ZynqSW/2017_4/ -> Make New Folder -> name it Lab_08_config_export -> OK -> Finish.
3.	File -> Export -> Run/Debug -> Breakpoints -> Next -> Select All -> browse to /home/training/AvnetTTc/ZynqSW/2019_1/ -> name it Lab_08_breakpoint_export.bkpt -> Save -> Finish.
4.	Create a new folder in /home/training/AvnetTTC/ZynqSW/2019_1 directory.
5.	Browse to File Explorer from workspace to .metadata\.plugins\org.eclipse.core.runtime\.settings make a copy of the files in this folder and copy them to Lab08_repositores_export.

#### Experiment 2: Import a Shared Project Archive

1.	File -> Switch Workspace -> Other -> name it New_Workspace -> OK.
2.	File -> Import -> General -> Existing Projects into Workspace -> Next.
3.	Select the button Select archive file and open Lab08_project_export.zip -> Select All -> Finish.
4.	File -> Import -> Run/Debug -> Launch Configurations -> Next.
5.	Browse to /home/trainig/AvnetTTC/ZynqSW/2019_1/Lab08_config_export -> OK -> Select Lab08_config_export -> Finish.
6.	File -> Import -> Run/Debug -> Breakpoints -> Next -> browse to /home/training/AvnetTTC/ZynqSW/2017_4/ -> Select Lab08_breakpoint_export.bkpt -> Open -> Finish.
7.	Copy files from Lab08_repositories_export folder and paste in .metadata\.plugins\org.eclipse.core.runtime\.settings.
8.	Open SDK again.
9.	Set your board to Cascaded JTAG MODE.
10.	Connect the USB-UART-JTAG (J2).
11.	Download PL Bitstream and Hello_Zynq to test.

### 9. LAB 9

#### Experiment 1: Create the Interrupt Application Project

1.	File -> New -> Application Project -> LED_Dimer_w_Int, change BSP to use existing standalone_bsp_0 -> Next -> Empty Application -> Finish.
2.	Right click on src folder and click import -> General Item -> File System -> Next -> Browse and select the folder witch application code, select main.c and click Finish.
3.	Connect the board to your laptop.
4.	Project Explorer -> LED_Dimmer_w_int -> Run As -> Launch on hardware (System Debugger).

#### Experiment 2: Add Interrupt Support to the Application

1.	LED_Dimmer_w_Int -> src -> main.c -> add imports.
2.	And also add definitions to map our interrupt setup routine.
3.	Declare variables, brightness will be declared globally.
4.	Add a code under variable declarations, this will act as a call back function.
5.	Add a function near line 89 which provides setup needed to enable the PWM interrupt to be recognized and attaches PWNIsr() as interrupt handler.
6.	Initialize brightness to 0.
7.	Add a call to SetupInterruptSystem() near line 164.

### 10. LAB 10

#### Experiment 1: Create the Application Project

1.	File -> New -> Application Project -> New Project -> Project Name -> flash_mac_app -> BSP   -> Create New -> flash_mac_app_bsp -> Next -> Empty Application -> Finish.
2.	Click on the Modify this BSP’s Setting to configure flash_mac_app_bsp.
3.	Enable Xilinx In system and Serial Flash Library by selecting checkboxes.
4.	In BSP setting -> Overview -> standalone -> xilisf -> Micron QSPI flash -> for serial_flash_family, 5 for seral_flash_interface, 3, -> change to stdin and stdout.
5.	Right click flash_mac_app -> src -> import -> general -> file system -> next-> browse -> /home/training/AvnetTTC/ZynqSW/2017_4/Support_documents/flash_mac_app/ -> OK -> select 18 files -> Import.

#### Experiment 2: Exploring the Application

1.	Reser on MiniZed, boot mode to JTAG mode, connect JTAG.
2.	Xilinx tools -> Program FPGA -> program.
3.	Project Explorer -> Run As -> Launch on Hardware.
4.	Help on Terminal -> mac help -> use the command to read and display QSPI Flash.
5.	Flash_mac_app -> src -> flash_mac.c.

### 11. LAB 11

#### Experiment 1: Create a Standalone BSP and an Application for the HTU21D Pmo

1.	System.mss -> Peripheral drivers -> “axi_iic_2iic” -> documentation.
2.	File -> new -> application Project -> “HTU21D” -> Next -> Empty Application -> Finish.
3.	HTU21D -> src -> Import.
4.	General -> File System -> Next.
5.	Browse -> Ok -> /home/training/AvnetTTC/ZynqSW/2019_1/Support_documents/Lab11 -> Select All -> Finish.

#### Experiment 2: Hardware Setup to Run HTU21D Pmod Application

1.	Boot mode switch SW1 to JTAG mode.
2.	Disconnect the MiniZed board.
3.	Connect you HTU21D Pmod to Pmod 2 connector on MiniZed.
4.	Set the COM port to active COM setting and set the Baud Rate to 115200.
5.	Xilinx Tools -> Program FPGA -> Program.

#### Experiment 3: Run and Explore HTU21D I2C Pmod Application

1.	Right click on HTU21D -> Run As -> Launch on hardware.
2.	Expand src and the six files will be visible
