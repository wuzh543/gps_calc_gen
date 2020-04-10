========================================================================
    Program Project£ºfastgps software calculate test generate files
========================================================================
//
//   04/09/2020
//   by wuzh
//
/////////////////////////////////////////////////////////////////////////////
    This version is based on the calculate part(2018) which inputs the tracking.log file
and outputs the receiver's position.
    This version has same effect as the 2018.But it can produce three files for the gps_calc.

    control_file.txt   The first row has the acquired channel numbers,and then the PRN numbers
                       in every channel.The follow rows are control flags.The first 12 bits are 
                       c[chan].chan_bit_flag,if one channel's flag is 1,in this cycle the program 
                       should collect a bit from the bit_file for the channel.The last bit is the 
                       system_vars.calc_flag,if the bit is 1,in this cycle the program could excute
                       the Leastsquare(if have enough eph). 

                       The control file simulate the interrupt in the embedded system.If there is 
                       no interrupt,all the flag is 0,and the program don't excute anthing.If some 
                       flag is 1,there is at least one interrupt,program collect the bit or start
                       the calculate.
    
    bit_file.txt       This file output every channel's nav bit(20ms) which is already have bit synced
                       by time.Attention:this is not one channel's bit stream.The bit is going to which
                       channel depending on the control_file.txt.

    calc_file.txt      This file output the necessary information for calculate the position.In every row,
                       the first num is loop_count,to calculate the system_vars.recv_time.Then every channel's
                       c[chan].state_ms, c[chan].track.nav_bit_start,  c[chan].code_prompt,  c[chan].doppler.



////////////////////////////////////////////////////////////////////////////

fastgps.vcxproj
    VC++ main project

fastgps.vcxproj.filters
    VC++ filter flie

fastgps.cpp
    main source file

/////////////////////////////////////////////////////////////////////////////
other standard file:

StdAfx.h, StdAfx.cpp
    This file is used to generate the file named fastgps.pch ,which is called precompile head (PCH) file
and the precompile file named StdAfx.obj.

/////////////////////////////////////////////////////////////////////////////

