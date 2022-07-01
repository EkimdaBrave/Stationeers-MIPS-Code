Mining rocket controller.

Setup:
d0: fuel pump
d1: Mode display (Optional)
d2: Fuel display (Optional)
d3: Minables display (Optional)
d4: Cargo display (Optional)
d5: Recall lever

This script will control the mining rocket to a fully automated state.
It will hold the rocket on the launch pad until the required fuel has been added and the cargo has been unloaded and the activation lever has been set
 then the rocket will launch and mine until it is running low on fuel or the recall lever has been set. Once back on the launchpad it will refuel and unload and relaunch and repeat until you tell it to stop.

The code uses batch commands for the control of the rocket so it will work for all configurations of mining modules, it can handle multiple mining modules and multiple storage silos with no changes to the code.

Update 28/9/2021: total rewrite adding automatic refuelling and automatic relaunch.
Update 29/9/2021: Fixed silos not opening. Fixed will now travel to more than two locations. Fixed errors if rocket has not been launched for the first time.


