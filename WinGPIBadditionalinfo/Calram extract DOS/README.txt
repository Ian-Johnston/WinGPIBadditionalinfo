3458ACalramExtract.exe v0.1

Alpha-quality 3458A calram extract utility.

(this is the text from '3458ACalramExtract.exe /?')


>>>
Function:

Extracts the 3458A calram over GPIB to a BIN file suitable for loading into battery backed SRAM with a general
purpose programmer and/or provides a formatted listing from an existing BIN file

Usage:

3458ACalramExtract /GPIB=number or 3458ACalramExtract filename

/GPIB=number Extract calram from GPIB to BIN file
             (Check which GPIB the 3458A is on with the ADDRESS command. Defaults to /GPIB=22)
             Note that the BIN file will appear in the same directory as this executable.
filename     Provide a formatted listing from a BIN file
             (You may need to surround the filename in quotes if it contains spaces)
             e.g. "3458A calram 2015-11-06 17-34-18.bin"

             Note that a log file is produced in the same directory as this executable and named:
             '3458ACalramExtract - [date] [time].log'
<<<


This utility uses a fairly old version of .Net Framework (i.e. 3.5) which should be on most Windows computers. For GPIB extract it
expects visa64.dll etc. in \Windows\System32. It has only been tested with the IVI Foundation Visa (as installed e.g. with Agilent
BenchVue) and on 64 bit machines.

Feel free to email me on alan.ambrose@anagram.net if you find any problems, but don't expect a fast response as I am super busy.




IanJ Info:-
If Address is GPIB1::22:INSTR then set an ALIAS in Keysight IO Expert as GPIB0::22:INSTR

The HP3458A MREAD command returns a 16 bit value as a decimal integer. The 2kB cal SRAM is only 8 bits wide and the values are returned in the high byte. On two of my machines the low byte is always B9 hex. One the other one (earlier serial number) it is always FF.
