portable ltspice simulation how to setup : 

Machine 1:
Machine 2:

Step 1:
	Copy the .asc and "Libs" folder in same directory

Step 2:
	-open the "Libs" folder
	-edit each .asy files (using notepad)
	-remove the line "SYMATTR ModelFile C:\Arvind\Projects\RCU\SimulaTION\Complete Sim 23092025\Libs\TLE2027.LIB"
	 (which is Machine 1 file path)
	-save the .asy files

Step 3:
	make sure the .asc has these statements (lib import command)
	.include Libs\OPAx189.LIB
	.include Libs\TLE2027.LIB
	.include Libs\lm311.lib
	.include Libs\OPAx192.LIB

Step 4:
	-open LTspice.exe
	-open .asc file
	-if the pop up message shows "symbols XXX.LIB, XXX.asy not found", dont worry we need to place the symbols manually
	-open place component(P)
	-choose [Libs]	directory
	-you should see your components "XXX.LIB" from Libs directory
	-if not check Step 2

Step 4:
	-place the particualr components in the circuit, where ever it is not found (empty)
	-for this step you need to have an Circut PDF/image to palce the correct components along with it pin connections

Step 5:
	-modify the simulation settings and save
	-run the simulation