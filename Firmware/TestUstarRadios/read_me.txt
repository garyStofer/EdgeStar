This folder contains the project files for j-logo/u-logo programs to exercise the dual radios and sensors
found on the uStar-V2 main board.

Two projects exist: 
	testRFM_TX.prj for the flight unit 
	testRFM_RX.prj for the ground unit.

Folders and Files of importance:
	logo 			-- folder sym-lnk to /usr/local/i3/logo  -- needed by compile and execution environment.
	
	testRFM_TX.prj	-- text project file containing the file names for the "JL" build environment to build the flight unit app.               
	testRFM_TX.logo	-- text J-logo file for the PC side code. Empty for the transmit side  -- must have same filename root as .prj 
	mainTX.txt		-- text u-logo file with the program entry point (ul-power) and main loop (ul-go).	
	
	testRFM_RX.prj	-- text project file containing the file names for the "JL" build environment to build the ground unit app.               
	testRFM_RX.logo	-- text J-logo file for the PC side code, must have same filename root as .prj. 
						Contains all the code that runs on the PC side to wait for and display a freshly received packet on the terminal
	mainRX.txt		-- text u-logo file with the program entry point (ul-power) and main loop (ul-go).	
	
Shared files between the two projects:	
	common.txt  	-- symbolic link to /usr/local/i3/logo/common.txt , read only -- contains APP board specific defines and functions. 
						not used directly -- some editors can not open symbolic linked files. File mycommon.txt originates from this file.          
	mycommon.txt	-- local copy of common.txt since some editors can not open files through symbolic links  
	            
	rfm22b_23bp.txt	-- text u-logo file with specific code for the operation of the two radio boards and the control thereof through the uStar-V2 interface                        
	rfm22b-init.txt	-- text u-logo file with RFM22/23 radio initialization data.           
	      
	
Other files of minor importance:
	read_me.txt		-- this file  
	np++.sess 		-- editor session file for notepad++ , a popular Windows based code editor easily installable on Ubuntu with bundled Wine  
	  
	data 			-- folder that the JL environment makes to save a log file of activities                

Note: Files with extension .txt are compiled and downloaded to the app board, while files with extension .logo execute 
		interpreted on the PC side.

	
      
Some hints of how to operate the JL environment
-----------------------------------------------           	  
To load the project into the "java logo" environment "jl"  first start the jl shell script "jl".  "jl" is in /usr/local/i3 and
the Linux user profile needs to setup correctly with the PATH to reach it.
                       
After the Welcome message, load the project with the command:  .project "testRFM     -- note the logo style single quote      
The jl environment should respond with a message:   Start Project:  testRFM   followed by the current time.... 

To compile the code use command: .compile -- if successful it will print the number of bytes of the compiled byte code.
A compile in the current session needs to proceed a download.

To download the byte code to the APP board use: .download -- Note the FTDI USB adapter must have been plugged in
BEFORE you started the jl environment. Pressing the reset button on the APP board before .download is sometimes needed. 

During the download the red and green led on the FTDI USB adapter blinks vigorously. 
The download terminates with a message indicating how many bytes have been programmed.            

To start the application press the reset button on the APP board.

