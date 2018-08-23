# Search and Destroy v2.0.0 instruction manual

### "xcp" command:
- **xcp** targets the first available cp mob (i.e. living and location known) on your list.  
- **xcp** *n*.**mob** targets the *n*th mob on your list, dead or alive.
- **xcp mode \[ht\|qw\|off\]** makes "xcp" do hunt trick, quick where, or nothing upon running to an area.
- Unknown location (i.e. room not mapped) mobs can't be targeted, because S&D needs the area or room id to find them.  When you target a cp mob, it will be highlighted in the GUI window.


"goto" command:
 - 'go' runs to first room out of any results returned by hunt trick / quick where.
 - 'go <number>' runs you to the numbered room.
---
 
"nx" (next) and "nx-" (back) commands:
 - 'nx' runs you to the next room in the list of results
 - 'nx-' runs to previous room in case you go too far
---
 
"ht" (hunt trick) command:
 - 'ht' runs the hunt trick on whatever cp mob is currently targeted.
 - 'ht <mob>' runs hunt trick on all instances of the given mob one by one until it finds your target.
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
  
 
 
