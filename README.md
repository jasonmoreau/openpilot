This is based on openpilot v0.8.12 and contains logic from spektor56's fork for always-on lateral control.

This will allow you to toggle openpilot ACC/longitudinal control ("OP long") on or off from the UI, if your car supports it. 

I added this toggle because I have a 2018 Toyota RAV4 XLE (ICE/non-hybrid) with a comma pedal and smartDSU, which enables OP long.

Depending on what kind of driving I'm doing, I wanted the ability to enable or disable OP long.  With my car, I have found that OP long decreases my gas mileage considerably, especially with highway driving.  With this toggle, if I plan on taking a long road trip, I can disable OP long to revert back to my stock ACC and get better gas mileage. 🙂 

Please note that you must either reboot the device or restart your car for this toggle to take effect. If you have any ideas on how I can get this toggle to take effect in real time, please let me know.

[![](https://i.imgur.com/xm69VMB.png)](#)

Changes outlined below:

* Added OpenpilotLongEnabledToggle to [selfdrive/ui/qt/offroad/settings.cc](selfdrive/ui/qt/offroad/settings.cc)
```c++
    {
      "OpenpilotLongEnabledToggle",
      "Enable openpilot",
      "Enable openpilot longitudinal control (if compatible). This is handy if you have a Comma Pedal and/or SmartDSU and want to toggle between stock ACC or openpilot ACC. Restart car or reboot system for this setting to take effect.",
      "../assets/offroad/icon_openpilot.png",
    },
```
* Added OpenpilotLongEnabledToggle to [selfdrive/common/params.cc](selfdrive/common/params.cc)
```c++
    {"OpenpilotLongEnabledToggle", PERSISTENT},
```
* Incorporated toggle in [selfdrive/car/toyota/interface.py](selfdrive/car/toyota/interface.py)
```python
from common.params import Params
```
```python
    params = Params()
    op_long_enabled_toggle = params.get_bool("OpenpilotLongEnabledToggle")
```
```python
    ret.openpilotLongitudinalControl = op_long_enabled_toggle and (smartDsu or ret.enableDsu or candidate in TSS2_CAR)
```
* Added [noise fix](https://github.com/commaai/openpilot/issues/21998) to prevent random disengagements for Toyotas with a Comma Pedal [selfdrive/car/toyota/carstate.py](selfdrive/car/toyota/carstate.py)
```python
      ret.gasPressed = ret.gas > 30
```
To install this fork, ssh into your comma and run the below command:
```
cd /data; mv openpilot openpilot.bkp; git clone -b combo-0.8.12 --single-branch https://github.com/jasonmoreau/openpilot.git --depth 1 --recurse-submodules --shallow-submodules -j8
```
