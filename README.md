### Rotor utility

To compile
```
 sudo make
```
Help
```
./rotor-control --help
```

Move to 89W
```
./rotor-control -T 3860,H,30000,56,s2,8psk,35 -m2 -n 19
```
help
```
Usage: rotor-control [options] 
         turn USALS sat polar-rotor to calculated position or in stored in it position

         Options:
          -m n        : set [m]odus (default -m1)
                        -m0 - just calculate and print antenn alignment angles
                        -m1 - USALS 
                        -m2 - GotoNN 
                        -m3 - turn rotor to set by -A NN option angle 

          -a N        : set [a]dapter N (default -a0)
          -f N        : set [f]rontend N (default -f0)
          -V 0|13|18  : set LNB [V]oltage to OFF, 13 or 18 Volts (default -V18)
          -O 0|1      : set LNB power supply in 0=normal/1=[O]vervoltage mode (add about +1 Volt) (default -O0)
          -d N        : set [d]iSEqC switch at input N (0=no_switch 1=A/A, 2=A/B, 3=B/A, 4=B/B) (default -d0)

          -D NN       : set [D]elay NN msec before send any rotor DiSEqC master command (default -D1000 e.g. 1 second)
                        Polar-rotor need to have time initialised after power up. Must be > 800 msec for SG-2100

          -X DD.MM    : USALS: rotor location Longitude, XX=degrees MM=minutes, minus sign for East  (default -X -30.20)
          -Y DD.MM    : USALS: rotor location Latitude,  XX=degrees MM=minutes, minus sign for South (default -Y 59.51)
          -s DD.dd    : USALS: [s]at Longitude in degrees, minus sign for East (default -s -19.20) (-s0 = no send USALS command) 

          -n NN       : GotoNN: drive to stored in rotor position memory cell [n]umber NN (default -n5) (-n0 = no send gotoNN command)

          -A NN       : set rotor [a]ngle NN degrees, minus sign for East (default -A00 = drive to zero rotor direction 

          -t NN       : set [t]imeout NN seconds while LNB voltage is up after send USALS or GotoNN command (default -t30)

          -e NN       : STEPS: drive rotor NN steps to [e]ast (NN = 0...127 steps) (default -e0 = no send steps command)
          -w NN       : STEPS: drive rotor NN steps to [w]est (NN = 0...127 steps) (default -w0 = no send steps command)
          -L NN       : STEPS: rotor speed parameter for calculate delay while LNB voltage is up after send STEPS command
                               - for rotor SG2100 NN=15 - you can set it by '-L 15'
                               - default for slow rotor -L2

          -R N        : [R]epeat all DISEQC master command N times (default -R1)

          -S NN       : [S]tore current rotor position in rotor memory cell NN (default -S0 = no store)

          -T freq,pol,sr,fec,delsys,modulation,rolloff : check [T]ransponder for LOCK (ONLY DVB-S transponders)
                                        (freq = frequences MHz, pol = polarization H|V, sr = Symbol rate kHz
                                        fec  0|12|23|34|45|56|67|78|89|35|910, (0=AUTO only for DVB-S)
                                        delsys 0|s1|s2 (DVB-S, DVB-S2) (0 = DVB-S)
                                        modulation  0|qpsk|8psk (0 = QPSK)
                                        rolloff 0|20|25|35 (0 = 35)
                                        so for check DVB-S 11642 H 27500 = -T 11642,H,27500,0,0,0,0
                                        for check DVB-S2 8psk 12169 V 27500 3/4 = -T 12169,V,27500,34,s2,8psk,35

          -W 0|1      : rotor angle s[W]eeper (default 0=no) only for modus 1 and 3 and if set transponder -T
          -?/h        : this help

```
