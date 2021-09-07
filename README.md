This is based on Aragon's [0.8.8-shane-spektor-honda-toyota](https://github.com/Aragon7777/openpilot/tree/0.8.8-shane-spektor-honda-toyota) fork. The branch name was inspired by a combination of the original fork's creator, Aragon, and the Argonauts from Jason and the Argonauts.

I have added a few of my own personal touches to it based off of my experience with my 2018 Toyota RAV4 XLE (ICE/non-hybrid) + Comma Pedal + SmartDSU, however this fork may still work well for other vehicles and configurations.

My personal additions so far:
* cruise_offset parameter added to op_edit - intended to help resolve [high-RPM/low-gear issues](https://github.com/commaai/openpilot/issues/2106#issuecomment-753718995) (common in Toyota & Lexus vehicles) by allowing users to adjust set cruise speed multiplier in real time
[![](https://i.imgur.com/XKl293u.png)](#)
* Toggle for switching between stock ACC and openpilot ACC (device reboot or car restart required)
[![](https://i.imgur.com/xm69VMB.png)](#)

Changes outlined below:

* Added OpenpilotLongEnabledToggle to [selfdrive/ui/qt/offroad/settings.cc](selfdrive/ui/qt/offroad/settings.cc)
```c++
  toggles.append(new ParamControl("OpenpilotLongEnabledToggle",
                                  "Enable openpilot Longitudinal Control",
                                  "Enable openpilot longitudinal control (if compatible). This is handy if you have a Comma Pedal and/or SmartDSU and want to toggle between stock ACC or openpilot ACC. Restart car or reboot system for this setting to take effect.",
                                  "../assets/offroad/icon_openpilot.png",
                                  this));
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
To install this fork, ssh into your comma and run the below command:
```
cd /data; mv openpilot openpilot.bkp; git clone -b argonaut-0.8.8 --single-branch https://github.com/jasonmoreau/openpilot.git --depth 1 --recurse-submodules --shallow-submodules -j8
```

