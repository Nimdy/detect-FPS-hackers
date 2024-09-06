# How to detect FPS hackers in any game with Elastic Search or Splunk 

Executive Summary:

FPS games are pretty much unplayable and dead because of the amount of script kiddies using software/hardware hacks. This write-up presents a solution to detect FPS hackers using Elastic Search or Splunk, coupled with machine learning (ML) and artificial intelligence (AI) technology. The core idea is to collect player and weapon data to establish normal gameplay baselines. By analyzing metrics like average kill range, player accuracy, target box locations hit, and player reports, we can identify cheaters whose stats fall way outside these baselines.

This system uses cloud-based storage and processing, with DynamoDB recommended for its scalability and performance. It's designed to overcome the challenges of traditional anti-cheat methods by making it harder for cheaters to bypass and adapting to new hacking techniques. The approach accounts for different skill levels, from below average to God-like, ensuring legit skilled players aren't falsely flagged. Implementing this system could help gaming companies like Riot Games, Infinity Ward, and others to combat cheating effectively, potentially reviving the FPS genre and improving player satisfaction.

My plan here is find others in the community that know how to use Elastic and/or other products to build something ourselfs and give a solution to companies like:
```
Riot Games, Infinity Ward, Treyarch, Digital Illusions CE, Ubisoft, EA, Bungie, Raven Software, Blizzard Entertainment, Activision...etc.
```
First Person Shooters(FPS) are pretty much unplayable and dead because of the amount of script kiddies using software/hardware hacks in pretty much every game.  Software and Hardware hacks are pretty freaking easy to use and close to impossible to keep up with. Companies need to change the way they are trying to detect cheaters and implement machine learning(ML) and artificial intelligence(AI) technology. 

Over coming these challenges today is very easy and a simple solution coupled with the collection player and weapon data could be the answer.  This data can be used to deterime normal game play baselines.  As data is being collected, a company will need to define baselines from trend analysis. Trend analysis is the process of comparing collected data over time to identify any consistent trends. 

These trends will help identify acceptable levels and if any event scores outside the trend will trigger a review for suspected cheating.

Using machine learning (ML) and artificial intelligence (AI) technology to detect cheaters in first-person shooter (FPS) games can be an effective way to combat the issue of script kiddies using software and hardware hacks. One solution is to collect player and weapon data, which can be used to establish normal game play baselines. 

By analyzing this data over time, trends can be identified that can help detect suspicious behavior. However, it is important to note that implementing such a system would require a significant amount of data and resources, as well as careful planning and execution to ensure accuracy and fairness. Additionally, companies would need to invest in data collection and analysis tools, as well as the necessary infrastructure to support them.  

The examples below are low level design but can scale into all types of elaborate data processing.

*Additional data concepts found at bottom of write-up*

Example idea of baseline data charting:
```
Average Kill Range: Player range + target range + weapon range
Average Player Accuracy (Hit any location on Target Box)
Average Target Box Locations Hit (Head, Body, Limbs)
Player Reported for cheating
```

These are examples of metrics that could be used to establish a baseline for normal game play. By charting the average kill range, player accuracy, and target box locations hit, a company could identify patterns and trends that could help detect suspicious behavior. 

Tracking the number of players who are reported for cheating could also be used as an indicator of potential cheating. 

However, it's important to note that these metrics alone may not be enough to definitively identify cheaters and would likely need to be used in combination with other data and analysis techniques.


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

These are examples of additional metrics that could be used to establish a baseline for normal game play, and detect potential cheating.

By tracking data such as player distance to target hit (PDTH), player distance to target hit with weapon (PDTHW), player target time to kill distance (PTTKD), player target time to kill distance with reports (PTTKDR), player target time to kill hitbox hit location (PTTKHHL) and other metrics like weapon distance hit, weapon distance kill, weapon hitbox hit location, weapon time to kill and weapon accuracy, a company could gain a more complete picture of player behavior and identify patterns and trends that could indicate cheating. 

Additionally, tracking data such as account age, skill trend, total time played, and times reported could also be used as an indicator of potential cheating.

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
The initial process of collecting the baseline data would require significant resources, including the infrastructure to collect and store the data, as well as the personnel to perform the analysis and establish the baselines. 

However, once the initial baselines have been established, it would not require as many resources to maintain and update the system, as it would only need to process the new data that is collected and compare it to the established baselines. However, resources would still be required to maintain the system, including the infrastructure to collect, store and analyze the data, as well as personnel to perform monitoring, troubleshoot and fine-tune the system.

Creating different tiers of baselines based on player skill is a good approach to detecting cheating. By establishing separate baselines for different skill levels, the system can account for the fact that different players may have different abilities and playstyles. This allows the system to be more accurate, as it can compare a player's statistics to those of other players with similar skill levels, rather than comparing them to a single set of baselines that may not be representative of the player's skill level. This can help to reduce the number of false positives and ensure that the system is fair and unbiased.




## So how do we get companies there?

There are a few different ways that a company could collect the initial data needed to establish baselines for normal game play:

In-game data collection: The company could collect data directly from the game, such as player statistics and gameplay metrics, using built-in data collection tools. This approach would provide a large amount of data from a variety of players and would be relatively easy to implement.

Surveys and player feedback: The company could also collect data from players through surveys or other forms of feedback. This approach would allow players to provide information about their skill level and gameplay habits, which could be used to establish baselines for different skill levels.

Community data: Companies could also collect data from the game communities, such as forums, social media, and other platforms where players discuss the game and share information. This would allow companies to have a large sample of players' data and get insights into the game play, skill level and players preferences.

External data: Companies could also purchase or collect external data such as player demographics and statistics from third-party data providers.

It would be best to use a combination of these methods to get a more complete and accurate view of player behavior and establish accurate baselines.

## Storing the data

The data collected from the game, player surveys, community feedback, and external data sources would need to be stored in a format that is easily accessible and can be easily analyzed. Some common formats for storing data include:

1. Relational databases: Data can be stored in a relational database such as MySQL, SQL Server, or PostgreSQL. Relational databases use tables to organize data and support advanced querying and indexing, making them well-suited for storing large amounts of structured data.

2. NoSQL databases: Data can also be stored in a NoSQL database such as MongoDB, Cassandra, or Amazon DynamoDB. These databases are designed for storing and querying large amounts of unstructured data, and are well-suited for data with a high degree of variability.

3. Flat files: Data can also be stored in flat files such as CSV or JSON. This approach is simple and easy to implement, but may not be as efficient as a relational or NoSQL database when it comes to querying and indexing large amounts of data.

4. Cloud storage: Data can also be stored in cloud storage such as Amazon S3, Google Cloud Storage, or Microsoft Azure Blob Storage. This approach would allow for easy scalability and access to the data from any location.

Which format is chosen will depend on the specific requirements of the data and the analysis that will be done on it. It's also important to consider the security of the data, the ability to scale the data storage and the ability to access the data easily.


I believe DynamoDB is the best choice for storing and processing.

DynamoDB is a NoSQL database service offered by Amazon Web Services (AWS) that can be an effective choice for storing and querying large amounts of game data. Here are a few reasons why DynamoDB may be the best option:

1. Scalability: DynamoDB is designed to automatically handle the scaling of data storage and throughput as needed. This means that as the amount of data grows, the service can automatically add more capacity to handle it, making it well-suited for storing large amounts of data.

2. Performance: DynamoDB is optimized for performance, with low latency and high throughput. This makes it well-suited for real-time data processing and analysis, which is important for detecting cheating in online games.

3. Flexibility: DynamoDB allows for flexible data modeling, with support for both structured and unstructured data. This makes it well-suited for storing data with a high degree of variability, such as game data.

4. Cost-effectiveness: DynamoDB is a pay-per-use service, which means that companies only pay for the resources they use. This can be a cost-effective option, especially for companies that have variable or unpredictable data storage and processing needs.

5. Integration: DynamoDB can be easily integrated with other AWS services, such as AWS Lambda, Amazon Kinesis, and Amazon S3, which allows for further data processing and analysis.

6. Accessibility: DynamoDB can be accessed from anywhere, which means that data can be easily queried, analyzed and visualized from any location.

It's important to note that there are other NoSQL databases available, such as MongoDB, Cassandra, and others that may be suitable for the same use case. However, DynamoDB is a fully managed service, which means that it abstracts away many of the operational complexities of running a NoSQL database, making it a highly available, scalable and low-latency option.


## DynamoDB Example

A DynamoDB table structure for storing game data might look like the following example:

Table Name: GameData

Primary Key:

- GameID (String)
- Timestamp (Number)


Attributes:

- PlayerID (String)
- PlayerName (String)
- PlayerRank (String)
- WeaponName (String)
- KillDistance (Number)
- Accuracy (Number)
- HitboxLocation (String)
- Reports (Number)

In this example, the GameData table has a primary key made up of two attributes: GameID and Timestamp. The GameID attribute is used to identify the game and the Timestamp attribute is used to identify the time the data was collected. The table also includes various attributes such as PlayerID, PlayerName, PlayerRank, WeaponName, KillDistance, Accuracy, HitboxLocation and Reports. These attributes are used to store the data collected from the game, such as the player's ID, name, rank, weapon used, distance of kill, accuracy, hitbox location, and number of reports.

This is just a simple example, in practice the table structure and attributes could vary depending on the data that needs to be collected and the analysis that will be done on it. Additionally, it's important to add secondary indexes to the table to optimize query and access patterns, and also to include a partition key to spread the data across multiple partitions for better performance.


## DynamoDB and algorithm for ML

Here's an example of an algorithm that could be used to analyze the game data stored in the DynamoDB table structure provided in the previous answer:

1. Retrieve data from the GameData table using the primary key (GameID and Timestamp) and any additional filters (PlayerRank, WeaponName, etc)
2. Group the data by PlayerID and calculate the average values for each metric (KillDistance, Accuracy, HitboxLocation, Reports)
3. Compare the calculated averages to the established baselines for each skill level.
4. For each player, if any metric is outside of the established baselines, flag the player as a potential cheater and add them to a review queue.
5. Review the flagged players' data manually to confirm if they are actually cheating or not.

This algorithm is based on the idea of anomaly detection, which is a common approach used in machine learning to identify patterns or behaviors that deviate from the norm. By comparing the players' data to the established baselines, the algorithm can identify any players whose data is significantly different from what is considered normal, which can indicate cheating.

A algorithm example would be like this:

1. KillDistance:
- Sum of all the KillDistance values for each player: Sum(Player_i.KillDistance)
- Average KillDistance per player: Sum(Player_i.KillDistance) / Count(Player_i.Kills)

2. Accuracy:
- Sum of all the number of successful hits for each player: Sum(Player_i.Hits)
- Average Accuracy per player: Sum(Player_i.Hits) / Count(Player_i.Shots)

3. HitboxLocation:
- Sum of all the number of head shots for each player: Sum(Player_i.Headshots)
- Average HitboxLocation per player: Sum(Player_i.Headshots) / Count(Player_i.Kills)

4. Reports:
- Sum of all the number of reports for each player: Sum(Player_i.Reports)
- Average Reports per player: Sum(Player_i.Reports) / Count(Player_i.Games)

I suck at math but these equations are simple and the actual calculations will depend on the specific data that is being collected and the analysis that needs to be done on it. It's important to consider the whole data set and not just one player, as the algorithm is meant to establish baselines and compare them to the data from all players.


## Here's an example of how a cheating player's stats might differ from a non-cheating player's stats:

Cheating player:

- KillDistance: 200 meters (average)
- Accuracy: 90% (average)
- HitboxLocation: Headshots: 80% (average)
- Reports: 2 (average)

Non-cheating player:

- KillDistance: 100 meters (average)
- Accuracy: 60% (average)
- HitboxLocation: Headshots: 50% (average)
- Reports: 0 (average)

The cheating player has significantly higher averages for KillDistance and Accuracy, and a higher percentage of headshots, compared to the non-cheating player. Additionally, the cheating player has more reports than the non-cheating player. These stats would be flagged as anomalous, and if they are consistent across a significant number of rounds, the player would be marked as a potential cheater and would be reviewed manually.

This example is based on assumptions, and a real-world scenario would require a lot of data and a lot of players to establish a clear baseline but if Call of Duty was doing this from day one... I would not be here writing this all out.

It's also important to note that not all players who deviate from the established baselines will be cheating and some legitimate players may have unique playing styles or strategies that account for the differences in their stats.

Example a god-like non-cheating player:

Non-cheating god-like player:

- KillDistance: 150 meters (average)
- Accuracy: 85% (average)
- HitboxLocation: Headshots: 75% (average)
- Reports: 0 (average)

A god-like player is assumed to have exceptional skills and they tend to have higher averages than non-cheating players in terms of kill distance and accuracy, and a higher percentage of headshots due to their aiming and aiming skills. Their stats would still fall within the established baselines for their skill level and would not be flagged as anomalous or potential cheating. It's important to note that legitimate players may have unique playing styles or strategies that account for the differences in their stats and don't necessarily indicate cheating.

## Determining a player's play style

To determine a non-cheating player's play style based on the metrics, you could analyze the following characteristics:

- Times a player jumps: A player's jumping frequency can provide insight into their play style. For example, a player who frequently jumps may have a more aggressive play style, while a player who rarely jumps may have a more defensive play style.
- Routes the player commonly takes on the map: A player's common routes can provide insight into their play style. For example, a player who consistently takes a specific route may have a more aggressive play style, while a player who frequently changes routes may have a more defensive play style.
- Reloading characteristics: A player's reloading habits can provide insight into their play style. For example, a player who frequently reloads may have a more cautious play style, while a player who rarely reloads may have a more aggressive play style.
- Weapon swapping characteristics: A player's weapon swapping habits can provide insight into their play style. For example, a player who frequently swaps weapons may have a more versatile play style, while a player who consistently uses the same weapon may have a more specialized play style.
- Movement speed: A player's movement speed can provide insight into their play style. For example, a player who moves quickly may have a more aggressive play style, while a player who moves slowly may have a more defensive play style.
- Aiming patterns: A player's aiming patterns can provide insight into their play style. For example, a player who consistently aims for headshots may have a more aggressive play style, while a player who consistently aims for body shots may have a more defensive play style.
- Peek timings: A player's peek timings can provide insight into their play style. For example, a player who frequently peeks may have a more aggressive play style, while a player who rarely peeks may have a more defensive play style.
- Cover usage: A player's cover usage can provide insight into their play style. For example, a player who frequently uses cover may have a more defensive play style, while a player who rarely uses cover may have a more aggressive play style.


Comparing metric data is one of the most effective ways to detect cheaters in online video games because cheating software has become so advanced. Cheating software can be used to manipulate many aspects of the game, including aim assist, no recoil, wall hacks, and many others. These cheats can make it difficult to detect cheaters using traditional methods, such as scanning for specific software or hardware on a player's device.

This is why I believe comparing data is the most effective way to detect cheaters by identifing patterns and anomalies that are indicative of cheating.



Happy gaming,

ZeroBandwidth
