Airlock Mega Readme
! WIP ! - Non-functional !!
# 2021-12-31 17:50:43

How does the Mega Airlock work?

- Things are divided into seperate 'networks' or sub-systems
    [network]       [offset]    [signals]
    Control                 
    InteriorDoors   10          10|11   Open 0|1 
                                12|13   Lock 0|1  
         Buttons                14|15
         NACK                   18
         ACK                    19 
    ExteriorDoors   20          20|21   Open 0|1
                                22|23   Lock 0|1 
         Buttons                24|25
    InteriorVents   30          30|31   On 0|1
                                32|33   Mode 0|1 (Out|In)
    ExteriorVents   40          40|41   On 0|1
                                42|43   Mode 0|1 (Out|In)

The Control network contains;
    [CtlICH] [GASSensor] [ExtVentICH] [InteriorICH] [ExtDoorICH] [IntDoorICH]

[Control ICH]
CtlICH
    - runs the airlock control code (modifed from some tricksy code someone else wrote - attribute to follow)
        - instead of controlling devices directly, it will write a code [signal] to a specific MEM  chip (one chip for each remote network)
        - when the 'remote' ICH completes it's task it will/could/might Batch Write [signal] the same MEM chip which is read from the CtlICH
    
The PWR & DATA ports of the ICH connect to the control backbone.
The PWR ports of the other ICHs also connect to the control backbone
The DATA ports of the other ICHs connect to their respective (isolated) networks
    There is one MEM per network, which is connected to the ControlICH (via purple) AND the other port of the MEM chip is connected to the DATA network for the 'remote' network



---------------------------------------------------------------------------------------

[Exterior Doors ICH]
ExtDoorICH
- Exterior doors are "Airlock Gate" and do not have any control buttons
This is an ICHousing and IC on an isolated network that consists of ONLY the doors, two buttons and the DATA port of the ICH ONLY
The PWR port of the ICH connects to the control backbone so that it can READ (only) from the ControlICH 

[Connections]
alias DoorMem d0
alias DoorButt1 d1
alias DoorButt2 d2

[Door Network]
[EXT_Door]  [DoorButt1] [DoorButt2] [DoorMem]




--------------------- RONG STUFF ----------------------
it's own ICHousing so that it can be read by the other ICHs 
