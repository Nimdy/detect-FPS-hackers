# How to detect FPS hackers in any game with Elastic Search or Splunk 

(Cleaning up write - everything below is data collection points for anomaly detection models - @valkmit thanks for the input - DISCLAIMER: I am not a expert in ML/AL but I do have a few years of anomaly detection using ML within Elastic. I am on the thought process of "If I can apply the same concepts to gaming as I can do with cyber, then maybe it could work")

My plan here is find others in the community that know how to use Elastic and/or other products to build something ourselfs and give a solution to companies like:
```
Riot Games, Infinity Ward, Treyarch, Digital Illusions CE, Ubisoft, EA, Bungie, Raven Software, Blizzard Entertainment, Activision...etc.
```
First Person Shooters(FPS) are pretty much unplayable and dead because of the amount of script kiddies using software/hardware hacks in pretty much every game.  Software and Hardware hacks are pretty freaking easy to use and close to impossible to keep up with. Companies need to change the way they are trying to detect cheaters and implement machine learning(ML) and artificial intelligence(AI) technology. 

Over coming these challenges today is very easy and a simple solution coupled with the collection player and weapon data could be the answer.  This data can be used to deterime normal game play baselines.  As data is being collected, a company will need to define baselines from trend analysis. Trend analysis is the process of comparing collected data over time to identify any consistent trends. These trends will help identify acceptable levels and if any event scores outside the trend will trigger a review for suspected cheating.


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
Example of how cheating would be identified with Machine Learning(ML) through anomaly detection models. 

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

Again, my experience with ML is with only using anomaly detection models.  

If you want to better understand my mindset and why I think this would work, take a look at https://www.elastic.co/guide/en/machine-learning/current/anomaly-examples.html

Some examples with Elastic. https://www.youtube.com/watch?v=wPd_JWWfre4

Figured if we can get the meta data for the examples listed above, then we can play around with it and get it working within Elastic.

I know there is all types of ML/AI uses and the majority of them are out side of my experience but I am always willing to learn from fellow nerds.

Happy gaming,

ZeroBandwidth
