# How to detect FPS hackers in any game with Elastic Search or Splunk 

My plan here is find others in the community that know how to use Elastic and/or other products to build something ourselfs and give a solution to companies like:
```
Riot Games, Infinity Ward, Treyarch, Digital Illusions CE, Ubisoft, EA, Bungie, Raven Software, Blizzard Entertainment, Activision...etc.
```
First Person Shooters(FPS) are pretty much unplayable and dead because of the amount of script kiddies using software/hardware hacks in pretty much every game.  Software and Hardware hacks are pretty freaking easy to use and close to impossible to keep up with. Companies need to change the way they are trying to detect cheaters and implement machine learning(ML) and artificial intelligence(AI) technology. 

Over coming these challenges today is very easy and a simple solution coupled with the collection player and weapon data is the answer.  This data can be used to deterime normal game play baselines.  As data is being collected, a company will need to define baselines from trend analysis. Trend analysis is the process of comparing collected data over time to identify any consistent trends. These trends will help identify acceptable levels and any event scoring outside the trend will trigger a review for suspected cheating.

This is how I would fix the overall cheating found in FPS games today with ML/AI through Elastic Search.

First we need a data set and I have had zero luck so far getting sample data from any company. I believe none of these companies are programming meta data collection metrics in their games at the correct level needed to detect cheaters. Well, correction they are but I believe the focus is in the wrong area (hardware/memory scans for IOC | hashes). 

Everything below is doable and needs to be scripted for meta data collection.  This will not require a lot of disk space... its meta data. The resources doing all the work will need testing and optimization.   

The examples below are low level design but can scale into all types of elaborate data processing.

*Additional data concepts found at bottom of write-up*

Example idea of baseline data charting:
```
Average Kill Range: Player range + target range + weapon range
Average Player Accuracy (Hit any location on Target Box)
Average Target Box Locations Hit (Head, Body, Limbs)
Player Reported for cheating
```

Let’s say only three guns are used in a game.
```
Big Gun - Long Range
Medium Gun - Medium Range
Small Gun - Close Range
```
Break down example of baseline player data:
(Skill is determined by Player Ranking by whatever scoring method)
```
10% of the Players have God-like skill
30% of the Players have Advance skill
40% of the Players have Average skill
20% of the Players have Below Average skill
```
Break down examples of baseline weapon data.

Average Big Gun Data:
```
The average distance of Player + target + kill = 100 meters
The average accuracy is 50%
The average target box locations hit: Head: 50% Body: 40% Limbs: 10
```
Average Medium Gun Data:
```
The average distance of Player + target + kill = 50 meters
The average accuracy is 40%
The average target box locations hit: Head: 30% Body: 60% Limbs: 10
```
Average Small Gun Data:
```
The average distance of Player + target + kill = 10 meters
The average accuracy is 80%
The average target box locations hit: Head: 20% Body: 60% Limbs: 20
```
Example of how cheating would be identified with Machine Learning(ML) and Artificial Intelligence(AI)

Let’s say the average God-like skilled players weapon stats are as follows:

Big Gun Data:
```
The average distance of Player + target + kill = 150 meters
The average accuracy is 75%
The average target box locations hit: Head: 70% Body: 30% Limbs: <1%
```
Medium Gun Data:
```
The average distance of Player + target + kill = 75 meters
The average accuracy is 80%
The average target box locations hit: Head: 40% Body: 60% Limbs: <1%
```
Small Gun Data:
```
The average distance of Player + target + kill = 25 meters
The average accuracy is 90%
The average target box locations hit: Head: 40% Body: 60% Limbs: <1%
```
Now if any player stats trigger outside the trend baseline - then flag for possible cheating and review

Let’s say the cheater stats are:

Big Gun Data:
```
The average distance of Player + target + kill = 300 meters
The average accuracy is 95%
The average target box locations hit: Head: 80% Body: 20% Limbs: <1%
```
Medium Gun Data:
```
The average distance of Player + target + kill = 175 meters
The average accuracy is 80%
The average target box locations hit: Head: 60% Body: 40% Limbs: <1%
```
Small Gun Data:
```
The average distance of Player + target + kill = 75 meters
The average accuracy is 90%
The average target box locations hit: Head: 40% Body: 60% Limbs: <1%
```
The cheater stats are way outside of the average baseline data collected.

Additional examples of detection are:
```
Player + Target + Time to Kill + Distance
Player + Target + Time to Kill + Distance + Reports
Player + Target + Time to Kill + Hitbox Hit Locations
```
Companies cry out saying they do not have the resources to watch every player and respond to every report, coupled with the validation process.

OKAY GREAT!  Now let the ML and AI identify these for the company and it will limit the resources required for validation. 
If you took the baseline trend data + the player data + reported data, then you will have a more surgical process for identifying cheaters from a game.

Elastic can do this pretty damn easily...

If I can find hackers in a network after digging through petabytes of PCAP data without ML or AI, then I know this can be completed. 


If somebody says:
So what if this works, script kiddies will still use hacks and lower the ML/AI cheating software to the averages, still maintaining a edge. 

I would say:
This would be a good thing because lowering the ML/AI cheat software to the trends would not ruin the game. This is because the players not using cheats would at least have a better chance at over coming the cheaters. Since nobody is doing this already, we dont know what the outcome would be... So I am guessing, it would just lower the amount of cheaters out there because at this point it just would not be worth it. This coupled with the fact companies are using this for detection, would also become a deterrent.

```
Detect hackers in Warzone

Detect hackers in Battlefield

Detect hackers in Fortnite 

Detect hackers in Valorant

Detect hackers in PUBG

```

Types of meta data needed in logs: (thinking up of more data points for collection and of course these metrics need to be programmed into the game)

```
Average PDTH    (Player + Distance to Target Hit)
Average PDTHW   (Player + Distance to Target Hit + Weapon)
 
Average PTTKD   (Player + Target + Time to Kill + Distance)
Average PTTKDR  (Player + Target + Time to Kill + Distance + Reports)
Average PTTKHHL (Player + Target + Time to Kill + Hitbox Hit Location)

Average Weapon Distance Hit
Average Weapon Distance Kill
Average Weapon Hitbox Hit Location

Average Weapon Distance Hit + Hit Box Location Hit
Average Weapon Distance Kill + Hit Box Location Hit

Average Weapon Time to Kill
Average Weapon Accuracy

Account Age
Account Skill Trend
Account Total Time Played
Account Times Reported
```
IDK... Just trying to spark conversation for people way smarter than I am to help me design and define a new standard in identifing cheaters in any game. 

I believe if you ever want to stand a chance in defeating cheaters that are using ML/AI, you need to fight back with ML/AI detection methods.

Maybe nothing will ever happen because people keep making purchases in the stores for DAT NEXT SICK SKIN... lol

Happy gaming,

ZeroBandwidth
