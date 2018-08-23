# Search and Destroy v2.0.0 instruction manual

### "xcp" command - target a mob on your 'cp check' list
- **xcp** targets the first available cp mob (i.e. living and location known) on your list.  
- **xcp** \<*n*.**mob**\> targets the *n*th mob on your list, dead or alive.
- **xcp mode \[ht\|qw\|off\]** makes "xcp" do hunt trick, quick where, or nothing after running to an area, while on an area cp.
- Hunt trick works well in most cases, but in others (e.g. 62.princess) it can take while.  Where only one instance exists, quick-where can be faster.
- Unknown mobs can't be targeted because the location hasn't been explored and therefore is missing from your mapper db.  In area cp's, it means you haven't explored the area at all, so you need to use "xrunto" or Aardwolf's "runto" command to run there.  In room cp's it means the room name wasn't found in your mapper db because the area containing it isn't fully explored.  Looking up a map for that area may be helpful.

### "goto" command — run to room within area after getting search results
- **go** runs to first room returned by hunt trick / quick where.
- **go** \<**number**\> runs you to the numbered room.
- **go 0** runs to the area start room (see 'xset mark')
 
### "nx" (next) and "nx-" (back) commands — run to next room in list of results
- **nx** runs you to the next room in the list of results.  If you don't use 'go' first, 'nx' will run to the first result in the list (same as 'go' with no argument)
- **nx-** runs to previous room in case you go too far, or want to backtrack through the room list.

### "ht" (hunt trick) command — exploit cp hunt restrictions to identify a target mob among look-alikes
- **'ht'** runs the hunt trick on whatever cp mob is currently targeted.
- **'ht \<mob\>'** runs hunt trick on all instances of the given mob one by one until it finds your target.
- 'ht <number.mob>' runs hunt trick as above, but starting with the numbered instance (e.g. 2.mob or 8.penguin) instead.  Useful for skipping past no-hunt or similar mobs — these will interrupt hunt trick and cause it to time out or simply fail to locate.  "No-hunt" means hunt returns a "No one by that name" message as if the mob doesn't exist at all.  Normally-huntable mobs return "You seem unable to hunt that target for some reason" when you get it as a cp (or gq) target.
 - 'ht abort', 'hta', and 'ht0' all cancel the hunt trick without returning any results.
---
 
"qw" (quick where) command:
 - 'qw' does 'where' on your current cp target, then looks up the location in the mapper and returns result(s).
 - 'qw <mob>' does 'where' on given mob and returns results.
 - 'qw <number.mob> does 'where' on the numbered instance (e.g. 2.guard or 8.penguin) and returns results.
 - "qw" only searches one mob, not multiple mobs as hunt trick does.
 - "qw" will fail if the mob is flagged no-where, and will fail if the mob is hidden and your character fails the detect roll.
---
  
 
 
