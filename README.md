I have some family friends with memory issues who take daily medicines. This makes it difficult for them to recall if they have taken their medication or not. The system I put together helps the individual taking the medication and can be used to let other people know if they have taken their medication.

I put together this workflow using Andrea Donno’s outstanding HA/ESPhome NFC reader, some NFC tag stickers and Node-Red. 

BOM:
 
-	Tag Reader: Build or buy Andrea Donno’s HA/ESPhome NFC reader https://github.com/adonno/tagreader
-	NFS stickers: I bought these on Amazon “THONSEN 30pcs NFC Tags Stickers” (B07MKWHYQK)


Guide:
1) Add your sticker to HA by swiping it on the reader and going to Settings –> Tags
2) I suggest renaming the tag to something meaningful
3) Create an input Boolean helper to toggle
   - Settings –> Devices & Services –> Helpers
   - Create Helper -> Toggle
   - Give it a meaningful name

In Node-Red:
1) Add a Tag Node
2) Add a Call Service Node and connect the two
