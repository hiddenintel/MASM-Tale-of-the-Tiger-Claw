# MASM-Tale-of-the-Tiger-Claw
This is a fairly large program that is similar to the old "Choose Your Own Adventure" books, telling the story of a battle ship in space.


TITLE MASM Template						(main.asm)

INCLUDE Irvine32.inc

.data

;TESTING TOOLS
nineTest byte "Quarters Unlocked" ,0ah,0dh,0
hangarTest byte "Hanger has been unlocked",0ah,0dh,0
TestingM3 byte "Start of Mission 3",0ah,0dh,0
Room17Test byte "Testing Room 17" ,0ah,0dh,0
Room18Test byte "Testing Room 18" ,0ah,0dh,0
testRoom20 byte "Testing Room 20" ,0ah,0dh,0
testCapRoom byte "Testing Room 26" ,0ah,0dh,0
AlexEncounterTest byte "Testing Room 27",0ah,0dh,0
RegCapRoomTest byte "Testing Room 28",0ah,0dh,0
testPQOne byte "Testing first entry to quarters",0ah,0dh,0
testPQTwo byte "Testing second entry to quarters",0ah,0dh,0
test30 byte "Testing room 30",0ah,0dh,0
test31 byte "Testing room 31",0ah,0dh,0

;Room0
welcomeMsg byte "Welcome aboard the Battle cruiser 'Tiger Claw'," ,0ah,0dh,0
welcomeMsg1 byte "I am Captain James Shepard" ,0ah,0dh,0
introMsg byte "Well hello, " ,0
introMsg1 byte " I know you have had a long trip out here to the front lines," ,0ah,0dh,0
introMsg2 byte "so I'll keep this short." ,0ah,0dh,0
introMsg3 byte "We're called the Tiger Claw because we are the tip of the spear." ,0ah,0dh,0
introMsg4 byte "First ones into battle, last ones out...",0ah,0dh,0
introMsg5 byte "Get some rest rookie, then we will see what you are capable of." ,0ah,0dh,0
nameMsg byte "What's your call sign..." ,0ah,0dh,0

;Room1-----------------------------------------------------------------
time byte ":: 0630 Hours - Tiger Claw Fighter Pilot Brifing Room ::" ,0ah,0dh,0
commander1 byte "You men have been brought here because you were the best" ,0ah,0dh,0
commander2 byte "of your training class..." ,0ah,0dh,0
commander3 byte "Our Battle Cruiser is the best in its class." ,0ah,0dh,0
commander4 byte "We have turrets and plasma launchers on just about" ,0ah,0dh,0
commander5 byte "every portion of the outer hull, the finest shields and" ,0ah,0dh,0
commander6 byte "reinforced uber titanium walls. " ,0ah,0dh,0
commander7 byte "Despite that, we are not invincible." ,0ah,0dh,0
commander8 byte "The enemy knows who the Tiger Claw is" ,0ah,0dh,0
commander9 byte "and how important we are to the war effort..." ,0ah,0dh,0
commander10 byte "That is where you and the other veteran pilots come in to play." ,0ah,0dh,0
commander11 byte "You are to protect the Tiger Claw from incoming fighters, at ALL COSTS!" ,0ah,0dh,0
commander12 byte "About our enemy, we have encountered them in deep space, " ,0ah,0dh,0
commander13 byte "and have been dubbed The Anunnaki." ,0ah,0dh,0
commander14 byte  "Their battle ships are massive, strong and well defended." ,0ah,0dh,0
commander15 byte "Their fighters are of the most impressive that we have encountered." ,0ah,0dh,0
commander16 byte "This does not mean that you men are heading into defeat." ,0ah,0dh,0
commander17 byte "Our fighters are as capable as the Anunnaki's," ,0ah,0dh,0
commander18 byte "Currently we tracked a small group of fighters, we brief" ,0ah,0dh,0
commander19 byte "at 1000 hours, you are dismissed..." ,0ah,0dh,0

;Room2------------------------------------------------------------------
menuHeadSpace byte " " ,0ah,0dh,0
menuHead byte "				||Main Menu||					" ,0ah,0dh,0
option1 byte "1. Pilot's Quarters" ,0ah,0dh,0
option2 byte "2. Hangar" ,0ah,0dh,0
option3 byte "3. Next Mission" ,0ah,0dh,0

;Room25 CAPTAINS MENU----------------------------------------------------
capmenuHeadSpace byte " " ,0ah,0dh,0
capmenuHead byte "				||Captain'S Menu|					" ,0ah,0dh,0
capoption1 byte "1. Captain's Quarters" ,0ah,0dh,0
capoption2 byte "2. Bridge (Next Mission)" ,0ah,0dh,0

;Room3
;NON VET MESSAGES WHEN STORE AND QUARTERS ARE LOCKED--------------------
nonVet1 byte "::You decide to enter the pilot's quarters::",0ah,0dh,0
nonVet2 byte "::The pilots are mostly seated, playing various games::",0ah,0dh,0
nonVet3 byte "Awkward looks are passed your way and one pilot stands up..." ,0ah,0dh,0
nonVet4 byte "DeadEye: Looks like the rookie doesn't know the rules yet..." ,0ah,0dh,0
nonVet5 byte "DeadEye: Rookies do not get to enter without soem kills under their belt" ,0ah,0dh,0
nonVet6 byte "DeadEye: Keep it moving rook..." ,0ah,0dh,0

;ROOM4-----------------------------------------------------------------
needVetStatus byte "You must increase your Veteran Status",0ah,0dh,0
needVetStatus2 byte "to enter this area" ,0ah,0dh,0
needVetStatus3 byte "Complete more missions" ,0ah,0dh,0

;ROOM6 MISSION 1 INTRO -----------------------------------------------
mission11 byte "::Briefing Room 1000 Hours::",0ah,0dh,0
mission12 byte "Captain Shepard: Greetings again men,",0ah,0dh,0
mission13 byte "Captain Shepard: As previously mentioned, we",0ah,0dh,0
mission14 byte "Captain Shepard: have located a group of fighters",0ah,0dh,0
mission15 byte "Captain Shepard: we believe to be on a scouting mission.",0ah,0dh,0
mission16 byte "Captain Shepard: Your job, is to take those fighters out",0ah,0dh,0
mission17 byte "Captain Shepard: and as fast as possible. We would hate for them",0ah,0dh,0
mission18 byte "Captain Shepard: to relay to their mothership our co-ordinates.",0ah,0dh,0
mission19 byte "Captain Shepard: Suit up, and may luck be on our side!",0ah,0dh,0
mission110 byte "Captain Shepard: Dismissed...",0ah,0dh,0

;ROOM7 MISSION 1 ACT 1 ----------------------------------------------
mission0Nar1 byte "With feelings of nervousness you enter the cock-pit of your",0ah,0dh,0
mission0Nar2 byte "newly assembled F102 - Screaming Eagle.",0ah,0dh,0
mission0Nar3 byte "As your fighter is launched through the runway at extreme speed",0ah,0dh,0
mission0Nar4 byte "You think, here goes nothing!",0ah,0dh,0
mission0Nar5 byte "It seems like seconds before the enemy is in sight!" ,0ah,0dh,0
mission0Nar6 byte "In formation, the Flying Tigers fly towards the enemy" ,0ah,0dh,0
mission0Nar7 byte "As they equally turn in formation to face them head on." ,0ah,0dh,0

encounter01 byte "As you and your squadron race towards the enemy,",0ah,0dh,0
encounter02 byte "You have a lock, but the enemy most likely has a lock on you as well.",0ah,0dh,0
encounter03 byte "1. Fire Photon Cannons as well as Machine guns",0ah,0dh,0
encounter04 byte "in a hail of gunfire!",0ah,0dh,0
encounter05 byte "2. to evade, and try to maneuvers into a",0ah,0dh,0
encounter06 byte "more tactically sound position.",0ah,0dh,0
encounter0Death1 byte "In a barrage of cannon and machine gun fire",0ah,0dh,0
encounter0Death2 byte "You see your target torn to pieces, and cheer with excitement!",0ah,0dh,0
encounter0Death3 byte "However, you do not see the enemy directly above you.",0ah,0dh,0
encounter0Death4 byte "Before you know it, your ship is obliterated.",0ah,0dh,0
encounter0Pass1 byte "Despite feeling the need to pull the trigger,",0ah,0dh,0
encounter0Pass2 byte "you enter a steep rolling dive, dodging the hail of ",0ah,0dh,0
encounter0Pass3 byte "bullets sent in your direction.",0ah,0dh,0
encounter0Pass4 byte "Looping around, you come right behind an enemy fighter",0ah,0dh,0
encounter0Pass5 byte "No escape for him...As his fighter is torn to pieces by your cannons.",0ah,0dh,0

;ROOM 8 MISSION 1 ACT 2 -----------------------------------------------
encounter02Death1 byte "You pull up as hard as you can, and hit the boosters.",0ah,0dh,0
encounter02Death2 byte "Despite your best efforts, the Anunnaki pilot out maneuvers you",0ah,0dh,0
encounter02Death3 byte "and you now little bits floating through space!",0ah,0dh,0
encounter02Pass1 byte "You hurriedly radio for help.",0ah,0dh,0
encounter02Pass2 byte "DeadEye: Well look who it is...",0ah,0dh,0
encounter02Pass3 byte "DeadEye: Ive got someone on my 6 too, im coming your way.",0ah,0dh,0
encounter02Pass4 byte "DeadEye: take him out on the fly by, you scratch my back ill scratch yours.",0ah,0dh,0
encounter02Pass5 byte "The two pilots hurtle towards each other, taking out each other's pursuing enemies",0ah,0dh,0
encounter02Pass6 byte "in seemingly easy fashion.",0ah,0dh,0
encounter02Pass7 byte "Looking out to the great abyss, you can tell this engagement is over.",0ah,0dh,0
encounter02Pass8 byte "Back to the Tiger it is, with a huge sigh of relief",0ah,0dh,0
encounter021 byte "With nervous excitement, you continue your hunt.",0ah,0dh,0
encounter022 byte "Suddenly you notice an enemy to your 6 o'clock, right behind you.",0ah,0dh,0
encounter023 byte "1. Attempt a steep climb and try to shake him",0ah,0dh,0
encounter024 byte "2. Radio for assistance!",0ah,0dh,0

;ROOM9 VETERAN STATUS ALLOWED INTO PILOT'S QUARTERS----------------------------
pilotQ1 byte "Razor: Hey look who it is, nice flying.",0ah,0dh,0
pilotQ2 byte "Razor: Hear you and DeadEye had a close call out there",0ah,0dh,0
pilotQ3 byte "DeadEye: Damn right we did, this guy had my back though.",0ah,0dh,0
pilotQ4 byte "DeadEye: Now that you have proved yourself",0ah,0dh,0
pilotQ5 byte "DeadEye: feel free to have a seat any time!",0ah,0dh,0

;SECOND ENTRANCE AND MORE ALLOWS GAME OF PAPER ROCK SCISSORS WITH RAZOR ---------
Razor1 byte "Razor: There he is, wish we could hang out more,",0ah,0dh,0
Razor2 byte "Razor: but with all the activity going on recently",0ah,0dh,0
Razor3 byte "Razor: we should likely get moving.",0ah,0dh,0

;ROOM10 MISSION 2 INTRO --------------------------------------------------------
mission21 byte "::Briefing Room 1600 Hours::",0ah,0dh,0
mission22 byte "Captain Shepard: Great job out there men.",0ah,0dh,0
mission23 byte "Captain Shepard: The good news is that the fighters were unable to signal",0ah,0dh,0
mission24 byte "Captain Shepard: their mothership. However, it seems they were able to",0ah,0dh,0
mission25 byte "Captain Shepard: get off a shorter range message to a nearby Dreadnought.",0ah,0dh,0
mission26 byte "Captain Shepard: Our readings show that it is most certainly headed our way.",0ah,0dh,0
mission27 byte "Captain Shepard: However, before we can deal with that, it",0ah,0dh,0
mission28 byte "Captain Shepard: seems they have deployed a sea of drones our way.",0ah,0dh,0
mission29 byte "Captain Shepard: Likely an attempt to soften us up.",0ah,0dh,0
mission210 byte "Captain Shepard: Let's go get em Tigers, its hunting time again",0ah,0dh,0

;ROOM11 MISSION 2 ACT 1 ---------------------------------------------------------
mission2Nar1 byte "And just like that you find yourself back in the emptyness of space.",0ah,0dh,0
mission2Nar2 byte "Suddenly a squawk over the radio screams, drones, overhead.",0ah,0dh,0
mission2Nar3 byte "And there was a ton of them, unfortunately the warning was too late.",0ah,0dh,0
mission2Nar4 byte "The drones were coming in right behind the Tiger formations.",0ah,0dh,0
mission2Nar5 byte "You break formation to take shelter behind a floating asteroid...",0ah,0dh,0
mission2Encounter0 byte "This seems like a resonably nice spot, especially with chaos is all around.",0ah,0dh,0
mission2Encounter1 byte "You spot Razor, tailed by 4 drones, and obviously in trouble.",0ah,0dh,0
mission2Encounter2 byte "But you feel it may be too dangerous right now... ",0ah,0dh,0
mission2Encounter3 byte "1. Stay where you are at, and wait to come out from hiding.",0ah,0dh,0
mission2Encounter4 byte "2. Come out from hiding boosters and guns ablazing to help Razor.",0ah,0dh,0
mission2Death1 byte "You decide to hang back for another minute or two before moving back out.",0ah,0dh,0
mission2Death2 byte "Little did you know 5 drones had already witnessed your maneuver",0ah,0dh,0
mission2Death3 byte "And come roaring up from beneath you, decimating your ship.",0ah,0dh,0
mission2Pass1 byte "You decide that there is no time to lose, and another Tiger will",0ah,0dh,0
mission2Pass2 byte "not die if you can help it. You come out firing everything you got.",0ah,0dh,0
mission2Pass3 byte "Killing all 4 drones.",0ah,0dh,0
mission2Pass4 byte "Razor: Give em hell Rookie!! Keep it up.",0ah,0dh,0

;ROOM12 MISSION 2 ACT 2 ----------------------------------------------------------
mission2Encounter20 byte "Feeling like you are on the prowl, you scan your monitors for enemies.",0ah,0dh,0
mission2Encounter21 byte "Immediately you notice a fellow rookie pilot, Silver, in pursuit of 6 drones.",0ah,0dh,0
mission2Encounter22 byte "As you look for another target, you see Silver takes damage from another group of drones!",0ah,0dh,0
mission2Encounter23 byte "Do you move in on the assaulting drones to help Silver,",0ah,0dh,0
mission2Encounter24 byte "or drop in to pursue Silver's Targets?????",0ah,0dh,0
mission2Encounter25 byte "1. Continue pursuing Silver's Targets" ,0ah,0dh,0
mission2Encounter26 byte "2. Disengage Silver's targets and assist him in defeating the drones on his 6",0ah,0dh,0
mission2Kill1 byte "As Silver peels off, you drop in right behind the drones.",0ah,0dh,0
mission2Kill2 byte "As you open fire and take out all 6 drones, you turn to check up on Silver." ,0ah,0dh,0
mission2Kill3 byte "Unfortunately he was not able to evade the attackers, and his ship is now in ruins.",0ah,0dh,0
mission2Save1 byte "Again you think to yourself, Saving Tigers is much more important than kills.",0ah,0dh,0
mission2Save2 byte "As Silver drops his attack, you disengage from the 6 drones and fall in",0ah,0dh,0
mission2Save3 byte "behind Silver's pursuers, decimating the 4 drones giving chase. Another Tiger saved.",0ah,0dh,0
mission2EncounterEnd1 byte "It was a hard fought battle, but we ended up on top.",0ah,0dh,0
mission2EncounterEnd2 byte "The order over the radio advised the command to return",0ah,0dh,0
mission2EncounterEnd3 byte "to base. You couldnt move fast enough on that order.",0ah,0dh,0

;ROOM13 HANGAR MEETING ALEXANDRIA -----------------------------------------------
Alex1 byte "Alexandria: Greetings ",0
Alex2 byte " Im Alex, I have heard about you,",0ah,0dh,0
Alex21 byte "Alexandria: seems you have been setting the bar high for",0ah,0dh,0
Alex3 byte "Alexandria: some of our other rookie pilots. The Tiger Claw can definitely ",0ah,0dh,0
Alex4 byte "Alexandria: use as many exceptional pilots as we can find!",0ah,0dh,0
Alex5 byte "Alexandria: We should meet up outside of this hangar, maybe we could get",0ah,0dh,0
Alex6 byte "Alexandria: to know each other better!",0ah,0dh,0
Alex7 byte "Alexandria: For now its all work work work though, best of luck out there!",0ah,0dh,0

;ROOM14 MISSION 3 INTRO ----------------------------------------------------------
missionIntro31 byte "::Briefing 1800 Hours::",0ah,0dh,0
missionIntro32 byte "Captain Shepard: Outstanding work on those drones Tigers.",0ah,0dh,0
missionIntro33 byte "Captain Shepard: We are all exhausted, and you are all performing",0ah,0dh,0
missionIntro34 byte "Captain Shepard: beyond expectations on this rough schedule.",0ah,0dh,0
missionIntro35 byte "Captain Shepard: However, I would like to point out one pilot",0ah,0dh,0
missionIntro36 byte "Captain Shepard: in particular, give a hand for :",0
missionIntro37 byte " this pilot",0ah,0dh,0
missionIntro38 byte "Captain Shepard: has surpassed expectations, I believe a congratulations are in order!",0ah,0dh,0
missionIntro39 byte "Captain Shepard: Now, on to more pressing issues...",0ah,0dh,0
missionIntro310 byte "Captain Shepard: That Dreadnought is out there in deep space and",0ah,0dh,0
missionIntro311 byte "Captain Shepard: headed our way fast. It could be here any moment.",0ah,0dh,0
missionIntro312 byte "Captain Shepard: We expect an all out confrontation. All hands aboard",0ah,0dh,0
missionIntro313 byte "Captain Shepard: The Tiger Claw are on deck, do not think this fight is",0ah,0dh,0
missionIntro314 byte "Captain Shepard: yours alone Tigers. We will be fighting with you",0ah,0dh,0
missionIntro315 byte "Captain Shepard: Your ships have been refueld, resupplied and repaired.",0ah,0dh,0
missionIntro316 byte "Captain Shepard: Upon sight of the Dreadnought you are to attack and bomb",0ah,0dh,0
missionIntro317 byte "Captain Shepard: the target with everything you got.",0ah,0dh,0
missionIntro318 byte "Captain Shepard: In case this is the last we see each other, it has",0ah,0dh,0
missionIntro319 byte "Captain Shepard: been a pleasure serving with everyone of you. Good luck out there!",0ah,0dh,0
missionIntro320 byte "Captain Shepard: Dismissed...",0ah,0dh,0

;ROOM15 MISSION 3 ACT 1 -------------------------------------------------------
mission3Encounter1 byte "As you and the Flying Tigers patrol the edges of the Tiger Claw's",0ah,0dh,0
mission3Encounter2 byte "sensor range, the ever dangerous Dreadnought appears.",0ah,0dh,0
mission3Encounter3 byte "Suddenly the enemy opens up with a multitude of ordinance.",0ah,0dh,0
mission3Encounter4 byte "Missles, lazers, cannons all at once. And fighters are deployed.",0ah,0dh,0
mission3Encounter5 byte "Hold off the attack, all Flying Tigers return to defend the Tiger Claw",0ah,0dh,0
mission3Encounter6 byte "against incoming all out fighter attack. If we succeed in thinning their",0ah,0dh,0
mission3Encounter7 byte "numbers, our fighter attack on them will be successful as well.",0ah,0dh,0
mission3Encounter8 byte "Boosters at maximum you close in on Tiger Claw and engage",0ah,0dh,0
mission3Encounter9 byte "fighters currently attacking the battle cruiser.",0ah,0dh,0
mission3Encounter10 byte "Two targets are pointed out by your targeting system.",0ah,0dh,0
mission3Encounter11 byte "A large missile incoming towards the Tiger Claw and a group of fighters",0ah,0dh,0
mission3Encounter12 byte "actively bombing the Tiger Claw. Seemingly unable to break it's shields.",0ah,0dh,0
mission3Encounter13 byte "1. Attack the large incoming missle",0ah,0dh,0
mission3Encounter14 byte "2. Aim for the group of fighters bombing the Tiger Claw",0ah,0dh,0

mission3EncounterFail1 byte "You decide its best to go after the fighters. As you take out the",0ah,0dh,0
mission3EncounterFail2 byte "multiple fighters, the large missile impacts the Tiger Claw broadside.",0ah,0dh,0
mission3EncounterFail3 byte "The explosion is blinding, when the impact settles",0ah,0dh,0
mission3EncounterFail4 byte "a tattered and withering ship is left behind. The Tiger Claw is no more.",0ah,0dh,0

mission3EncounterPass1 byte "You decide to go after the massive incoming missile",0ah,0dh,0
mission3EncounterPass2 byte "Two fighters were escorting the missile, which were dispatched easily.",0ah,0dh,0
mission3EncounterPass3 byte "Thankfully you decided to go after this missile.",0ah,0dh,0
mission3EncounterPass4 byte "The explosion from the detonation was massive, maybe",0ah,0dh,0
mission3EncounterPass5 byte "even enough to have taken out the Tiger Claw!",0ah,0dh,0
mission3EncounterPass6 byte "SHEPARD RADIO: Their fighters are mostly annihalated, full-scale",0ah,0dh,0
mission3EncounterPass7 byte "SHEPARD RADIO: fighter attack is a go. Tiger Claw will be",0ah,0dh,0
mission3EncounterPass8 byte "SHEPARD RADIO: on the lookout for friendly fire, god speed eveyone!",0ah,0dh,0

;ROOM16 MISSION 3 ACT 2 --------------------------------------------------------------
mission3Encounter21 byte "As you speed off towards the massive ship, you think",0ah,0dh,0
mission3Encounter22 byte "about how low your chances of survival are.",0ah,0dh,0
mission3Encounter23 byte "In the face of annihalation, what other choice was there.",0ah,0dh,0
mission3Encounter24 byte "In what seemed like seconds, you were up close to the",0ah,0dh,0
mission3Encounter25 byte "dreadnought. Now to strafe the bridge of the ship or",0ah,0dh,0
mission3Encounter26 byte "perform an attack from the rear, possibly hitting the ship's engines?",0ah,0dh,0
mission3Encounter27 byte "1. Attack head on",0ah,0dh,0
mission3Encounter28 byte "2. Dodge incoming fire to attack engines.",0ah,0dh,0

mission3Fail21 byte "You hit the boosters and move in to make a run on the massive ship.",0ah,0dh,0
mission3Fail22 byte "As you enter your run, massive turrets are deployed, and you are mercilessly shot down.",0ah,0dh,0

mission3Pass21 byte "As you pass the front end of the ship, you notice massive turrets being deployed.",0ah,0dh,0
mission3Pass22 byte "Sure are glad you did not pass by there.",0ah,0dh,0
mission3Pass23 byte "RADIO-RAZOR: All Tigers attack the rear of the ship!",0ah,0dh,0
mission3Pass24 byte "RADIO-RAZOR: With their fighters out of commission they are wide open.",0ah,0dh,0
mission3Pass25 byte "In formation you all attack the ship's engines crippling the giant beast.",0ah,0dh,0

;ROOM17 MISSION 3 ACT 3-----------------------------------------------------------------------
mission3Encounter31 byte "RADIO-RAZOR: Alright team lets bring our formations broadside",0ah,0dh,0
mission3Encounter32 byte "RADIO-RAZOR: and take out some turrets!",0ah,0dh,0
mission3Encounter33 byte "After several strafe runs, you have perfect sights on another",0ah,0dh,0
mission3Encounter34 byte "tiger in serious problems, chased by two drones.",0ah,0dh,0
mission3Encounter35 byte "1. Aid fellow Tiger",0ah,0dh,0
mission3Encounter36 byte "2. Continue taking out Turrets?",0ah,0dh,0
mission3Save1 byte "You decide to break formation and aid your fellow Tiger",0ah,0dh,0
mission3Save2 byte "Score two more for me and another saved pilot!",0ah,0dh,0
mission3Save3 byte "Unfortunately other turrets had you in their sites and you take massive damage!",0ah,0dh,0
mission3Save4 byte "Crap I have to take it in, im on my last leg out here!!",0ah,0dh,0
mission3Save5 byte "RAZOR: Take it in, we got this!",0ah,0dh,0
mission3Turret1 byte "You decide he can take care of himself and make another run at the Turrets",0ah,0dh,0

;ROOM18 MISSION 3 ACT 4 MFING CAPTAIN TIME ------------------------------------------------------
mission3TC1 byte "Taking heavy damage, you limp back to the Tiger Claw, crash landing in the docking bay",0ah,0dh,0
mission3TC2 byte "only to find the ship in shambles...",0ah,0dh,0
mission3TC3 byte "She has taken massive damage from the Dreadnought",0ah,0dh,0
mission3TC4 byte "Captain Shepard is dead, and there are only 3 crewman left on the bridge",0ah,0dh,0
mission3TC5 byte "You shout, what do we do... They respond we dont know!!!",0ah,0dh,0
mission3TC6 byte "1. Take Command of what remains of the Tiger Claw",0ah,0dh,0
mission3TC7 byte "2. Try to run from the chaos...",0ah,0dh,0
mission3TCCoward1 byte "You run from the bridge, while people ask where you are going.",0ah,0dh,0
mission3TCCoward2 byte "You run for a little bit, before the Tiger Claw is demolished in a blaze of defeat",0ah,0dh,0
mission3TCCaptain1 byte "We Still have people out there, we are not giving up...",0ah,0dh,0
mission3TCCaptain2 byte "Were almost done for, we got one shot left, turn us broadside to the dreadnought",0ah,0dh,0
mission3TCCaptain3 byte "she cant move, focus all energy on the broadside laser cannons!!",0ah,0dh,0
mission3TCCaptain4 byte "Crew Member: But that leaves us defensless!",0ah,0dh,0
mission3TCCaptain5 byte "You Respond: Dont worry, we wont need defenses if this works!",0ah,0dh,0
mission3TCCaptain6 byte "With the firing of all 35 laser cannons on maximum power, they tear through",0ah,0dh,0
mission3TCCaptain7 byte "the dreadnought with ease!",0ah,0dh,0
mission3TCCaptain8 byte "What fighters remain head back to base and the Tiger Claw limps back for repairs.",0ah,0dh,0

;ROOM19 EARTH GET COMMANDER --------------------------------------------------------------------------------
Earth1 byte "The Tiger Claw limps back to Earth with limited crew, fighters and you as Captain.",0ah,0dh,0
Earth2 byte "After seeing the videos of the battles you and the Tiger Claw encountered",0ah,0dh,0
Earth3 byte "in the front lines of this war, the people are outraged.",0ah,0dh,0
Earth4 byte "Vowing never to let the Tiger out of the bay without the latest of technology,",0ah,0dh,0
Earth5 byte "The Tiger Claw is outfitted with even stronger fire power, defenses, fighters",0ah,0dh,0
Earth6 byte "and of course, a great Captain.",0ah,0dh,0
Earth7 byte "You have been put through rigourous hours of schooling, testing and simulations.",0ah,0dh,0
Earth8 byte "Now it is time for the Tiger Claw to get back into the fight with you at the helm.",0ah,0dh,0
Earth9 byte "As the Tiger Claw takes off from the Earth docking bay, Razor, DeadEye and Alexandria",0ah,0dh,0
Earth10 byte "Stand before you, all in saluting attention.",0ah,0dh,0
Earth11 byte "How crazy things work out, as you tell them to quit the crap and get back to their stations.",0ah,0dh,0
Earth12 byte "There are bigger battles to come.",0ah,0dh,0

;ROOM20 MISSION 4 INTRO -------------------------------------------------------------------
Mission4Intro1 byte "As you embark on your first mission sitting at the helm of the Tiger Claw,",0ah,0dh,0
Mission4Intro2 byte "you prepare to give your first mission briefing.",0ah,0dh,0
Mission4Intro3 byte "Alright men, I know we havent been out long, but we got our first mission.",0ah,0dh,0
Mission4Intro4 byte "We have word of a small group of fighters patrolling the Zeta sector.",0ah,0dh,0
Mission4Intro5 byte "Currently we are unsure of our next move, but be on the ready, we may need",0ah,0dh,0
Mission4Intro6 byte "you at a moment's notice!",0ah,0dh,0
Mission4Intro7 byte "Stay frosty everone, dismissed!",0ah,0dh,0

;ROOM21 MISSION 4 ACT 1 -------------------------------------------------------------------------
Mission4Act11 byte "Sitting at the helm of the Tiger Claw, someone shouts out.",0ah,0dh,0
Mission4Act12 byte "Captain, we have something on our long range scanners.",0ah,0dh,0
Mission4Act13 byte "dont think they have spotted us yet.",0ah,0dh,0
Mission4Act14 byte "What course of action should we take?",0ah,0dh,0
Mission4Act15 byte "1. Fire at the group of fighters using lasers.",0ah,0dh,0
Mission4Act16 byte "2. Fire at the group of fighters using cannons",0ah,0dh,0
Mission4Act17 byte "3. Deploy small team of stealth fighters.",0ah,0dh,0

Mission4Act1Fail1 byte "Firing your large weapons at the small targets from such a distance",0ah,0dh,0
Mission4Act1Fail2 byte "was a crucial mistake. Not all fighters were destroyed. And within",0ah,0dh,0
Mission4Act1Fail3 byte "seconds, a mothership arrives ademolishing the Tiger Claw",0ah,0dh,0

Mission4Act1Pass1 byte "Congratulations, deploying stealth fighters was perfect!",0ah,0dh,0
Mission4Act1Pass2 byte "your Fighting Tigers were able to sneak up on the enemy fighters.",0ah,0dh,0
Mission4Act1Pass3 byte "They destroyed all but one fighter and were even able to capture him.",0ah,0dh,0
Mission4Act1Pass4 byte "Upon their return, you will need to interrogate him.",0ah,0dh,0

;ROOM22 MISSION 4 ACT 2 ------------------------------------------------------------------------------
prisoner1 byte "         {}                          {}",0ah,0dh,0
prisoner2 byte "                      (| |)",0ah,0dh,0
prisoner3 byte "		     _  -  _",0ah,0dh,0
prisoner4 byte "                    //|   |\\",0ah,0dh,0
prisoner5 byte "               ||--()-------()---||",0ah,0dh,0
prisoner6 byte "	       ||   (_)/__\( )   ||",0ah,0dh,0
prisoner7 byte "	       ||   | |   | |    ||",0ah,0dh,0
prisoner8 byte "	       ||   | |   | |    ||",0ah,0dh,0

Mission4Act21 byte "You enter a dark room, with a lonely shiny metal table at the center.",0ah,0dh,0
Mission4Act22 byte "Sitting behind it in cuffs is a face that looks human, but awkwardly not quite",0ah,0dh,0
Mission4Act23 byte "You take a seat at the table.",0ah,0dh,0
Mission4Act24 byte "After some small chat, you get down to business",0ah,0dh,0
Mission4Act25 byte "And tell him you want the co-ordinates to his mothership.",0ah,0dh,0
Mission4Act26 byte "1. Ask nicely",0ah,0dh,0
Mission4Act27 byte "2. Offer asylum on an off Earth colony where he can live in peace.",0ah,0dh,0
Mission4Act28 byte "3. Take the hard route, and beat the prisoner.",0ah,0dh,0

Mission4Act2Nice1 byte "After hours of trying to appeal to the prisoner's good side, he does not crack.",0ah,0dh,0
Mission4Act2Nice2 byte "Because of this, your stay in space aboard the Tiger's Claw runs the course",0ah,0dh,0
Mission4Act2Nice3 byte "of your life, leading a life of loneliness and war.",0ah,0dh,0
Mission4Act2Nice4 byte "you have failed to end the war in a moderate time line try again!",0ah,0dh,0

Mission4Act2Asylum1 byte "You plead to the pilot that you wish to end this conflict as soon as possible.",0ah,0dh,0	
Mission4Act2Asylum2 byte "And that he could spend the rest of his days at peace, on an off Earth colony.",0ah,0dh,0	
Mission4Act2Asylum3 byte "The rest of his life could be lived out in peace, without worry.",0ah,0dh,0	
Mission4Act2Asylum4 byte "He likes this idea, and advises you of the mothership's location.",0ah,0dh,0

Mission4Act2Aggressor1 byte "You gently close the door behind you, and start to crack your knuckles.",0ah,0dh,0
Mission4Act2Aggressor2 byte "It is about to get ugly.",0ah,0dh,0
Mission4Act2Aggressor3 byte "After several hours of beating the prisoner, he provides the location...",0ah,0dh,0

;ROOM26 CAPTAIN'S QUARTERS
;----------------------------------------------------------------------------------------------------------
deathMsg byte "You have chosen incorrectly and have suffered the consequences.",0ah,0dh,0
deathMsg2 byte "You are merely another casualty in this intergalactic battle.",0ah,0dh,0
deathMsg3 byte "Returning to beginning of action sequence, choose wisely!",0ah,0dh,0

congratulations1 byte "Congratulations, your veteran status has increased!",0ah,0dh,0
congratulations2 byte "New options are available!",0ah,0dh,0

;ROOM27 ENCOUNTER WITH ALEXANDRIA
romance1 byte "Alexandria: Hey there :",0
romance2 byte " I was wondering when we would get some alone time!",0ah,0dh,0
romance3 byte "Alexandria: How about you take me up on that",0ah,0dh,0
romance4 byte "Alexandria: offer to meet up outside of the hangar?",0ah,0dh,0

response1 byte "1. Oh yea, I knew we would be hooking up!",0ah,0dh,0
response2 byte "2. Hmm, you throw yourself at captains this much?",0ah,0dh,0
response3 byte "3. I was kinda hoping to see you here.",0ah,0dh,0

responselose1 byte "Alexandria: I should have known you would be a douche, goodbye!",0ah,0dh,0
responsewin1 byte "Alexandria: Well it looks like great minds think alike!",0ah,0dh,0
responsewin2 byte "Alexandria: Why dont you show me these fancy captain's quarters!",0ah,0dh,0
responsewin3 byte "You follow her into your quarters, queue the sexy music!",0ah,0dh,0

;ROOM 28 CAPTAINS QUARTERS -------------------------------------------------------------------------------
captq1 byte "You enter your captain's quarters.",0ah,0dh,0
captq2 byte "After lying in bed for a few minutes, you are uneasy.",0ah,0dh,0
captq3 byte "You decide this is no time for sleep, and off you go.",0ah,0dh,0

;ROOM29 FINAL MISSION -----------------------------------------------------------------------------------
missionChoice1 byte "Now that you have successfully acquired the mothership's location,",0ah,0dh,0
missionChoice2 byte "what action do you wish to take?",0ah,0dh,0
missionChoice3 byte "1. Warp speed into the mothership's location, and give it everything the Tiger Claw has.",0ah,0dh,0
missionChoice4 byte "2. Warp near the mothership's firing range, slowly moving in and opening fire",0ah,0dh,0
missionChoice5 byte "with eveything you got as soon as you come into firing range, may get caught in the process,",0ah,0dh,0
missionChoice6 byte "losing your surprise attack.",0ah,0dh,0

;ROOM30 MISSION 5 ACT 1 --------------------------------------------------------------------------------
mission5ACT1 byte "teleport right behind the Anunnaki mothership.",0ah,0dh,0
mission5ACT2 byte "and hit her with everything we got.",0ah,0dh,0
mission5ACT3 byte "We currently have the advantage that they have no clue we are coming.",0ah,0dh,0
mission5ACT4 byte "Catching them off guard would aid us in a surprise attack.",0ah,0dh,0
mission5ACT5 byte "So I need all pilots ready, all hands on deck",0ah,0dh,0
mission5ACT6 byte "and those in charge of battlestations,",0ah,0dh,0
mission5ACT7 byte "be ready to fire everything we got at them.",0ah,0dh,0
mission5ACT8 byte "Tiger Claw, it has been a pleasure.",0ah,0dh,0

mission5ACT9 byte "The Tiger Claw teleports right behind the mothership.",0ah,0dh,0
mission5ACT10 byte "The crew stares in awe for a split second, before opening",0ah,0dh,0
mission5ACT11 byte "fire, the mothership struggles to maneuver and active its heavy",0ah,0dh,0
mission5ACT12 byte "shields, but it is too late. The Tiger Claw has caught",0ah,0dh,0
mission5ACT13 byte "her sleeping, and the ship goes down will little damage done to the Tiger Claw.",0ah,0dh,0

mission5ACT14 byte "Thanks to your immediate action and the action of your crew,",0ah,0dh,0
mission5ACT15 byte "The Anunnaki find one of their flagships decimated.",0ah,0dh,0
mission5ACT16 byte "Because of this, they immediately initiate peace talks, and for now at least,",0ah,0dh,0
mission5ACT17 byte "the war is over, you and your crew get to head home to enjoy some peace and quiet.",0ah,0dh,0

;ROOM31 MISSION 5 ACT 1 ----------------------------------------------------------------------------
mission52ACT11 byte "teleport just out of the mothership's range.",0ah,0dh,0
mission52ACT22 byte "It will also be out of our range too, so we will slowly",0ah,0dh,0
mission52ACT33 byte "approach the ship untill we are just in range then open",0ah,0dh,0
mission52ACT44 byte "up with everything weve got.",0ah,0dh,0
mission52ACT55 byte "So I need all pilots ready, all hands on deck",0ah,0dh,0
mission52ACT66 byte "and those in charge of battlestations,",0ah,0dh,0
mission52ACT77 byte "be ready to fire everything we got at them.",0ah,0dh,0
mission52ACT88 byte "Tiger Claw, it has been a pleasure.",0ah,0dh,0

mission52ACT9 byte "The Tiger Claw teleports in just out of the Motherships range,",0ah,0dh,0
mission52ACT10 byte "Taking cover behind a wandering asteroid.",0ah,0dh,0
mission52ACT011 byte "Despite taking the best percautions, the Tiger Claw is sighted on radar!",0ah,0dh,0
mission52ACT12 byte "With the loss of the surprise attack, the Tiger Claw takes",0ah,0dh,0
mission52ACT13 byte "massive casualties. With her improved armor, weapons and strategic",0ah,0dh,0
mission52ACT14 byte "captain at the helm, the Tiger Claw is able to deal a surprising victory.",0ah,0dh,0
mission52ACT15 byte "Unfortunately, since it was not a swift defeat, the Anunnaki were not demoralised",0ah,0dh,0
mission52ACT16 byte "enough to offer peace. They instead fought back harder, engaging the two species",0ah,0dh,0
mission52ACT17 byte "in a battle that would rage for centuries.",0ah,0dh,0

;FINAL MISSION PLAYER (CAPTAIN) STATEMENTS -------------------------------------------------------------
finalBrief1 byte "Greetings to all of you currently stationed on the Tiger Claw",0ah,0dh,0
finalBrief2 byte "We have come across the location of an Anunnaki Mothership.",0ah,0dh,0
finalBrief3 byte "We do not know much about them, other than the fact that the",0ah,0dh,0
finalBrief4 byte "enemy has very few of these. They are heavily armored and",0ah,0dh,0
finalBrief5 byte "heavily defended.",0ah,0dh,0
finalBrief6 byte "Our next mission is extremely dangerous, and we may not survive it.",0ah,0dh,0
finalBrief7 byte "However, if we win this battle, and crush the enemy with their strongest weapon,",0ah,0dh,0
finalBrief8 byte "We may be able to push the enemy into a peaceful surrender.",0ah,0dh,0
finalBrief9 byte "Bringing an end to this tiresome war.",0ah,0dh,0
finalBrief10 byte "There are plenty of evacuation pods found onboard.",0ah,0dh,0
finalBrief11 byte "For those that wish to flee, I would not blame you, but",0ah,0dh,0
finalBrief12 byte "please remember the less hands we have on deck, the less a",0ah,0dh,0
finalBrief13 byte "chance we have of a victory. I leave the decision to you.",0ah,0dh,0
finalBrief14 byte "At 1200 hours, we will...",0ah,0dh,0

;DISPLAY PLAYER'S SCORE -----------------------------------------------------------------------------
score1 byte "Congratulations, you have acquired: ",0
score2 byte " kills ",0ah,0dh,0
death1 byte "You have died a total of :",0
death2 byte " times.",0ah,0dh,0
saves1 byte "And you have saved: ",0
saves2 byte " tigers.",0ah,0dh,0

;ROOM32 ---------------------------------------------------------------------------------------
stats byte "Here are your stats throughout the game!",0ah,0dh,0
ending byte "I hope you have enjoyed -Tale of the Tiger Claw!-",0ah,0dh,0

;Romance RESULTS -------------------------------------------------------------------------------
casinova byte "You successfully romanced Alexandria!" ,0ah,0dh,0
coldShoulder byte "You were not able to romance Alexandria!",0ah,0dh,0
earlyend byte "Thanks to your bravery in combat, the war was brought to an immediate end!",0ah,0dh,0
notearlyend byte "As the Anunnaki were not crushed in defeat, the war rages on for centuries to come!",0ah,0dh,0

;VARIABLE KEEPING TRACK OF WHETHER PLAYER IS VET STATUS 1 yet or not
vetStatus dword 0

;VARIABLE STORING PLAYER'S NAME
getName byte "                 ",0ah,0dh,0

;VARIABLE THAT CAN BE SET TO SPECIFIC NUMBER AND USED TO PORT CHARACTER TO DIFFERENT ROOMS SUCH AS AFTER A DEATH
currentroom dword 0

;VARIABLE THAT WILL TAKE IN PLAYER'S CHOICE
menuChoice dword 0

;VARIABLE THAT WILL TELL WHICH MISSION YOU ARE ON 0-9
missionChapter dword 0

;THESE VARIABLES WILL TELL WHEN A PLAYER HAS LOST ALL THEIR HEALTH AND DIES
statusHealth dword 1

;VARIABLE FOR ACTION ENCOUNTERS
actionChoice dword 0

;VARIABLES FOR KEEPING TRACK OF PLAYER DEATHS AND KILLS
deaths dword 0
numKills dword 0

;VARIABLE THAT FOLLOWS THE NUMBER OF TIGER PILOTS YOU HELPED SAVE
savedPilots dword 0

;VARIABLE THAT PROVIDES ONE ENCOUNTER WITH ALEXANDRIA REGULAR QUARTERS AFTER THAT
capEntry dword 0
peaceful dword 0
love dword 0

;VARIABLE THAT KEEPS TRACK OF ENTRIES TO THE PILOT'S QUARTERS
pilotQEntry dword 0

;SHIP
killsDisp byte "-KILLS-		-DEATHS-", 0ah,0dh,0
killsSpacing byte "		",0
killsSpacing2 byte "		",0ah,0dh,0
line byte "           _",0ah,0dh,0
line1 byte "          / \",0ah,0dh,0
line2 byte "         /   \",0ah,0dh,0
line3 byte "         |   |",0ah,0dh,0
line4 byte "         | O |",0ah,0dh,0
line5 byte "       --|   |--",0ah,0dh,0
line6 byte "      |  |   |  |",0ah,0dh,0
line7 byte "     /   |   |   \",0ah,0dh,0
line8 byte "    /    | | |    \",0ah,0dh,0
line9 byte "   /_ _ _|_|_|_ _ _\",0ah,0dh,0
line10 byte "       |__| |__|" ,0ah,0dh,0

;SHIP DESTROYED!
line20 byte "           _",0ah,0dh,0
line21 byte "     \    / \   /",0ah,0dh,0
line22 byte "    --   /   \  --",0ah,0dh,0
line23 byte "  --     |   |    --",0ah,0dh,0
line24 byte " --      | O |     --",0ah,0dh,0
line25 byte "       --    |   |   --",0ah,0dh,0
line26 byte "      |  \    |   |     |",0ah,0dh,0
line27 byte "     /     \  |   |      \",0ah,0dh,0
line28 byte "    /       \ | | |       \",0ah,0dh,0
line29 byte "   /_ _ _   | |_|_|   _ _ _\",0ah,0dh,0
line210 byte "       |__| |__|" ,0ah,0dh,0

;TIGER CLAW
TC1 byte "                                    _______",0ah,0dh,0
TC2 byte "                                   /___    |",0ah,0dh,0
TC3 byte "              \   \  \  \	  //////|  |",0ah,0dh,0
TC4 byte "               i   i  i   i      ///////||====",0ah,0dh,0
TC5 byte "   /=====================================|----|",0ah,0dh,0
TC6 byte "  / o  o  o   o   o    o     ______      |----|",0ah,0dh,0
TC7 byte " / 0   0   0   0   0   0    [______]     |====",0ah,0dh,0
TC8 byte " =======================================/",0ah,0dh,0

;TIGER CLAW DESTROYED
TCD1 byte "                                    _______",0ah,0dh,0
TCD2 byte "                                   /___    |",0ah,0dh,0
TCD3 byte "                         	  //////|  |",0ah,0dh,0
TCD4 byte "               X   X  X   X      ///////||====",0ah,0dh,0
TCD5 byte "   /======================>   <===============|----|",0ah,0dh,0
TCD6 byte "  / o  o  o   o   o    o >    <   ______      |----|",0ah,0dh,0
TCD7 byte " / 0   0   0   0   0   0   > <   [______]     |====",0ah,0dh,0
TCD8 byte " ==========================  > <=============/",0ah,0dh,0

.code

fighterDisp proc
	call clrscr
	mov edx, offset killsDisp
	call writestring
	mov eax, numKills
	call writeInt
	mov edx, offset killsSpacing
	call writeString
	mov eax, deaths
	call writeInt
	mov edx, offset line
	call writestring
	mov edx, offset line1
	call writestring
	mov edx, offset line2
	call writestring
	mov edx, offset line3
	call writestring
	mov edx, offset line4
	call writestring
	mov edx, offset line5
	call writestring
	mov edx, offset line6
	call writestring
	mov edx, offset line7
	call writestring
	mov edx, offset line8
	call writestring
	mov edx, offset line9
	call writestring
	mov edx, offset line10
	call writestring
	call readint
ret
fighterDisp endp

fighterDestroyed proc
	call clrscr
	mov edx, offset line20
	call writestring
	mov edx, offset line21
	call writestring
	mov edx, offset line22
	call writestring
	mov edx, offset line23
	call writestring
	mov edx, offset line24
	call writestring
	mov edx, offset line25
	call writestring
	mov edx, offset line26
	call writestring
	mov edx, offset line27
	call writestring
	mov edx, offset line28
	call writestring
	mov edx, offset line29
	call writestring
	mov edx, offset line210
	call writestring
	call readint
ret
fighterDestroyed endp

tigerDisp proc
	mov edx, offset TC1
	call writeString
	mov edx, offset TC2
	call writeString
	mov edx, offset TC3
	call writeString
	mov edx, offset TC4
	call writeString
	mov edx, offset TC5
	call writeString
	mov edx, offset TC6
	call writeString
	mov edx, offset TC7
	call writeString
	mov edx, offset TC8
	call writeString
	call readint
ret
tigerDisp endp

tigerDestroyed proc
	mov eax, red
	call settextcolor
	mov edx, offset TCD1
	call writeString
	mov edx, offset TCD2
	call writeString
	mov edx, offset TCD3
	call writeString
	mov edx, offset TCD4
	call writeString
	mov edx, offset TCD5
	call writeString
	mov edx, offset TCD6
	call writeString
	mov edx, offset TCD7
	call writeString
	mov edx, offset TCD8
	call writeString
	call readint
	mov eax, white
	call settextcolor
ret
tigerDestroyed endp

prisonerDisp proc
	call clrscr
	mov eax, yellow
	call settextcolor
	mov edx, offset prisoner1
	call writeString
	mov eax, white
	call settextcolor
	mov edx, offset prisoner2
	call writeString
	mov edx, offset prisoner3
	call writeString
	mov edx, offset prisoner4
	call writeString
	mov edx, offset prisoner5
	call writeString
	mov edx, offset prisoner6
	call writeString
	mov edx, offset prisoner7
	call writeString
	mov edx, offset prisoner8
	call writeString
ret
prisonerDisp endp

block proc
	call clrscr
	mov eax, green
	call settextcolor
	mov edx, offset needVetStatus
	call writestring
	mov edx, offset needVetStatus2
	call writestring
	mov edx, offset needVetStatus3
	call writestring
	call readint
ret
block endp

death proc
	call clrscr
	inc deaths
	call fighterDestroyed
	mov edx, offset deathMsg
	call writestring
	mov edx, offset deathMsg2
	call writestring
	mov edx, offset deathMsg3
	call writestring
	call readint
ret
death endp

tigerDeath proc
	call clrscr
	inc deaths
	call tigerDestroyed
	mov edx, offset deathMsg
	call writestring
	mov edx, offset deathMsg2
	call writestring
	mov edx, offset deathMsg3
	call writestring
	call readint
ret
tigerDeath endp

vetIncrease proc
	call clrscr
	inc vetStatus
	mov edx, offset congratulations1
	call writestring
	mov edx, offset congratulations2
	call writestring
	call readint
ret
vetIncrease endp

scoreDisp proc
	call clrscr
	mov edx, offset score1
	call writeString
	mov eax, numKills
	call writeInt
	mov edx, offset score2
	call writeString
	mov edx, offset death1
	call writeString
	mov eax, deaths
	call writeInt
	mov edx, offset death2
	call writeString
	mov edx, offset saves1
	call writeString
	mov eax, savedPilots
	call writeInt
	mov edx, offset saves2
	call writeString
ret
scoreDisp endp

finalBriefing proc
	call clrscr
	call tigerDisp
	mov edx, offset finalBrief1
	call writeString
	mov edx, offset finalBrief2
	call writeString
	mov edx, offset finalBrief3
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset finalBrief4
	call writeString
	mov edx, offset finalBrief5
	call writeString
	mov edx, offset finalBrief6
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset finalBrief7
	call writeString
	mov edx, offset finalBrief8
	call writeString
	mov edx, offset finalBrief9
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset finalBrief10
	call writeString
	mov edx, offset finalBrief11
	call writeString
	mov edx, offset finalBrief12
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset finalBrief13
	call writeString
	mov edx, offset finalBrief14
	call writeString
	call readint
	call clrscr
ret
finalBriefing endp

romanceResults proc
	mov eax, love
	cmp eax, 0
		je struckout
	cmp eax, 1
		je lucky

	struckout:
		mov edx, offset coldShoulder
		call writeString
		mov currentRoom, 33
		jmp main
	lucky:
		mov edx, offset casinova
		call writeString
		mov currentRoom, 33
		jmp main
ret
romanceResults endp

battleResults proc
	mov eax, peaceful
	cmp eax, 0
		je earlyWarEnd
	cmp eax, 1
		je foreverWar

	earlyWarEnd:
		mov edx, offset earlyEnd
		call writeString
		mov edx, offset ending
		call writeString
		call readint
		mov currentRoom, 34
		jmp main
	foreverWar:
		mov edx, offset notearlyend
		call writeString
		mov edx, offset ending
		call writeString
		call readint
		mov currentRoom, 34
		jmp main
ret
battleResults endp

Room0 proc
	call Clrscr
	mov eax, yellow
	call settextcolor
	mov	 edx,OFFSET welcomeMsg
	call WriteString
	mov	 edx,OFFSET welcomeMsg1
	call WriteString
	call readint
	call Clrscr
	;Getting player name
	mov edx, offset nameMsg
	call WriteString
	mov ecx, sizeof getName
	mov edx, offset getName
	call readstring
	mov edx, offset intromsg
	call WriteString
	mov edx, offset getName
	call WriteString
	mov edx, offset intromsg1
	call WriteString
	call readint
	call Clrscr
	mov edx, offset intromsg2
	call WriteString
	mov edx, offset intromsg3
	call WriteString
	call readint
	call Clrscr
	mov edx, offset intromsg4
	call WriteString
	mov edx, offset intromsg5
	call WriteString
	call readint
	
	mov currentRoom, 1
	jmp main
ret
Room0 endp

Room1 proc
	call Clrscr
	mov edx, offset time
	mov eax, green
	call settextcolor
	call WriteString
	call readint
	mov eax, yellow
	call settextcolor
	mov edx, offset Commander1
	call WriteString
	mov edx, offset Commander2
	call WriteString
	mov edx, offset Commander3
	call WriteString
	call readint
	call Clrscr
	mov edx, offset Commander4
	call WriteString
	mov edx, offset Commander5
	call WriteString
	mov edx, offset Commander6
	call WriteString
	call readint
	call Clrscr
	mov edx, offset Commander7
	call WriteString
	mov edx, offset Commander8
	call WriteString
	mov edx, offset Commander9
	call WriteString
	call readint
	call Clrscr
	mov edx, offset Commander10
	call WriteString
	mov edx, offset Commander11
	call WriteString
	mov edx, offset Commander12
	call WriteString
	call readint
	call Clrscr
	mov edx, offset Commander13
	call WriteString
	mov edx, offset Commander14
	call WriteString
	mov edx, offset Commander15
	call WriteString
	call readint
	call Clrscr
	mov edx, offset Commander16
	call WriteString
	mov edx, offset Commander17
	call WriteString
	mov edx, offset Commander18
	call WriteString
	mov edx, offset Commander19
	call WriteString
	call readint
	mov currentRoom, 2
	jmp main
ret
Room1 endp

Room2 proc
	call clrscr
	mov edx, offset menuHeadSpace
	call WriteString
	mov eax, red +(white*16) 
	call settextcolor
	mov edx, offset menuHead
	call WriteString
	mov eax, white
	call settextcolor
	mov edx, offset option1
	call WriteString
	mov edx, offset option2
	call WriteString
	mov edx, offset option3
	call WriteString
	mov eax, menuChoice
	call readint

	;pilots quarters
	cmp eax, 1
		je jumptoroom3
	;Hangar
	cmp eax, 2
		je jumptoroom4
	;NEXT MISSION 
	cmp eax, 3
		je jumptoroom5

	jumptoroom3:
		mov currentroom, 3
		jmp main
	jumptoroom4:
		mov currentroom, 4
		jmp main
	jumptoroom5:
		mov currentroom, 5
		jmp main
ret
Room2 endp

Room3 proc
	call clrscr
	mov eax, green 
	call settextcolor
	mov edx, offset nonVet1
	call writeString
	mov edx, offset nonVet2
	call writeString
	call readint

	mov eax, vetStatus
	cmp eax, 0
		je deniedAccess
	cmp eax, 1
		je entry
	cmp eax, 2
		je entry

	deniedAccess:
		mov eax, white
		call settextcolor
		mov edx, offset nonVet3
		call writeString
		mov edx, offset nonVet4
		call writeString
		call readint
		call clrscr
		mov edx, offset nonVet5
		call writeString
		mov edx, offset nonVet6
		call writeString
		call readint
		call block
		mov currentRoom, 2
		jmp main
	entry:
		mov currentRoom, 9
		jmp main
ret
Room3 endp

Room4 proc
	mov eax, vetStatus
	cmp eax, 0
		je deniedAccess
	cmp eax, 1
		je deniedAccess
	cmp eax, 2
		je entry

	deniedAccess:
		call block
		mov currentRoom, 2
		jmp main
	entry:
		mov currentRoom, 13
		jmp main
ret
Room4 endp

;MISSION FINDER
Room5 proc
	mov eax, missionChapter
	cmp eax, 0
		je move2mission1
	cmp eax, 1
		je move2mission2
	cmp eax, 2
		je move2mission3
	cmp eax, 3
		je move2mission4
	cmp eax, 4
		je move2FinalMission5
	move2mission1:
		mov currentRoom, 6
		jmp main
	move2mission2:
		mov currentRoom, 10
		jmp main
	move2mission3:
		mov currentRoom, 14
		jmp main
	move2mission4:
		mov currentRoom, 20
		jmp main
	move2FinalMission5:
		mov currentRoom, 29
		jmp main
ret
Room5 endp

Room6 proc
	call clrscr
	mov eax, green
	call settextcolor
	mov edx, offset mission11
	call writeString
	call readint
	mov eax, yellow
	call settextcolor
	mov edx, offset mission12
	call writeString
	mov edx, offset mission13
	call writeString
	mov edx, offset mission14
	call writeString
	call readint
	call clrscr
	mov edx, offset mission15
	call writeString
	mov edx, offset mission16
	call writeString
	mov edx, offset mission17
	call writeString
	call readint
	call clrscr
	mov edx, offset mission18
	call writeString
	mov edx, offset mission19
	call writeString
	mov edx, offset mission110
	call writeString
	call readint
	call clrscr
	mov eax, white
	call settextcolor
	mov currentRoom, 7
	jmp main
ret
Room6 endp

Room7 proc
	call clrscr
	mov edx, offset mission0Nar1
	call writeString 
	mov edx, offset mission0Nar2
	call writeString
	mov edx, offset mission0Nar3
	call writeString
	call readint
	call clrscr
	mov edx, offset mission0Nar4
	call writeString
	mov edx, offset mission0Nar5
	call writeString
	mov edx, offset mission0Nar6
	call writeString
	mov edx, offset mission0Nar7
	call writeString
	call readint
	call clrscr
	call fighterDisp
	mov edx, offset encounter01
	call writeString
	mov edx, offset encounter02
	call writeString
	call readint
	call clrscr
	call fighterDisp
	mov edx, offset encounter03
	call writeString
	mov edx, offset encounter04
	call writeString
	mov edx, offset encounter05
	call writeString
	mov edx, offset encounter06
	call writeString

	mov eax, actionChoice
	call readint
	cmp eax, 1
		je m1Act1Death
	cmp eax, 2
		je m1Act1pass

	m1Act1Death:
		call fighterDisp
		mov edx, offset encounter0Death1
		call writeString
		mov edx, offset encounter0Death2
		call writeString
		mov edx, offset encounter0Death3
		call writeString
		mov edx, offset encounter0Death4
		call writeString
		call readint
		call death
		call Room7
	m1Act1pass:
		inc numKills
		call fighterDisp
		mov edx, offset encounter0Pass1
		call writeString
		mov edx, offset encounter0Pass2
		call writeString
		mov edx, offset encounter0Pass3
		call writeString
		mov edx, offset encounter0Pass4
		call writeString
		mov edx, offset encounter0Pass5
		call writeString
		call readint
		mov currentRoom, 8
		jmp main
ret
Room7 endp
	
Room8 proc
	call fighterDisp
	call readint
	mov edx, offset encounter021
	call writeString
	mov edx, offset encounter022
	call writeString
	mov edx, offset encounter023
	call writeString
	mov edx, offset encounter024
	call writeString
	mov eax, actionChoice
	call readint

	cmp eax, 1
		je m1Act2Death
	cmp eax, 2
		je m1Act2Pass
	m1Act2Death:
		mov edx, offset encounter02Death1
		call writeString
		mov edx, offset encounter02Death2
		call writeString
		mov edx, offset encounter02Death3
		call writeString
		call readint
		call death
		call clrscr
		call Room8
	m1Act2Pass:
		mov edx, offset encounter02Pass1
		call writeString
		mov edx, offset encounter02Pass2
		call writeString
		mov edx, offset encounter02Pass3
		call writeString
		mov edx, offset encounter02Pass4
		call writeString
		mov edx, offset encounter02Pass5
		call writeString
		call readint
		call clrscr
		inc numKills
		call fighterDisp
		mov edx, offset encounter02Pass6
		call writeString
		mov edx, offset encounter02Pass7
		call writeString
		call readint
		inc missionChapter
		call vetIncrease
		mov currentRoom, 2
		jmp main
ret
Room8 endp

Room9 proc
	call clrscr
	mov eax, pilotQEntry
	cmp eax, 0
		je firstEntry
		jne secondEntry

	firstEntry:
		mov edx, offset pilotQ1
		call writeString
		mov edx, offset pilotQ2
		call writeString
		mov edx, offset pilotQ3
		call writeString
		call readint
		call clrscr
		mov edx, offset pilotQ4
		call writeString
		mov edx, offset pilotQ5
		call writeString
		call readint
		call clrscr
		inc pilotQEntry
		call readint
		mov currentRoom, 2
		jmp main
	secondEntry:
		mov edx, offset Razor1
		call writeString
		mov edx, offset Razor2
		call writeString
		mov edx, offset Razor3
		call writeString
		call readint
		mov currentRoom, 2
		jmp main
ret
Room9 endp

Room10 proc
	mov eax, green
	call settextcolor
	mov edx, offset mission21
	call writeString
	mov eax, yellow
	call settextcolor
	mov edx, offset mission22
	call writeString
	mov edx, offset mission23
	call writeString
	call readint
	call clrscr
	mov edx, offset mission24
	call writeString
	mov edx, offset mission25
	call writeString
	mov edx, offset mission26
	call writeString
	call readint
	call clrscr
	mov edx, offset mission27
	call writeString
	mov edx, offset mission28
	call writeString
	mov edx, offset mission29
	call writeString
	mov edx, offset mission210
	call writeString
	call readint
	call clrscr
	mov currentRoom, 11
	jmp main
ret
Room10 endp

Room11 proc
	mov eax, white
	call settextcolor
	call clrscr
	call fighterDisp
	mov edx, offset mission2Nar1
	call writeString
	mov edx, offset mission2Nar2
	call writeString
	mov edx, offset mission2Nar3
	call writeString
	call readint
	call clrscr
	call fighterDisp
	mov edx, offset mission2Nar4
	call writeString
	mov edx, offset mission2Nar5
	call writeString
	call readint
	call clrscr
	call fighterDisp
	mov edx, offset mission2Encounter0
	call writeString
	mov edx, offset mission2Encounter1
	call writeString
	mov edx, offset mission2Encounter2
	call writeString
	call readint
	call clrscr
	call fighterDisp
	mov edx, offset mission2Encounter3
	call writeString
	mov edx, offset mission2Encounter4
	call writeString
	mov eax, actionChoice
	call readint
	cmp eax, 1
		je M2Act1Death
	cmp eax, 2
		je M2Act1Pass

	M2Act1Death:
		call clrscr
		call fighterDestroyed
		mov edx, offset mission2Death1
		call writeString
		mov edx, offset mission2Death2
		call writeString
		mov edx, offset mission2Death3
		call writeString
		call readint
		call death
		call readint
		call Room11
	M2Act1Pass:
		inc numKills
		inc numKills
		inc numKills
		inc numKills
		inc savedPilots
		call fighterDisp
		mov edx, offset mission2Pass1
		call writeString
		mov edx, offset mission2Pass2
		call writeString
		mov edx, offset mission2Pass3
		call writeString
		mov edx, offset mission2Pass4
		call writeString
		call readint
		mov currentRoom, 12
		jmp main
ret
Room11 endp

Room12 proc
	call fighterDisp
	mov edx, offset mission2Encounter20
	call writeString
	mov edx, offset mission2Encounter21
	call writeString
	mov edx, offset mission2Encounter22
	call writeString
	mov edx, offset mission2Encounter23
	call writeString
	mov edx, offset mission2Encounter24
	call writeString
	mov edx, offset mission2Encounter25
	call writeString
	mov edx, offset mission2Encounter26
	call writeString
	mov eax, actionChoice
	call readint

	cmp eax, 1
		je M2Act2Kill
	cmp eax, 2
		je M2Act2Save
	M2Act2Kill:
		inc numKills
		inc numKills
		inc numKills
		inc numKills
		inc numKills
		inc numKills
		inc missionChapter
		call fighterDisp
		mov edx, offset mission2Kill1
		call writeString
		mov edx, offset mission2Kill2
		call writeString
		mov edx, offset mission2Kill3
		call writeString
		call readint
		call clrscr
		mov edx, offset mission2EncounterEnd1
		call writeString
		mov edx, offset mission2EncounterEnd2
		call writeString
		mov edx, offset mission2EncounterEnd3
		call writeString
		call readint
		call vetIncrease
		mov currentRoom, 2
		jmp main
	M2Act2Save:
		inc numKills
		inc numKills
		inc numKills
		inc numKills
		inc missionChapter
		call readint
		inc savedPilots
		call fighterDisp
		mov edx, offset mission2Save1
		call writeString
		mov edx, offset mission2Save2
		call writeString
		mov edx, offset mission2Save3
		call writeString
		call readint
		call clrscr
		mov edx, offset mission2EncounterEnd1
		call writeString
		mov edx, offset mission2EncounterEnd2
		call writeString
		mov edx, offset mission2EncounterEnd3
		call writeString
		call vetIncrease
		call readint
		call clrscr
		mov currentRoom, 2
		jmp main
ret
Room12 endp

Room13 proc
	call clrscr
	mov edx, offset Alex1
	call writestring
	mov edx, offset getName
	call writestring
	mov edx, offset Alex2
	call writestring
	mov edx, offset Alex21
	call writestring
	call readint
	call clrscr
	mov edx, offset Alex3
	call writestring
	mov edx, offset Alex4
	call writestring
	mov edx, offset Alex5
	call writestring
	call readint
	call clrscr
	mov edx, offset Alex6
	call writestring
	mov edx, offset Alex7
	call writestring
	call readint
	mov currentRoom, 2
	jmp main
ret
Room13 endp

Room14 proc
	mov eax, green
	call settextcolor
	mov edx, offset missionIntro31
	call writeString
	mov eax, yellow
	call settextcolor
	mov edx, offset missionIntro32
	call writeString
	call readint
	call clrscr
	mov edx, offset missionIntro33
	call writeString
	mov edx, offset missionIntro34
	call writeString
	mov edx, offset missionIntro35
	call writeString
	call readint
	call clrscr
	mov edx, offset missionIntro36
	call writeString
	mov edx, offset getName
	call writeString
	mov edx, offset missionIntro37
	call writeString
	call readint
	call clrscr
	mov edx, offset missionIntro38
	call writeString
	mov edx, offset missionIntro39
	call writeString
	mov edx, offset missionIntro310
	call writeString
	call readint
	call clrscr
	mov edx, offset missionIntro311
	call writeString
	mov edx, offset missionIntro312
	call writeString
	mov edx, offset missionIntro313
	call writeString
	mov edx, offset missionIntro314
	call writeString
	call readint
	call clrscr
	mov edx, offset missionIntro315
	call writeString
	mov edx, offset missionIntro316
	call writeString
	mov edx, offset missionIntro317
	call writeString
	call readint
	call clrscr
	mov edx, offset missionIntro318
	call writeString
	mov edx, offset missionIntro319
	call writeString
	mov edx, offset missionIntro320
	call writeString
	call readint
	call clrscr
	mov eax, white
	call settextcolor
	mov currentRoom, 15
	jmp main
ret
Room14 endp

Room15 proc
	call fighterDisp
	mov edx, offset mission3Encounter1
	call writeString
	mov edx, offset mission3Encounter2
	call writeString
	mov edx, offset mission3Encounter3
	call writeString
	call readint
	call clrscr
	mov edx, offset mission3Encounter4
	call writeString
	mov eax, green
	call settextcolor
	mov edx, offset mission3Encounter5
	call writeString
	mov edx, offset mission3Encounter6
	call writeString
	mov edx, offset mission3Encounter7
	call writeString
	call readint
	call clrscr
	mov eax, white
	call settextcolor
	call tigerDisp
	mov edx, offset mission3Encounter8
	call writeString
	mov edx, offset mission3Encounter9
	call writeString
	mov edx, offset mission3Encounter10
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission3Encounter11
	call writeString
	mov edx, offset mission3Encounter12
	call writeString
	mov edx, offset mission3Encounter13
	call writeString
	mov edx, offset mission3Encounter14
	call writeString

	mov eax, actionChoice
	call readint

	cmp eax, 1
		je mission3Pass
	cmp eax, 2
		je mission3Fail

	mission3Pass:
		call fighterDisp
		inc numKills
		inc numKills
		mov edx, offset mission3EncounterPass1
		call writeString
		mov edx, offset mission3EncounterPass2
		call writeString
		mov edx, offset mission3EncounterPass3
		call writeString
		call readint
		call clrscr
		mov edx, offset mission3EncounterPass4
		call writeString
		mov edx, offset mission3EncounterPass5
		call writeString
		call readint
		call clrscr
		call fighterDisp
		mov eax, yellow
		call settextcolor
		mov edx, offset mission3EncounterPass6
		call writeString
		mov edx, offset mission3EncounterPass7
		call writeString
		mov edx, offset mission3EncounterPass8
		call writeString
		call readint
		mov currentRoom, 16
		jmp main
	mission3Fail:
		call tigerDestroyed
		mov edx, offset mission3EncounterFail1
		call writeString
		mov edx, offset mission3EncounterFail2
		call writeString
		mov edx, offset mission3EncounterFail3
		call writeString
		mov edx, offset mission3EncounterFail4
		call writeString
		call readint
		call tigerDeath
		call Room15
ret
Room15 endp

Room16 proc
	mov eax, white
	call settextcolor
	call clrscr
	call fighterDisp
	mov edx, offset mission3Encounter21
	call writeString
	mov edx, offset mission3Encounter22
	call writeString
	mov edx, offset mission3Encounter23
	call writeString
	call readint
	call clrscr
	call fighterDisp
	mov edx, offset mission3Encounter24
	call writeString
	mov edx, offset mission3Encounter25
	call writeString
	mov edx, offset mission3Encounter26
	call writeString
	mov edx, offset mission3Encounter27
	call writeString
	mov edx, offset mission3Encounter28
	call writeString

	mov eax, actionChoice
	call readint
	cmp eax, 1
		je mission32Fail
	cmp eax, 2
		je mission32Pass

	mission32Fail:
		mov edx, offset mission3Fail21
		call writeString
		mov edx, offset mission3Fail22
		call writeString
		call readint
		call death
		call Room16
	mission32Pass:
		call fighterDisp
		mov edx, offset mission3Pass21
		call writeString
		mov edx, offset mission3Pass22
		call writeString
		mov edx, offset mission3Pass23
		call writeString
		mov edx, offset mission3Pass24
		call writeString
		mov edx, offset mission3Pass25
		call writeString
		call readint
		mov currentRoom, 17
		jmp main
ret
Room16 endp

Room17 proc
	mov edx, offset mission3Encounter31
	call writeString
	mov edx, offset mission3Encounter32
	call writeString
	mov edx, offset mission3Encounter33
	call writeString
	call readint
	call clrscr
	mov edx, offset mission3Encounter34
	call writeString
	mov edx, offset mission3Encounter35
	call writeString
	mov edx, offset mission3Encounter36
	call writeString
	
	mov eax, actionChoice
	call readint

	cmp eax, 1
		je M3Act3Aid
	cmp eax, 2
		je M3Act3Turrets
	M3Act3Aid:
		inc savedPilots
		inc numKills
		inc numKills
		call fighterDisp
		mov edx, offset mission3Save1
		call writeString
		mov edx, offset mission3Save2
		call writeString
		mov edx, offset mission3Save3
		call writeString
		mov edx, offset mission3Save4
		call writeString
		mov edx, offset mission3Save5
		call writeString
		call readint
		mov currentRoom, 18
		jmp main
	M3Act3Turrets:
		mov edx, offset mission3Turret1
		call writeString
		mov edx, offset mission3Save3
		call writeString
		mov edx, offset mission3Save4
		call writeString
		mov edx, offset mission3Save5
		call writeString
		call readint
		mov currentRoom, 18
		jmp main
ret
Room17 endp

Room18 proc
	call clrscr
	mov edx, offset mission3TC1
	call writeString
	mov edx, offset mission3TC2
	call writeString
	mov edx, offset mission3TC3
	call writeString
	call readint
	call clrscr
	mov edx, offset mission3TC4
	call writeString
	mov edx, offset mission3TC5
	call writeString
	mov edx, offset mission3TC6
	call writeString
	mov edx, offset mission3TC7
	call writeString

	mov eax, actionChoice
	call readint

	cmp eax, 1
		je badAss
	cmp eax, 2
		je coward

	badAss:
		call tigerDisp
		mov edx, offset mission3TCCaptain1
		call writeString
		mov edx, offset mission3TCCaptain2
		call writeString
		mov edx, offset mission3TCCaptain3
		call writeString
		call readint
		call clrscr
		call tigerDisp
		mov edx, offset mission3TCCaptain4
		call writeString
		mov edx, offset mission3TCCaptain5
		call writeString
		mov edx, offset mission3TCCaptain6
		call writeString
		call readint
		call clrscr
		call tigerDisp
		mov edx, offset mission3TCCaptain7
		call writeString
		mov edx, offset mission3TCCaptain8
		call writeString
		call readint
		inc missionChapter
		mov currentRoom, 19
		jmp main

	coward:
		mov edx, offset mission3TCCoward1
		call writeString
		mov edx, offset mission3TCCoward2
		call writeString
		call readint
		call tigerDeath
		call clrscr
		call Room18

ret
Room18 endp

Room19 proc
	mov edx, offset Earth1
	call writeString
	mov edx, offset Earth2
	call writeString
	mov edx, offset Earth3
	call writeString
	call readint
	call clrscr
	mov edx, offset Earth4
	call writeString
	mov edx, offset Earth5
	call writeString
	mov edx, offset Earth6
	call writeString
	call readint
	call clrscr
	mov edx, offset Earth7
	call writeString
	mov edx, offset Earth8
	call writeString
	mov edx, offset Earth9
	call writeString
	call readint
	call clrscr
	mov edx, offset Earth10
	call writeString
	mov edx, offset Earth11
	call writeString
	mov edx, offset Earth12
	call writeString
	call readint
	call clrscr
	call readint
	call scoreDisp
	call readint
	mov currentRoom, 25
	jmp main
ret
Room19 endp

Room20 proc
	call clrscr
	call tigerDisp
	mov edx, offset Mission4Intro1
	call writestring
	mov edx, offset Mission4Intro2
	call writestring
	mov edx, offset Mission4Intro3
	call writestring
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset Mission4Intro4
	call writestring
	mov edx, offset Mission4Intro5
	call writestring
	mov edx, offset Mission4Intro6
	call writestring
	mov edx, offset Mission4Intro7
	call writestring
	call readint
	call clrscr
	call tigerDisp
	mov currentRoom, 21
	jmp main

ret
Room20 endp

Room21 proc
	call clrscr
	call tigerDisp
	mov edx, offset Mission4Act11
	call writeString
	mov edx, offset Mission4Act12
	call writeString
	mov edx, offset Mission4Act13
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset Mission4Act14
	call writeString
	mov edx, offset Mission4Act15
	call writeString
	mov edx, offset Mission4Act16
	call writeString
	mov edx, offset Mission4Act17
	call writeString

	mov eax, actionChoice
	call readint
	cmp eax, 3
		je Mission4Act1Pass
		jne Mission4Act1Fail
	Mission4Act1Pass:
		call clrscr
		call tigerDisp
		mov edx, offset Mission4Act1Pass1
		call writeString
		mov edx, offset Mission4Act1Pass2
		call writeString
		mov edx, offset Mission4Act1Pass3
		call writeString
		mov edx, offset Mission4Act1Pass4
		call writeString
		call readint
		mov currentRoom, 22
		jmp main
	Mission4Act1Fail:
		mov edx, offset Mission4Act1Fail1
		call writeString
		mov edx, offset Mission4Act1Fail2
		call writeString
		mov edx, offset Mission4Act1Fail3
		call writeString
		call readint
		call clrscr
		call tigerDeath
		call Room21
ret
Room21 endp

Room22 proc
	call prisonerDisp
	call readint
	mov edx, offset Mission4Act21
	call writeString
	mov edx, offset Mission4Act22
	call writeString
	mov edx, offset Mission4Act23
	call writeString
	mov edx, offset Mission4Act24
	call writeString
	call readint
	call clrscr
	call prisonerDisp
	mov edx, offset Mission4Act25
	call writeString
	mov edx, offset Mission4Act26
	call writeString
	mov edx, offset Mission4Act27
	call writeString
	mov edx, offset Mission4Act28
	call writeString

	mov eax, actionChoice
	call readint

	cmp eax, 1
		je nicelose
	cmp eax, 2
		je offerAsylum
	cmp eax, 3
		je Anger

	nicelose:
		call clrscr
		call prisonerDisp
		mov edx, offset Mission4Act2Nice1
		call writeString
		mov edx, offset Mission4Act2Nice2
		call writeString
		mov edx, offset Mission4Act2Nice3
		call writeString
		mov edx, offset Mission4Act2Nice4
		call writeString
		call readint
		call Room22
	offerAsylum:
		call clrscr
		call prisonerDisp
		mov edx, offset Mission4Act2Asylum1
		call writeString
		mov edx, offset Mission4Act2Asylum2
		call writeString
		mov edx, offset Mission4Act2Asylum3
		call writeString
		mov edx, offset Mission4Act2Asylum4
		call writeString
		call readint
		inc missionChapter
		mov currentRoom, 25
		jmp main
	Anger:
		call clrscr
		call prisonerDisp
		mov edx, offset Mission4Act2Aggressor1
		call writeString
		mov edx, offset Mission4Act2Aggressor2
		call writeString
		mov edx, offset Mission4Act2Aggressor3
		call writeString
		call readint
		inc missionChapter
		mov currentRoom, 25
		jmp main
ret
room22 endp

	

Room25 proc
	call clrscr
	mov edx, offset capmenuHeadSpace
	call writeString
	mov edx, offset capmenuHead
	call writeString
	mov edx, offset capoption1
	call writeString
	mov edx, offset capoption2
	call writeString

	mov eax, menuChoice
	call readint
	cmp eax, 1
		je jumptoCapQ
	cmp eax, 2
		je jumptoMissionFinder
	jumptoCapQ:
		mov currentRoom, 26
		jmp main
	jumptoMissionFinder:
		mov currentRoom, 5
		jmp main
ret
Room25 endp

Room26 proc
	mov eax, capEntry
	cmp eax, 0
		je AlexRoom
	cmp eax, 1
		je RegCapRoom
	AlexRoom:
		mov currentRoom, 27
		jmp main
	RegCapRoom:
		mov currentRoom, 28
		jmp main
ret
Room26 endp

Room27 proc
	mov eax, red
	call settextcolor
	call clrscr
	mov edx, offset romance1
	call writestring
	mov edx, offset romance2
	call writeString
	mov edx, offset romance3
	call writestring
	mov edx, offset romance4
	call writeString
	mov eax, white
	call settextcolor
	mov edx, offset response1
	call writestring
	mov edx, offset response2
	call writeString
	mov edx, offset response3
	call writeString

	mov eax, actionChoice
	call readint

	cmp eax, 3
		jl nolovetime
		je lovetime

	nolovetime:
		mov edx, offset responselose1
		call writeString
		call readint
		inc capEntry
		mov currentRoom, 28
		jmp main
	lovetime:
		mov edx, offset responsewin1
		call writeString
		mov edx, offset responsewin2
		call writeString
		mov edx, offset responsewin3
		call writeString
		call readint
		inc love
		inc capEntry
		mov currentRoom, 25
		jmp main
ret
Room27 endp

Room28 proc
	call clrscr
	mov edx, offset captq1
	call writestring
	mov edx, offset captq2
	call writestring
	mov edx, offset captq3
	call writestring
	call readint
	mov currentRoom, 25
	jmp main
ret
Room28 endp

ROOM29 proc
	call clrscr
	mov edx, offset missionChoice1
	call writeString
	mov edx, offset missionChoice2
	call writeString
	mov edx, offset missionChoice3
	call writeString
	mov edx, offset missionChoice4
	call writeString
	mov edx, offset missionChoice5
	call writeString

	mov eax, actionChoice
	call readint

	cmp eax, 1
		je headon
	cmp eax, 2
		je sneak

	headon:
		mov currentRoom, 30
		jmp main
	sneak:
		mov currentRoom, 31
		jmp main
ret
Room29 endp

Room30 proc
	call finalBriefing
	call tigerDisp
	mov edx, offset mission5ACT1
	call writeString
	mov edx, offset mission5ACT2
	call writeString
	mov edx, offset mission5ACT3
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission5ACT4
	call writeString
	mov edx, offset mission5ACT5
	call writeString
	mov edx, offset mission5ACT6
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission5ACT7
	call writeString
	mov edx, offset mission5ACT8
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission5ACT9
	call writeString
	mov edx, offset mission5ACT10
	call writeString
	mov edx, offset mission5ACT11
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission5ACT12
	call writeString
	mov edx, offset mission5ACT13
	call writeString
	mov edx, offset mission5ACT14
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission5ACT15
	call writeString
	mov edx, offset mission5ACT16
	call writeString
	mov edx, offset mission5ACT17
	call writeString
	call readint
	call clrscr
	mov currentRoom, 32
	jmp main
ret
Room30 endp

Room31 proc
	call finalBriefing
	call tigerDisp
	mov edx, offset mission52ACT11
	call writeString
	mov edx, offset mission52ACT22
	call writeString
	mov edx, offset mission52ACT33
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission52ACT44
	call writeString
	mov edx, offset mission52ACT55
	call writeString
	mov edx, offset mission52ACT66
	call writeString
	call readint
	call clrscr
	call tigerDisp
	mov edx, offset mission52ACT77
	call writeString
	mov edx, offset mission52ACT88
	call writeString
	call readint
	call clrscr
	call tigerDestroyed
	mov edx, offset mission52ACT9
	call writeString
	mov edx, offset mission52ACT10
	call writeString
	mov edx, offset mission52ACT011
	call writeString
	call readint
	call clrscr
	call tigerDestroyed
	mov edx, offset mission52ACT12
	call writeString
	mov edx, offset mission52ACT13
	call writeString
	mov edx, offset mission52ACT14
	call writeString
	call readint
	call clrscr
	call tigerDestroyed
	mov edx, offset mission52ACT15
	call writeString
	mov edx, offset mission52ACT16
	call writeString
	mov edx, offset mission52ACT17
	call writeString
	call readint
	call clrscr
	inc peaceful
	mov currentRoom, 32
	jmp main
ret
Room31 endp

room32 proc
	mov edx, offset stats
	call scoreDisp
	call romanceResults
ret
room32 endp

room33 proc
call tigerDisp
	call battleResults
ret
room33 endp


main PROC
;if current room is equal to 0
	mov eax, currentroom
	cmp eax, 0
	je Room1Intro

;if current room is equal to 1
	mov eax, currentRoom
	cmp eax, 1
	je Room1Brief
;if current room is equal to 2 MAIN MENU
	mov eax, currentRoom
	cmp eax, 2
	je Room2Menu
;if current room is equal to 3 LOCKED QUARTERS
	mov eax, currentRoom
	cmp eax, 3
	je Room3Quart
;if current room is equal to 4 LOCKED HANGAR
	mov eax, currentRoom
	cmp eax, 4
	je Room4Hangar
;if current room is equal to 5 MISSION FINDER
	mov eax, currentRoom
	cmp eax, 5
	je Room5FindMission
;if current room is equal to 6 MISSION 1 INTRO
	mov eax, currentRoom
	cmp eax, 6
	je Room6M1Intro
;if current room is equal to 7 MISSION 1 Act 1
	mov eax, currentRoom
	cmp eax, 7
	je Room7M1Act1
;if current room is equal to 8 MISSION 1 Act 2
	mov eax, currentRoom
	cmp eax, 8
	je Room8M1Act2
;if current room is equal to 9 Unlocked Quarters
	mov eax, currentRoom
	cmp eax, 9
	je Room9Quar
;if current room is equal to 10 Mission 2 Intro
	mov eax, currentRoom
	cmp eax, 10
	je Room10M2Intro
;if current room is equal to 11 Mission 2 Act 1
	mov eax, currentRoom
	cmp eax, 11
	je Room11M2Act1
;if current room is equal to 12 Mission 2 Act 2
	mov eax, currentRoom
	cmp eax, 12
	je Room12M2Act2
;if current room is equal to 13 Hangar is unlocked
	mov eax, currentRoom
	cmp eax, 13
	je Room13Hangar
;if current room is equal to 14 Mission 3 Intro
	mov eax, currentRoom
	cmp eax, 14
	je Room14M3Intro
;if current room is equal to 15 Mission 3 Act 1
	mov eax, currentRoom
	cmp eax, 15
	je Room15M3Act1
;if current room is equal to 16 Mission 3 Act 2
	mov eax, currentRoom
	cmp eax, 16
	je Room16M3Act2
;if current room is equal to 17 Mission 3 Act 3
	mov eax, currentRoom
	cmp eax, 17
	je Room17M3Act3
;if Currcent Room is equal to 18 Mission 3 Act 4
	mov eax, currentRoom
	cmp eax, 18
	je Room18M3Act4
;if Currcent Room is equal to 19 You have made Captain!!
	mov eax, currentRoom
	cmp eax, 19
	je Room19Earth
;if Currcent Room is equal to 20 You have made Captain!!
	mov eax, currentRoom
	cmp eax, 20
	je Room20M4Intro
;if Currcent Room is equal to 21 MISSION 4 ACT 1 as Captain!
	mov eax, currentRoom
	cmp eax, 21
	je Room21M4ACT1
	;if Currcent Room is equal to 22 MISSION 4 ACT 2 as Captain!
	mov eax, currentRoom
	cmp eax, 22
	je Room22M4ACT2
;if Currcent Room is equal to 25 Captain's Menu
	mov eax, currentRoom
	cmp eax, 25
	je Room25CapMenu
;if Currcent Room is equal to 26 Captain's Quarters
	mov eax, currentRoom
	cmp eax, 26
	je Room26CapQuart
;if Currcent Room is equal to 27 Alex Encounter
	mov eax, currentRoom
	cmp eax, 27
	je AlexEnc
;if Currcent Room is equal to 28 Reg Cap Room
	mov eax, currentRoom
	cmp eax, 28
	je RegCapRoom
;if Currcent Room is equal to 29 FinalMissionIntro
	mov eax, currentRoom
	cmp eax, 29
	je FinalMissionIntro
;if Currcent Room is equal to 30 FINAL MISSION HEAD ON ATTACK
	mov eax, currentRoom
	cmp eax, 30
	je headONATTACK
;if Currcent Room is equal to 31 FINAL MISSION SNEAK ATTACK
	mov eax, currentRoom
	cmp eax, 31
	je sneakAttack
;if Currcent Room is equal to 32 Display Stats
	mov eax, currentRoom
	cmp eax, 32
	je statRoom
;if Currcent Room is equal to 33 show battle results
	mov eax, currentRoom
	cmp eax, 33
	je showingBattleResults
;if Current Room is equal to 34 EXIT!
	mov eax, currentRoom
	cmp eax, 34
	je done

Room1Intro:
	call Room0
Room1Brief:
	call Room1
Room2Menu:
	call Room2
Room3Quart:
	call Room3
Room4Hangar:
	call Room4
Room5FindMission:
	call Room5
Room6M1Intro:
	call Room6
Room7M1Act1:
	call Room7
Room8M1Act2:
	call Room8
Room9Quar:
	call Room9
Room10M2Intro:
	call Room10
Room11M2Act1:
	call Room11
Room12M2Act2:
	call Room12
Room13Hangar:
	call Room13
Room14M3Intro:
	call Room14
Room15M3Act1:
	call Room15
Room16M3Act2:
	call Room16
Room17M3Act3:
	call Room17
Room18M3Act4:
	call Room18
Room19Earth:
	call Room19
Room20M4Intro:
	call Room20
Room21M4ACT1:
	call Room21
Room22M4ACT2:
	call Room22
Room25CapMenu:
	call Room25
Room26CapQuart:
	call Room26
AlexEnc:
	call Room27
RegCapRoom:
	call Room28
FinalMissionIntro:
	call Room29
headONATTACK:
	call Room30
sneakAttack:
	call Room31
statRoom:
	call Room32
showingBattleResults:
	call Room33

done:
	exit

main ENDP

END main
