## Section 15 - Cisco Device Management

### The Boot Up Process S15V88

![alt text](image-320.png)

- Flash on newer devices is removable card, older is in a chassis

![alt text](image-321.png)

![alt text](image-322.png)

- If an IOS image can't be found in flash then the device will show the ROMMON prompt at the command line.
    - Can be used to recover a missing or corrupted software image - can boot from USB or an external Trivial File Transfer Protocol (TFTP) server to recover device

![alt text](image-323.png)

![alt text](image-324.png)

![alt text](image-325.png)

![alt text](image-326.png)

![alt text](image-327.png)

![alt text](image-328.png)


### Boot Up Process Lab Demo S15V89


![alt text](image-329.png)

![alt text](image-330.png)
![alt text](image-331.png)

![alt text](image-332.png)

![alt text](image-333.png)

![alt text](image-334.png)

- ^only 1 system image

![alt text](image-335.png)
![alt text](image-336.png)

- still works while running since it's using RAM while running

![alt text](image-337.png)

- ^problem comes when you try to boot up again

Recover System Image:

![alt text](image-338.png)

![alt text](image-339.png)

![alt text](image-340.png)

Since startup-config isn't loaded need to configure ip connectivity at rommon prompt:

![alt text](image-341.png)

- ^if router is on same subnet as TFTP server just put the TFTP (Trivial File Transfer Protocol) server's ip down for default gateway

![alt text](image-342.png)

![alt text](image-343.png)

![alt text](image-344.png)

- ^already IOS system images on the TFTP server 
    - In the real world can download a free TFTP server, or use a paid one

### Factory Reset and Password Recovery S15V90

#### Factory Reset

![alt text](image-345.png)

![alt text](image-346.png)

- ^hostname is R1 in running/startup config

Just change name in running: 

![alt text](image-347.png)

![alt text](image-348.png)

![alt text](image-349.png)

#### Password Recovery 

![alt text](image-350.png)

![alt text](image-351.png)

- ^When you've lost the enable prompt password

![alt text](image-352.png)

- important to copy into running config
- important to copy-register 0x2102 so router will not booth like a factory reset next time

![alt text](image-353.png)

### Password Recovery Lab Demo S15V91

- recovering from a lost enable password or sec ret

- Save a running config: `copy running-config startup-config`

![alt text](image-354.png)
![alt text](image-355.png)

- secret is encrypted password is not
    - secret overrides password

1. Boot Router into rommon mode with 'Ctrl + Break'
    - do it from normal config (can't actually do it irl)

![alt text](image-356.png)

![alt text](image-357.png)

2. Once in rommon mode we need to tell the router to bypass startup-config while booting 

![alt text](image-358.png)

![alt text](image-359.png)

3. Set new enable secret or remove

![alt text](image-360.png)

4. Copy running config

![alt text](image-361.png)

5. In global config reset the register

![alt text](image-362.png)

6. reload again to double-check that it works

**it didn't for this lab??**

- Why: It was originally an 'enable password' and we did 'disable secret' so it's still asking for a password.
    - You would normally add a secret so that wouldn't happen

### Backing up System Image and Configuration S15V92

![alt text](image-363.png)

- helps if you don't want to download it again later
- Backup config helps if you want to rollback
- Can't just copy into running config because they will merge

Steps:

1. Factory reset

2. Take copy of config file (`copy flash tftp` `copy running-config tftp`, etc)

![alt text](image-364.png)

1. Back up system image and running config to TFTP server 

    - Check system image name
    ![alt text](image-365.png)

    - Make sure it's not already on TFTP (Trivial File Transfer Protocol) server (it's not)
    ![alt text](image-366.png)

![alt text](image-367.png)
![alt text](image-368.png)

On router

![alt text](image-369.png)

2. Take a backup to flash then restore it

Router: 

None Yet, copy running config (useful in lab or test environment)
    - Lab: 
        1. Save startup config to flash, do lab exercises
        2. To get back to original startup config do `write erase` 
        3. then `show flash` 
        4. then `copy flash start` with the flash file you saved
        5. Reload
         
![alt text](image-370.png)

![alt text](image-371.png)
![alt text](image-372.png)

### Upgrading IOS S15V93

![alt text](image-373.png)

1. Get new software image
    ![alt text](image-374.png)
2. copy to device's flash using tftp
3. delete old image or use boot system command 

![alt text](image-375.png)

Check current:

![alt text](image-376.png)
![alt text](image-377.png)

Upgrade to new:

See new one in TFTP:
![alt text](image-378.png)

TFTP server is at 10.10.10.10 want to keep same name:
![alt text](image-379.png)

![alt text](image-380.png)

- Now we're gonna keep the old one jic 

- do boot system flash command now it should be good: 
![alt text](image-381.png)

- When system boots up it loads image into RAM so we need to reload the new system image:

![alt text](image-382.png)
![alt text](image-383.png)

Both images are still there: 

![alt text](image-384.png)

Now we're running 15.0: 
![alt text](image-385.png)
 