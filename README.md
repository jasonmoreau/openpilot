This is based on Aragon's [0.8.8-shane-spektor-honda-toyota](https://github.com/Aragon7777/openpilot/tree/0.8.8-shane-spektor-honda-toyota) fork. The branch name was inspired by a combination of the original fork's creator, Aragon, and the Argonauts from Jason and the Argonauts.

I have added a few of my own personal touches to it based off of my experience with my 2018 Toyota RAV4 XLE (ICE/non-hybrid) + Comma Pedal + SmartDSU, however this fork may still work well for other vehicles and configurations.

My personal additions so far:
* cruise_offset parameter added to op_edit - intended to help resolve [high-RPM/low-gear issues](https://github.com/commaai/openpilot/issues/2106#issuecomment-753718995) (common in Toyota & Lexus vehicles) by allowing users to adjust set cruise speed multiplier in real time
[![](https://i.imgur.com/XKl293u.png)](#)
* Toggle for switching between stock ACC and openpilot ACC (device reboot or car restart required)
[![](https://i.imgur.com/xm69VMB.png)](#)

To install this fork, ssh into your comma and run the below command:
```
cd /data; mv openpilot openpilot.bkp; git clone -b argonaut-0.8.8 --single-branch https://github.com/jasonmoreau/openpilot.git --depth 1 --recurse-submodules --shallow-submodules -j8
```

