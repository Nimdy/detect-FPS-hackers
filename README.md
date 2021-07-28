# How to detect FPS hackers in any game with Elastic 

My plan here is find others in the community that know how to use Elastic and/or other products to build something ourselfs and give a solution to companies like:
```
Riot Games, Infinity Ward, Treyarch, Digital Illusions CE, Ubisoft, EA, Bungie, Raven Software, Blizzard Entertainment, Activision...etc.
```
FPS are dead because of hackers and nobody can seem to figure it out? BS. Companies need to change the way they are trying to detect cheaters… Software and Hardware hacks are pretty freaking easy to use and close to impossible to keep up with. 

This is how I would fix the overall cheating found in FPS games today. 

Over coming these challenges today will be very easy and a simple solution that starts with the collection player and weapon data.  This data can be used to deterime normal game play baselines.  As data is being collected, a company will need to define baselines based off trend analysis. Trend analysis is the process of comparing collected data over time to identify any consistent trends. These trends will help identify acceptable levels and any event scoring outside the trend will trigger a review for suspected cheating.

Example idea of baseline data charting:
```
Average Kill Range: Player range + target range + weapon range
Average Player Accuracy (Hit any location on Target Box)
Average Target Box Locations Hit (Head, Body, Limbs)
Player Reported for cheating
```
Example of how this works with small numbers.

Let’s say there are only three guns 
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

Big Gun Data:
```
The average distance of Player + target + kill = 100 meters
The average accuracy is 50%
The average target box locations hit: Head: 50% Body: 40% Limbs: 10
```
Medium Gun Data:
```
The average distance of Player + target + kill = 50 meters
The average accuracy is 40%
The average target box locations hit: Head: 30% Body: 60% Limbs: 10
```
Small Gun Data:
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
Now if any player stats reflect way outside the normal - then flag for possible cheating and review

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

Hear me out… This was just a simple low level example of data comparison and can become very complex in the different mathematical formulas used to build out different trend models.

Additional examples of detection are:
```
Player + Target + Time to Kill + Distance
Player + Target + Time to Kill + Distance + Reports
Player + Target + Time to Kill + Hitbox Hit Locations
```
Companies cry out saying they do not have the resources to watch every player and respond to every report, coupled with the validation process.

OKAY GREAT!  Now let the ML and AI identify these for the company and it will limit the resources required for validation. If you took the baseline data + the player reported data, then you will have a more surgical process for identifying cheaters from a game.

Elastic can do this pretty damn easily...

If I can find hackers in a network after digging through petabytes of PCAP data without ML or AI, then I know this can be completed. 

IDK... Just trying to spark conversation for people way smarter than I am to design Elastic ML cookbooks...

Or nothing will ever happen because companies only shadow ban people and loot boxes are still being purchased... lol

Detect hackers in Warzone
Detect hackers in Battlefield
Detect hackers in Fortnite 
Detect hackers in Valorant
Detect hackers in PUBG

