# Forensics
- Challenge Name : OakvilleTownMystery
- Difficulty :  Medium

## Challenge Description
On March 27, 2023, a golden sceptre was taken from Oakville Town Hall. Suspect Johannes Trithemius has been taken into custody by Detective Jameson. Jameson believes he is the town's fugitive thief's right-hand man. Jameson was able to retrieve one image that he thinks contains details about the vehicle the thief fled in, even though Johannes had erased all digital traces from the device. There are four intertown highways in Oakville, and they are constantly closely watched. The database contains all the data on the roads as well as the data on the residents of the towns. Find the thief and town name he escaped to. Watch out for Johannes, a cunning con artist who frequently knows how to trick the police.

---------

#### Flag format: VishwaCTF{FirstNameLastNameTown}

#### Assets/files : [image.jpg](https://klsgit-wgcs.github.io/VishwaCTF-2023/writeups/Forensics/image.jpg), [database.db](https://klsgit-wgcs.github.io/VishwaCTF-2023/writeups/Forensics/database.db) 

---------

## Methodology
After reading the description we first looked at the image and it seemed like a picture of a CCTV grab. The license plate of the car was clearly visible. The database file attached, had around 6 tables with huge amount of data. The tables were:

> people, town_code, traffic_cam1, traffic_cam2, traffic_cam3, traffic_cam4

There were fields like license plates, and highway vehicular movement records in the cam footage tables. At first we directly plugged in the license number from the image into an SQL query :

> SELECT * FROM people WHERE license_plate="WB-0420";

This fetched :

> 510	Johannes True	892-627-1275	WB-0420

However he was not the culprit.

Then we took a better look at the image, which revealed some timestamps and date at the bottom right corner in red. The traffic cam tables had timestamp columns, so plugging in the values obtained from the image into a query :

> SELECT * FROM traffic_cam3 WHERE year=2023 AND month=3 AND day=27 AND hour=21 AND minute=45;

This fetched a single record :

> 715	SW	2023	3	27	21	45	OV-007

SW was the town code and OV-007 was the escape vehicle. Cross referencing with other tables with SELECT statements the culprit was Wellington East and he tried escaping to Springwood as indicated by SW. Justice is served !! 

The flag was :

> vishwaCTF{WellingtonEastSpringwood}

And it was correct !! This is an example where it shows the importance of attention to detail, and going over the given materials carefully before proceeding. Remember that these little details are almost always hidden in plain sight...
