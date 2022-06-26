# How to run ESP32 on VM


## Download and run the VM

   * Download and install the VMWare Player from [here](https://customerconnect.vmware.com/en/downloads/details?downloadGroup=WKST-PLAYER-1623-NEW&productId=1039&rPId=85399).
   * Download [VM image](https://drive.google.com/file/d/1xOLU-tVGi6lpPW1X19SgKS9j1awppvm_/view?usp=sharing). Extract it wherever it is suitable for you.
   * Run VMWare Player and select “Open a Virtual Machine”. Provide path to the “SuperWitrualka.vmx” file.
   * Select “SuperWirtualka” from the VM list and click on “Edit virtual machine settings”. Adjust Memory and Processors amount to as much as your machine allows (about 80% of all RAM and cores should be fine). Click Save button.
   * Click on Power On button in VMWare Player. The VM should power up. Login credentials are as following:
      * Login: user
      * Password: user


## Connect the devboard

   * Start console and type in ```bash ls -la /dev/ttyUSB*```. There should be no devices listed. If there is any, just remember its name.
   * Connect ESP32 devboard to the computer.
   * Move your coursor to the top of the screen. A VMWare bar should appear. Select Virtual Machine → Removable Devices → Silicon CP2102 USB to UART Bridge Controller → Connect
   * Go back to the terminal window and run again ```bash ls -la /dev/ttyUSB*```. A new device should appear - this is your board.


## Check if everything works

   * Run VS Code
   * On the bar on the left select ESP-IDF Explorer icon
   * Press Ctrl + Shift + T and type “new project”. Select ESP-IDF:New Project
   * Choose proper serial port from the list and change project directory to be outside of a repository. Click Choose Template button.
   * From the drop-down list select “ESP-IDF” and then “hello_world” template from the get-started section. Click on Create project using template hello_world button. When you get a prompt if open a project in new window, select Yes.
   * Go to the bottom bar in VS Code window. You should see a set of icons there. Select “ESP-IDF Build, Flash and Monitor” button (a fire icon). When you are prompted to select interface, choose UART.
   * If everything goes well, in up to 2-3 minutes a console should appear with following output. If not, click Full Clean (trashbin icon) and try again.

      ```
      I (0) cpu_start: App cpu up.
      I (213) cpu_start: Pro cpu start user code
      I (213) cpu_start: cpu freq: 160000000
      I (213) cpu_start: Application information:
      I (218) cpu_start: Project name:     project-name
      I (223) cpu_start: App version:      1
      I (227) cpu_start: Compile time:     May 29 2022 18:50:55
      I (233) cpu_start: ELF file SHA256:  11559448d7de7454...
      I (239) cpu_start: ESP-IDF:          v4.4.1-dirty
      I (245) heap_init: Initializing. RAM available for dynamic allocation:
      I (252) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
      I (258) heap_init: At 3FFB2C28 len 0002D3D8 (180 KiB): DRAM
      I (264) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
      I (271) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
      I (277) heap_init: At 4008B1E8 len 00014E18 (83 KiB): IRAM
      I (285) spi_flash: detected chip: generic
      I (288) spi_flash: flash io: dio
      I (293) cpu_start: Starting scheduler on PRO CPU.
      I (0) cpu_start: Starting scheduler on APP CPU.
      Hello world!
      This is esp32 chip with 2 CPU core(s), WiFi/BT/BLE, silicon revision 1, 4MB external flash
      Minimum free heap size: 295372 bytes
      Restarting in 10 seconds...
      Restarting in 9 seconds...
      Restarting in 8 seconds...
      Restarting in 7 seconds...
      Restarting in 6 seconds...
      Restarting in 5 seconds...
      Restarting in 4 seconds...
      Restarting in 3 seconds...
      Restarting in 2 seconds...
      Restarting in 1 seconds...
      Restarting in 0 seconds...
      Restarting now.
      ```
