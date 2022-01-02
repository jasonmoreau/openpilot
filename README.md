This is my personal openpilot repo, geared towards my own car and configuration:
* 2018 Toyota RAV4 XLE (ICE/non-hybrid)
* Comma Pedal
* SmartDSU

Branches:
* [combo-0.8.12](https://github.com/jasonmoreau/openpilot/tree/combo-0.8.12)
  * Based on openpilot v0.8.12
  * Contains spektor56's logic for always-on lateral control
  * Allows you to toggle between stock ACC and openpilot ACC from the UI
  * Includes [noise fix](https://github.com/commaai/openpilot/issues/21998) to prevent random disengagements for Toyotas with a Comma Pedal
* [combo-0.8.10](https://github.com/jasonmoreau/openpilot/tree/combo-0.8.10)
  * Based on openpilot v0.8.10
  * Contains spektor56's logic for always-on lateral control
  * Allows you to toggle between stock ACC and openpilot ACC from the UI
  * Includes [noise fix](https://github.com/commaai/openpilot/issues/21998) to prevent random disengagements for Toyotas with a Comma Pedal
* [op-long-toggle-0.8.8](https://github.com/jasonmoreau/openpilot/tree/op-long-toggle-0.8.8)
  * Based on pure/stock openpilot v0.8.8
  * Allows you to toggle between stock ACC and openpilot ACC from the UI
  * Includes [noise fix](https://github.com/commaai/openpilot/issues/21998) to prevent random disengagements for Toyotas with a Comma Pedal
* [argonaut-0.8.8](https://github.com/jasonmoreau/openpilot/tree/argonaut-0.8.8)
  * Based on Aragon's [0.8.8-shane-spektor-honda-toyota](https://github.com/Aragon7777/openpilot/tree/0.8.8-shane-spektor-honda-toyota) fork
  * Includes toggle from [op-long-toggle-0.8.8](https://github.com/jasonmoreau/openpilot/tree/op-long-toggle-0.8.8)
  * Added cruise_offset parameter to op_edit for adjusting set cruise speed muiltiplier

Check out [my YouTube channel](https://www.youtube.com/user/J4SONM/videos) to see what I'm up to with openpilot and my RAV4!

Also, feel free to message me on Discord at [jasonmoreau#3991](https://discordapp.com/users/428354577960665090) if you have any questions.
