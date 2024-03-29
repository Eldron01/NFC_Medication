# Medication Tracker

I have some family friends with memory issues who take daily medicines. This makes it difficult for them to recall if they have taken their medication or not. The system I put together helps the individual taking the medication and can be used to let other people know if they have taken their medication.

I put together this workflow using Andrea Donno’s outstanding HA/ESPhome NFC reader, some NFC tag stickers and Node-Red. 

![NFC1](/pics/NFC1.jpg)
## BOM
BOM:
 
-	Tag Reader: I am sure there are others, but I liked Andrea's. Build or buy Andrea Donno’s HA/ESPhome NFC reader. Build: https://github.com/adonno/tagreader Buy: https://adonno-crafts.myshopify.com/ 
-	NFC stickers: I bought these on Amazon “THONSEN 30pcs NFC Tags Stickers” (B07MKWHYQK)

## Guide
Guide:
1) Add your sticker to HA by swiping it on the reader and going to Settings –> Tags
2) I suggest renaming the tag to something meaningful
3) Create an input Boolean helper to toggle
   - Settings –> Devices & Services –> Helpers
   - Create Helper -> Toggle
   - Give it a meaningful name

In Node-Red:

1) Add a Tag node and set the Tag to the one you just created in HA
2) Add a Call Service node and connect the two. Set the Call Service node to turn on the Input Boolean you created in HA.
3) Add a an Inject node and set the time to a time before your person is took take their medication. I use 30min. This is to make sure the boolean is off before being turned on by the NFC swipe.
4) Add a Call Service node and connect it to the Inject node you just created. Set the Call Service node to turn off the Input Boolean you created in HA.
5) Add an Inject node and set the time to when you want to receive a notification if the medication is not taken. I use 30min after.
6) Add a Current State node and connect it to the Inject node you just created. Set the node to check your Input Boolean status is off or on. On means they swiped and off means they did not.
7) Add a Call Service node and connect it to the Current State node you just created. Set your notification of choice. I use an IOS push notification.

![NFC1](/Node-Red/NR_1.PNG)

STLs:

I modified the STLs that Andrea created to allow more room for wires and a larger buzzer. I used these buzzers: "uxcell 9mmx5.5mm" (B018I1WBNQ).

## Additonal Ideas
The Node-Red flow could also be modified to turn a light on or off as a visual indication of the medication status. You could also attached it to a matrix display that could read out the status and give a countdown timer. There are a lot of ways HA can be used to help someone.
