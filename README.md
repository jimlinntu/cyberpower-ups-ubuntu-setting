# CyberPower UPS for Ubuntu

## Prerequisite
* A CyberPower UPS CP1000AVRLCDA
* A Ubuntu 18.04 with CyberPower's PowerPanel for Linux: <https://www.cyberpower.com/tw/en/product/sku/powerpanel%C2%AE_for_linux>

## Settings
* I set `turn-ups-off = no` in `/etc/pwrstatd.conf`. Because I do not want the computer to instruct UPS to shutdown!
    * Remember to `sudo systemctl restart pwrstatd.service` to take effect.

## Troubleshooting
* `sudo pwrstat -status`:
    ```
    The UPS information shows as following:

        Properties:
            Model Name................... CP1000AVRLCDa
            Firmware Number.............. CXVLN2000116
            Rating Voltage............... 120 V
            Rating Power................. 600 Watt(1000 VA)

        Current UPS status:
            State........................ Normal
            Power Supply by.............. Utility Power
            Utility Voltage.............. 114 V
            Output Voltage............... 114 V
            Battery Capacity............. 95 %
            Remaining Runtime............ 52 min.
            Load......................... 72 Watt(12 %)
            Line Interaction............. None
            Test Result.................. Unknown
            Last Power Event............. Blackout at 2021/03/05 22:22:16
    ```
* `sudo pwrstat -config`:
    ```
    Daemon Configuration:

    Alarm .............................................. On
    Hibernate .......................................... Off

    Action for Power Failure:

        Delay time since Power failure ............. 60 sec.
        Run script command ......................... On
        Path of script command ..................... /etc/pwrstatd-powerfail.sh
        Duration of command running ................ 0 sec.
        Enable shutdown system ..................... On

    Action for Battery Low:

        Remaining runtime threshold ................ 300 sec.
        Battery capacity threshold ................. 35 %.
        Run script command ......................... On
        Path of command ............................ /etc/pwrstatd-lowbatt.sh
        Duration of command running ................ 0 sec.
        Enable shutdown system ..................... On
    ```


## References
* <https://www.techpowerup.com/forums/threads/why-would-my-ups-turn-off-while-under-minimal-load.250550/>
