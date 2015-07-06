### Description

 LSM9DS0 linux driver. Can be used on a raspberry PI. Tested on Raspberry 2 Linux a4h-rpi2-arch 4.0.7-1-ARCH 

### Prerequisities
 
 * LSM9DS0 powered @3.3 and connected to i2c-1, SDA-1 (pin 3), SCL-1 (pin 5) - http://www.element14.com/community/docs/DOC-73950/l/raspberry-pi-2-model-b-gpio-40-pin-block-pinout
 * i2c and i2c-dev loaded https://wiki.archlinux.org/index.php/Raspberry_Pi#I2C
 * lsm9ds0 gyro and lsm9ds0 Accel/mag i2c peripherals instantiated, depending on  SDO_XM/SA0_XM pin and  SDO_G/SA0_G pin  :

### Compilation / install
    
    make
    insmod lsm9ds0_gyr.ko
    insmod lsm9ds0_acc_mag.ko

### Module loading

 * i2c and i2c-dev loaded https://wiki.archlinux.org/index.php/Raspberry_Pi#I2C
 * lsm9ds0 gyro and lsm9ds0 Accel/mag i2c peripherals instantiated, depending on  SDO_XM/SA0_XM pin and  SDO_G/SA0_G pin:
    
    
    echo 'lsm9ds0_gyr 0x6a' > /sys/bus/i2c/devices/i2c-1/new_device 
    echo 'lsm9ds0_gyr 0x6b' > /sys/bus/i2c/devices/i2c-1/new_device
    
    echo 'lsm9ds0_acc_mag 0x1d' > /sys/bus/i2c/devices/i2c-1/new_device
    // OR 
    echo 'lsm9ds0_acc_mag 0x1e' > /sys/bus/i2c/devices/i2c-1/new_device
    
    # test it using evtest
 
### Module testing

    evtest
    No device specified, trying to scan all of /dev/input/event*
    Not running as root, no devices may be available.
    Available devices:
    /dev/input/event0:      lsm9ds0_gyr
    /dev/input/event1:      lsm9ds0_acc
    /dev/input/event2:      lsm9ds0_mag
    Select the device event number [0-2]: 0
    Input driver version is 1.0.1
    Input device ID: bus 0x18 vendor 0x0 product 0x0 version 0x0
    Input device name: "lsm9ds0_gyr"
    Supported events:
      Event type 0 (EV_SYN)
      Event type 3 (EV_ABS)
        Event code 0 (ABS_X)
          Value    124
          Min   -32769
          Max    32768
        Event code 1 (ABS_Y)
          Value    134
          Min   -32769
          Max    32768
        Event code 2 (ABS_Z)
          Value   -157
          Min   -32769
          Max    32768
        Event code 40 (ABS_MISC)
          Value      0
          Min        0
          Max        1
    Properties:
    Testing ... (interrupt to exit)
    Event: time 1436193950.437630, type 3 (EV_ABS), code 0 (ABS_X), value 514
    Event: time 1436193950.437630, type 3 (EV_ABS), code 1 (ABS_Y), value 346
    Event: time 1436193950.437630, type 3 (EV_ABS), code 2 (ABS_Z), value -1307
    Event: time 1436193950.437630, -------------- EV_SYN ------------
    Event: time 1436193950.538694, type 3 (EV_ABS), code 1 (ABS_Y), value 508

    

### Useful links

 * original source files http://www.st.com/web/en/catalog/tools/PF258124
 * datasheet http://www.st.com/st-web-ui/static/active/en/resource/technical/document/datasheet/DM00087365.pdf
 