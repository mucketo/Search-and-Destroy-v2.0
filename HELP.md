# Search and Destroy v2.0.0 instruction manual

### campaign: "xcp" command - target a mob on your 'cp check' list and get location
- '**xcp**' targets the first available mob on your cp list and gets possible locations. "Available" means living and location is known.  E.g. the first four mobs on your list are all dead, unknown, and/or both, "xcp" will ignore all of those and target the 5th mob.
- '**xcp** \<*n*\>' targets the *n*th target on your cp list, dead or alive.  If dead, the MUD only ever gives the area name, even if the cp is room, so dead mobs are always handled as if the cp were area.
- '**xcp 0**' clears the current target and its room search results.
- '**xcp mode** \<**ht**\|**qw**\|**off**\>' determines what xcp does after running to an area — "ht", "qw", nothing (area cp's only).  In most cases, setting it to "qw" (quick-where) will find the right mob without having to hunt trick, which is faster.  
- For area cp's, "xcp" first runs to target area.  Upon arrival, it does hunt trick (default) to pick out your cp mob, then does quick-where to get room(s).  If the area has duplicate roomnames, your mob could be in any of them, use 'nx' to check through them.
- For room cp's, "xcp" gets the room and area info from mapper and generates a direct run to that room.  If the same roomname exists in multiple areas, the cp target list builder will generate a list index for each of them, which can be barely noticeable, or flood the whole list with 12 links for one mob.  This is on the list of current problem-solve items and sooner or later will probably be fixed.
- Unknown mobs can't be targeted because the location isn't in your mapper db.  For area cp's, this means you've never been to the area at all.  For room cp's it means you haven't mapped any rooms with that name in any area — in most of these cases you'll have been to the area before, but haven't explored (i.e. mapped) every room.

### "goto" command — run to room within area after getting search results
- '**go**' runs to first room on the list returned by hunt trick / quick where.
- '**go** \<*n*\>' runs to the *n*th room on the list.
- '**go 0**' runs to the area start room (see 'xset mark')

### "ht" (hunt trick) command — leverage cp hunt mechanics to find target mob and location
- '**ht**' runs the hunt trick (ingame: **'help hunt trick'**) on your currently-targeted cp mob.
- '**ht** \<**mobname**\>' runs hunt trick on mobname, 2.mobname, 3.mobname, etc. until it finds the target or fails to do so after testing all instances.
- '**ht** \<*n*.**mobname**\>' runs hunt trick starting with *n*.mob Useful for skipping past no-hunt or similar mobs — these will interrupt hunt trick and cause it to time out or simply fail to locate.  "No-hunt" means hunt returns a "No one by that name" message as if the mob doesn't exist in the area.  Normally-huntable mobs return "You seem unable to hunt that target for some reason" when you get it as a cp (or gq) target.
- '**ht abort**', '**hta**', and '**ht0**' all cancel a hunt trick in progress without returning any results.

### "kk" (quick kill) command:
- '**kk**' tries to kill the current target
- '**xset kk** \<**command**\>' sets quick-kill to attack with the given skill or spell, e.g. , 'xset kk bs', 'xset kk c 541'

### "nx" and "nx-" commands — run to next or previous room in list of results
- '**nx**' runs to the next room in the list of results, after doing 'go'
- '**nx-**' runs to previous room.
- If you don't use 'go' first, 'nx' and 'nx-' will both run to the first room on the list (same as 'go')

### "qw" (quick where) command:
- '**qw**' gets results for your currently-targeted cp mob.
- '**qw** \<**mobname**\>' gets results for given mobname.  Use this when the auto-guesser fails.
- '**qw** \<*n*.**mobname**\>' gets results for *n*.mobname (e.g. 3.fido).
- Note that "qw" searches only one target, unlike hunt trick (whose input looks similar).  Use "xwhere" to 'where' multiple mobname instances.
- "qw" will fail if the mob is flagged no-where, or in a dark room.  It works intermittently on hidden mobs due to your detect roll vs hidden.

### Vidblain navigation
- '**xset vidblain**' turns on Vidblain navigation, which allows one to quickly and easily cross the dark portal into Vidblain.  It also compensates for the portal's reality-distortion and uncertain transit vector and landing room, enabling straightforward travel to Vidblain destinations which would otherwise be tedious at best.
- '**xset vidblain** \<*level*\>' turns off Vidblain navigation when you reach the desired level, typically that of your lowest-level Vidblain area portal.  It does take tier into account, as well.  This is useful because it's always faster to use an area portal to get to Vidblain than to run via the dark portal.

### Window commands - change font size, line spacing, etc.
- '**sdwindow fontsize** \<*n*\>' changes target list font size.  Default is 8.
- '**sdwindow linespace** \<*n*\>' changes target list line spacing.  Default is 14.
- '**sdwindow** \<**off**\|**hide**\|**0**\>' turns the window off and removes it from view.
- '**sdwindow** \<**on**\|**show**\|**1**\>' turns the window on and displays it.
 
