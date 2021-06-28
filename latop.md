# Used Laptop checklist

1. Power up while plugged in, then let it run for 30 minutes on battery. Note the changes.
2. Check system info -- processor, ram, drive, etc `lspci -k `
3. check that BIOS is not password protected -- DO NOT BUY IF IT IS PASSWORD PROTECTED, or, MAKE SURE HE GIVES YOU IT. If there's a BIOS password and he doesn't know what it is, then it could be stolen goods and it is not worth the fuss of trying to work around it.
	- Lenovo cannot reset the BIOS aka supervisor password -- losing this will literally brick the board and require a full replacement computer.
	- Ask if there is a hard disk password as well -- ask for it if there is one
	- ask if Power password has been set. this is a pain in the ass but as long as you have the BIOS/Supervisor PW, you'll be ok.
4. WiFi Connectivity
4. Viewing Angle, Brightness, Color Contrast
5. Check Keyboard backlight
5. Type a pangram -- the quick brown fox jumped over the lazy dog.
6. Check Battery Cycles `upower -i /org/freedesktop/UPower/devices/battery_BAT0`
7. On Windows 10, run this: `start > run > type 'perfmon /report'`

## Questions to Ask
1. Where it was purchased originally
9. Why is it being sold
10. If you can inspect the inside of the chassis
	- Check if the disk is removable
	- Check if the ram is soldered on 
	- check if battery and SSD are factory original

## Things that don't add up:

- L14 with the Ryzen 5 Pro 4650U didn't ship with the 128 gb sdd
- And as far as I can tell, the L14 with the 128 gb sdd was never sold in North America
- The 45w power supply was on the Latin American Model -- which has a FHD 1920x1080p screen resolution

[link to lenovo site with stats](https://psref.lenovo.com/Product/ThinkPad/ThinkPad_L14_Gen_1_AMD?MT=20U6)

\pagebreak

# Hardware Specs

`cat /sys/devices/virtual/dmi/id/board_{vendor,name,version}` #<- Lists your motherboard details.

`lspci -Q` #<- Lists all your internal hardware and checks online for missing/updated names.

`lspci -v | grep "VGA controller"` #<- Displays your currently active graphics card. Very useful on laptops with hybrid/switchable graphics. (Typically this is the integrated card unless you have configured it otherwise)

`lspci -v | grep "3D controller"` #<- Displays your Nvidia Dedicated GPU. For laptops with hybrid/switchable graphics.

`lspci -v | grep "Display controller"` #<- Displays your ATI/AMD Dedicated GPU. For laptops with hybrid/switchable graphics.

`lsusb` #<- Lists all your USB hardware.

`lscpu` #<- Lists detailed processor info (alternative: cat /proc/cpuinfo )

`lshw`` #<- A combination of lspci and lscpu, also displays total RAM.

`fdisk -l` #<- Lists your hard drives and partitions (may requires sudo access).

`free -h --si` #<- Lists your memory information, total is your total, available is your total free memory.

`cat /proc/meminfo` #<- Much more detailed hardware info on your memory

`ip link` #<- lists your network devices and their status

`cat /proc/kmsg | grep Error` #<-Lists errors detected by the kernel (often hardware related ones), probably requires sudo access.

## Memory Test

`memtester 1024 5` #<- Sets aside 1GB(1024MB) free memory, and runs tests on it 5 times, then displays results.

## Battery

`acpi -ib` #<-Lists battery status, basic specs and gives an idea of it's health (shows it's charge level last time it was "full")

`upower -i /org/freedesktop/UPower/devices/battery_BAT0` #<- Should provide detailed battery information.

## CPU \& GPU

`hardinfo` (A GUI utility that lists detailed info about all your system specs and has benchmark capabilities, very handy!)

`sysbench` # Command-line benchmarking tool for cpu, memory and hdd among others, []guide here](https://www.howtoforge.com/how-to-benchmark-your-system-cpu-file-io-mysql-with-sysbench)

`sysbench --test=cpu --cpu-max-prime=20000 run` # does a simple prime number test. The Manjo21 PC got a score of total time: 10.0011 and number of events: 8189



