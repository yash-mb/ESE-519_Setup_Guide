# ESE-519_Setup_Guide

    Yash Budhe
    LinkedIn: https://www.linkedin.com/in/yash-mb-a1723812b
    Tested on: HP Envy x360 Convertible, 11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz
    
This is a detailed guide for setting up SDK on Windows PC for RP2040 microcontrollers.
    
## List of Softwares 
 
1. [CircuitPython 7.3.3](https://circuitpython.org/board/adafruit_qtpy_rp2040/)
2. [PyCharm IDE 2022.2.2](https://www.jetbrains.com/pycharm/download/#section=windows)
3. [PuTTY Terminal](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
4. [ARM GNU Toolchain](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)
5. [CMake](https://cmake.org/download/)
6. [Build Tools for Visual Studio 2022](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022)
7. [Python 3.10](https://www.python.org/downloads/windows/)
8. [Git](https://git-scm.com/download/win)

## Steps

### For the Lab 1 part:

1. Follow the [intructions](https://learn.adafruit.com/adafruit-qt-py-2040/circuitpython) given by Adafruit team to setup CircuitPython on the PC. By the end of this we should have a drive called "CIRCUITPY" when the microcontroller is connected to the PC. This task should be pretty straight forward.

2. Instead of Mu editor we will be using PyCharm IDE for editing. Remember to turn on "Safe Write" in Settings->System Settings->Synchronization (true by default).

3. Once the sensor is connected to microcontroller using an STEMMA QT cable, refer to this [page](https://learn.adafruit.com/adafruit-apds9960-breakout/circuitpython) for sample codes to obtain proximity, color, and gesture readings.

4. We can get all the relevant librariers from this [page](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries).

### For Lab 2:

1. Follow the intructions in [Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) step by step. For our particular purpose, refer to section 9.2: Building on MS Windows in Chapter 9: Building on other platforms. 

2. Start with installing the tool chain. 

3. Use the above link for ARM GNU toolchain. And download the highlighted file.

   ![image](https://user-images.githubusercontent.com/99275864/195441170-84d61e6f-0fb4-4cb6-a7ab-89dc7ac575c0.png)

   Remember to check the "Add path to environment variable" at the end.

   ![image](https://user-images.githubusercontent.com/99275864/195442617-81efa4a6-5961-4a06-94d1-fd2986b39c82.png)
   
 
 
 4. Download and install CMake. Download the .msi file for Windows x64. And make sure to check "Add CMake to system PATH for all users". 
 
    ![image](https://user-images.githubusercontent.com/99275864/195445574-6e178d93-7ff3-450c-be3e-1f8ace8ab94d.png)
    
    
    
 5. Install VS code and just select the "Desktop Development with C++". 
 
 6. While installing Python, you should take care of three things. Check "For all users" and "Add Python 3.10 to PATH", and disable "MAX_PATH" length limit.
 
 
 7. During installing Git, make sure to change default editor and choose "Use Notepad as Git's default editor".
 
    ![image](https://user-images.githubusercontent.com/99275864/195448624-347ca8fc-b8f6-46be-9d7f-c4bc3f789ef9.png)

 
    Make sure to check three parts here: "Checkout as is, commit as-is", select "Use Windows' default console window", and "Enable experimental support for pseudo 
    consoles".
 
 
 
 8. Now, go to C: --> Users --> yashm and make a file named "Pico". This is what I follwed but any different path may be choosen. This is where all the files will be 
    extracted.
    
 9. Go to command prompt and input following commands:
    
        C:\Users\yashm\Pico> git clone -b master https://github.com/raspberrypi/pico-sdk.git
        C:\Users\yashm\Pico> cd pico-sdk
        C:\Users\yashm\Pico\pico-sdk> git submodule update --init
        C:\Users\yashm\Pico\pico-sdk> cd ..
        C:\Users\yashm\Pico> git clone -b master https://github.com/raspberrypi/pico-examples.git
        
    This will get the SDK and all the examples which are required.
    
 10. Now, open the developer command prompt for VS 2022. Note: Don't open the regular command prompt, it won't work. 
      
            C:\Users\yashm\Pico> setx PICO_SDK_PATH "..\..\pico-sdk"
        
 11. Close this window and open another developer command prompt and add this following:
        
            C:\Users\yashm\Pico> cd pico-examples
            C:\Users\yashm\Pico\pico-examples> mkdir build
            C:\Users\yashm\Pico\pico-examples> cd build
            C:\Users\yashm\Pico\pico-examples\build> cmake -G "NMake Makefiles" ..
            C:\Users\yashm\Pico\pico-examples\build> nmake
    
  
 12. Inside the build folder go to --> Hello_world --> usb and you will find the files elf, bin, uf2, etc. 
     
     ![image](https://user-images.githubusercontent.com/99275864/195457726-1ecd4c95-8169-43e0-a6b6-d6d668aadd40.png)
     
     
 13. Open VS code and install CMake Tool from the extensions tab. It was alrerady installed from me. Go to settings and then to extension settings. Scroll down and 
     make the following changes:
     
     ![image](https://user-images.githubusercontent.com/99275864/195459081-bf32b3df-86f5-4627-8a4b-305d4323f93c.png)
     
     ![image](https://user-images.githubusercontent.com/99275864/195459147-d32f23f1-a398-4f5b-898e-9d5e7517691f.png)
     
     
 14. 


















    
    
