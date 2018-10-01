May,26, 2014, Peja, Kosovo
by Toma

This is a fully functional configuration file for Linuxcnc to be used
 with any and all of the "simple THC" systems on sale, like:
Proma Elektronika Compact THC (tested and verified)
 All that output "UP""DOWN""ARCOK" signals even those that normaly use 2 parallel ports
 if you can manage the changes in wiring and change the pins in the config files.

This setup is configured with slightly relaxed timings so can be used even on older systems
 and systems with lattency problems. It is based on the "thc_300" config found bundeled 
 with Linuxcnc but it is heavily modified since in it's original form it does not work.

Before you start, be sure to check the "parport addres" and the output pins for motor
 drivesin the "thc_parport.hal" file, then change the pins in the "thc.hal" file to match
 the "UP""DOWN"ARCOK""TORCH ON" signals. You need to check for positive or negative input
 signals and change that too.
 
Also you need to change the "scale" "velocity" and "acceleration" in "Axes Section" in 
 the "thc_toma.ini" file to mach your setup.

For "scale" i use "40" since i have full step drives connected to 200 step/rev 
 (1.8 degre/step) motors attached to 5mm/rev ballscrews. This is simple 
 math: steps per rev/mm per rev, in my case 200/50=40.

For "velocity" use anything between 30 and 100 that your setup can handle without
 loosing steps or stalling. The value is mm per second so 30 is 1800mm/minute 
 and 100 is 6000mm/minute.
 FYI do this for each AXIS separatly or just use a value that is below the maximum 
 your setup can handle to be on the safe side. For actual cutting on a plasma the 
 maximum usable speed is about 4200mm/minute for cutting a 1mm thick mild steel plate,
 in this case that would be a value of 70 for "velocity".

For "acceleration", again depending on your setup, put 100 to 500, that is mm/s squared,
 but for geting sharp corners you need at least 300 if cutting under 3mm thick 
 plates, 200 for 4 to 6mm thick plates and 100 if cutting anything over 10mm. But if 
 your setup can handle 300 and above just leave it there, do not change this.

This config also remembers last machine position so if the machine is not moved while 
 powered off, you can continue from where it left. This is done since where i live 
 power outs are a normal occurence.
