---
layout: post
title:  "Issuse when using apple watch to unlock Mac"
date:   2020-09-19 7:26:00 +0800
categories: Watch os 7
---
I've finally fixed it! I found a bunch of errors related to "AutoUnlock" in the Console that was hinting to me that there was some invalid state on my Mac with keys and plists not being reset properly. After clearing/resetting them, I can now successfully pair my watchOS 7 Series 3 to macOS 10.15.6.

Steps (follow at your own discretion)
Open "Keychain Access"
In "View", enable "Show Invisible Items"
1600317739824.png
Search for "Auto Unlock"
You should see a whole bunch of application passwords for "Auto Unlock: XXXX's ..."

Select all records and delete (this will reset/disable auto unlock on other Macs if you use multiple Macs)
Whilst still in "Keychain Access", search for "AutoUnlock" (no space)
There should be 4 entries for "tlk" "tlk-nonsync" "classA" "classC"
Screen Shot 2020-09-17 at 1.26.18 pm.png
Select 4 records and delete (don't worry if they re-appear, the system repairs this automatically)
Open "Finder" and navigate to "~/Library/Sharing/AutoUnlock"
There should be two files "ltk.plist" and "pairing-records.plist"
1600313712532.png
Delete both files
Open "System Preferences" and try enabling auto unlock. You may need to enable it twice, the first attempt will fail.