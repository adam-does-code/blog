+++
title = "Building a clock" 
tags = ["arduino"]
date = "2020-11-23"
+++

## A clock? 

I was bored one day and I randomly remembered that I own a bunch of arduino stuff and modules that I can play around and build with. I wasn't sure what to build but then I realized that to be aware of the time can help when i'm working and generally can benefit from having a clock hung around my room. 

Apart of the arduino kit that I got was a 4 digit 7-segment display, which screamed to me CLOCK? ALARM CLOCK? It's been a while since i've worked with all this stuff and I still consider myself a huge beginner so I broke out a few tutorials to see how it works. 

After I got the basics of how to hook up the display, and learning about the cathod and anodes of it. I did a few voltage? power? calculations to see how much resisting I need. 

My code currently looked like: 

```
#include "SevSeg.h"

SevSeg sevseg; 

void setup(){

  byte numDigits = 4;
  byte digitPins[] = {10, 11, 12, 13};
  byte segmentPins[] = {9, 2, 3, 5, 6, 8, 7, 4};
  bool resistorsOnSegments = true; 
  bool updateWithDelaysIn = true;
  byte hardwareConfig = COMMON_CATHODE; 
  
  sevseg.begin(hardwareConfig, numDigits, digitPins, segmentPins, resistorsOnSegments);
  sevseg.setBrightness(90);
}

void loop(){

    sevseg.setNumber(result, -1);
    sevseg.refreshDisplay(); 
}
```

Basically I connected the pins to the specific digital pins, this part is a little confusing for me since im not too sure what the difference between digitPins and segmentPins are (time to learn something!). After that we used the SevSeg library (which to me reminded me of segmentation faults). Setting the number could be any 4 digit number since we only have 4 digits to display, and then the second parameter to the `sevseg.setNumber()` function is where the decimal point can be. I put -1 since we dont need a decimal point for our clock! 


