SMART HOME AUTOMATION CONTROLLER
================================

Overview
--------
A menu-driven C console project that simulates a rule-based smart home controller. It manages household devices, schedules and sensor-driven automation, then estimates energy use during simulated operation. This is a software simulation; it does not connect to physical smart-home hardware.

Features
--------
- Add, list and remove lights, air conditioners, fans, heaters and other appliances.
- Set device power ratings and manage time schedules, including schedules that cross midnight.
- Enter sensor readings manually or use a simulated daily profile for temperature, ambient light and occupancy. Optional noise can be added to simulated readings.
- Create, enable, disable and delete automation rules. Rules can use up to two conditions joined with AND.
- Apply manual ON/OFF overrides to individual devices.
- Run the controller in configurable time steps and review estimated energy usage and cost.
- Compare thermostat settings with a what-if simulation.
- Save and reload the home configuration using a local text file.

Device control priority
-----------------------
For each device during a simulation cycle, the controller applies:
1. Manual override, if enabled.
2. A matching schedule, which turns the device on.
3. Matching sensor rules, evaluated in list order; the last matching rule determines the action.

If no rule matches, the device keeps its current state, subject to the program's schedule and override handling.

Requirements
------------
- A C compiler with C99 support (for example, GCC).
- A terminal or command prompt.

Build
-----
Linux / macOS / GCC:
    gcc -std=c99 -Wall -Wextra smart_home.c -o smart_home

Windows / MinGW GCC:
    gcc -std=c99 -Wall -Wextra smart_home.c -o smart_home.exe

Run
---
Linux / macOS:
    ./smart_home

Windows:
    smart_home.exe

On first run, if no configuration file is found, the program loads a sample home with devices, schedules and rules. Use the interactive menu to configure and run the simulation. Configuration is stored in "smarthome.cfg" in the program's current working directory when you choose Save or confirm saving on exit.

Menu summary
------------
1. Add device                 8. Add rule
2. Remove device              9. Show rules
3. Show devices              10. Enable/disable/delete rule
4. Add schedule              11. Run simulation
5. Clear schedules           12. Energy usage report
6. Manual override           13. What-if thermostat simulation
7. Sensors (set / mode)      14. Save configuration
0. Exit

Notes
-----
- Sensor values and energy figures are simulated estimates, not live measurements.
- The energy cost estimate uses a default tariff of Rs 8.00 per kWh. Change TARIFF_PER_KWH in the source to use a different rate.

License
-------
No license is specified in the supplied source file. Add a license before presenting this project as open source if you want others to reuse or distribute it.
