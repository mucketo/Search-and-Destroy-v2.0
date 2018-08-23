# Search and Destroy v2.0.0 instruction manual

### "xcp" command - target a mob on your 'cp check' list and get location
- **xcp** targets the first available cp mob (i.e. living and location known) on your list.  
- **xcp** \<*n*\> targets the *n*th mob on your list, dead or alive.
- **xcp 0** clears the current target and its room search results.
- **xcp mode** \[**ht**\|**qw**\|**off**\] makes "xcp" do hunt trick, quick where, or nothing after running to an area, while on an area cp.
- Hunt trick works well in most cases, but can be slow (e.g. 62.princess).  Where mob is unique (only 1 instance), hunt trick isn't needed, so quick-where by itself can be faster if your cp gives you multiple unique targets.
- Unknown mobs can't be targeted because the location hasn't been explored and therefore is missing from your mapper db.  In area cp's, it means you haven't explored the area at all, so you need to use "xrunto" or Aardwolf's "runto" command to run there.  In room cp's it means the room name wasn't found in your mapper db because the area containing it isn't fully explored.  Looking up a map for that area may be helpful.

### "goto" command — run to room within area after getting search results
- '**go**' runs to first room on the list returned by hunt trick / quick where.
- '**go**' \<*n*\> runs to the *n*th room on the list.
- '**go 0**' runs to the area start room (see 'xset mark')
 
### "nx" (next) and "nx-" (back) commands — run to next room in list of results
- '**nx**' runs you to the next room in the list of results, after doing 'go'
- '**nx-**' runs to previous room.
- If you don't use 'go' first, 'nx' and 'nx-' will both run to the first room on the list (same as 'go')

### "ht" (hunt trick) command — leverage cp hunt mechanics to identify target mob and find its location
- '**ht**' runs the hunt trick (ingame: **'help hunt trick'**) on your currently-targeted cp mob.
- '**ht** \<**mobname**\>' runs hunt trick on mobname, 2.mobname, 3.mobname, etc. until it finds the target or fails to do so after testing all instances.
- '**ht** \<*n*.**mobname**\>' runs hunt trick starting with *n*.mob Useful for skipping past no-hunt or similar mobs — these will interrupt hunt trick and cause it to time out or simply fail to locate.  "No-hunt" means hunt returns a "No one by that name" message as if the mob doesn't exist at all.  Normally-huntable mobs return "You seem unable to hunt that target for some reason" when you get it as a cp (or gq) target.
- '**ht abort**', '**hta**', and '**ht0**' all cancel a hunt trick in progress without returning any results.
 
###"qw" (quick where) command:
 - '**qw**' gets results for your currently-targeted cp mob.
 - '**qw** \<**mob**\>' gets results for given mob.
 - '**qw** \<*n*.**mob**\>' gets results for *n*.mob (e.g. 3.fido).
 - Somewhat confusingly, the syntax for "qw" is similar to hunt trick, however "qw" searches 
 - "qw" will fail if the mob is flagged no-where, and will fail if the mob is hidden and your character fails the detect roll.
  
 
 
