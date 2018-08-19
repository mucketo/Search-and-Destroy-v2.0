# Search and Destroy v2.0.0 — 19 Aug 2018



# Search and Destroy v2.0 beta — 11 Aug 2018

- Beta revision 9 uploaded at 03:05 on 11 Aug 2018

Good morning ninjas and ninja fans, I have finally gotten around to merging the original three plugins (Mapper Extender, Search and Destroy, and Search and Destroy GUI) into a single plugin.  Version 2.0 should do everything that the originals did, while suffering none of the drawbacks.

As the beta release of version 2.0 there are no new features yet.  I expect this to have unresolved problems, but I've been doing campaigns with it over the last day and nothing's really caught fire.  Feel free to give it a try and let me know what you think!

Here is the outline of what's been done up to this point:

 - Removed the plugin-broadcast interface and its supporting code and replaced with conventional variable assignments and function calls.  Three separate plugins receiving mostly the same data made for a lot of redundant/triplicated code and CPU work.  All gone now.
 
 - Removed most of the redundant/duplicate code resulting from separate plugins having similar functions and utilities.  The    
   important ones are pretty much taken care of, but given time constraints and exhaustion from work I had to prioritize a bit
   and likely didn't get it all.  I'll clear up the rest in the next update.
   
 - Fixed duplicate alias/trigger names, of which there were a few.  Duplicate pattern matches should all be merged and the excess 
   removed.
   
 - The plugin help text is not working.  It took up a lot of space and was making it harder to browse the file so I cut it out and 
   put it in a text file for later.  Also removed the help button from the window because it wasn't really useful.  I'd like to 
   redesign the window layout and features but am not sure what to do yet.
   
 - Rearranged the XML code for aliases and triggers to be more compact, reducing file length by some 150 lines.  It makes it a lot 
   easier to find and fix things.
 
 - Default start rooms for Ooku and Arboretum have been added.
 
 - I reworked init_plugin and there shouldn't be any problems at the login screen or login process.  Let me know if there are.
 
 - Since version 2 is an entirely new plugin, it has a different plugin ID which means that user-set area start rooms and 
   similar saved things will not carry over.  It's not feasible to try combining three sets of saved settings and ensure there 
   are no problems.  The new version is basically incompatible with the old.  I regret any inconvenience arising from this.
   
That's pretty much it for now.  Please let me know when things break so I can get them handled, and keep in mind that this is indeed a beta version which might crash or glitch on you.  General comments, suggestions, and questions are also welcome, as always.  The beta will run for a couple of weeks to a month, depending on feedback and further testing.  Good luck, and thanks for all of your support and encouragement!

# Search and Destroy 1.3.5 - 7 April 2018
Happy new year, ninjas and other fans of mine!  I'm happy to report that 1.3.5 is a really nice update.  Without further ado, here's what's new:

 - The process for getting cp target data has been redesigned.  The cp type check is the primary
    director of process flow and occurs after cp check, rather than during.  The number of required
    mapper DB operations is reduced by roughly half and all of the post-process filtering has been
    eliminated, further improving performance and reducing ambiguity.  This should finally put an
    end to most of the display and link-related problems that have plagued S&D since the beginning.
    
    As of April 27 the recent crashes and a few other issues discovered during the investigation
    should be fixed.  I guess we'll find out.  Let me know if not.
  
  Additional process improvements, bug fixes, and other changes include:
 
 - Unknown target links were glitchier than expected but Mapper Extender and GUI should now handle them correctly.
 
 - Adjusted the room cp filtering parameters to deal with high-level mobs in low level areas.  For
    example, living wall in Descent to Hell would come up as unknown because it's a level 85 mob in
    a level 35 to 55 zone.  Most of these should now be handled correctly.  A side effect of this
    change is that you'll probably see more 'redundant' room cp links than before.  Unfortunately,
    using the area level ranges for filtering is sub-optimal and given the number of exceptions and
    overly broad (or just flat out wrong) level ranges, the only good way to filter would be to
    store data for every mob, but at that point you're looking at something way more involved.
	
 - Cp type check moved to Search and Destroy, using cp info to get the data.  This removes the 
    escalating probability of mis-identification, which can happen if cp check is used instead.
	The cp level taken is also recorded at this time.
   
 - Room names containing parentheses are now matched correctly.
  
 - Mapper Extender should no longer crash due to missing area or mapper data (e.g. as happens when new areas
    are added to the game).
 
 - The area indexing process is only allowed run when your character state is 3 (standing), 8 (fighting), 9 (asleep), or 11 (sitting or resting).  This solves any issues related to the process running at inappropriate times, e.g. while logging in, afk, or writing a note.

 - Cp check output for room cp's is now easier to read.
  
 - Dead targets on room cp's now display correctly.

 - Xcp with no argument would always target the first mob in the list, even if dead, which could
    prove unhelpful.  Xcp now targets the first mob that is alive.
    
 - Xcp also skips over targets whose locations are unknown.
	
 - Xcp can now be set to automatically hunt trick, quick where, or do nothing after running to
    the target area (on area cp's).  The syntax is 'xcp mode [ht|qw|off]'.  The default has always
    been hunt trick, but sometimes that's not ideal and this allows some flexibility.  Has no 
	effect on room cp's since they directly state the room name.

 - Improved quest handling.  S&D has always worked with quests, but 'xcp' would overwrite the quest
    info and cause it to be lost.  The command 'xq' has been added which re-targets your quest mob.
 
 - Auto noexp has been updated to use GMCP config, making it about as reliable as it can get.
  
 - Removed a lot of dead, orphaned, or otherwise obsolete code and triggers; improved regexp for
    various triggers, etc.; and other general cleanup.

# Search and Destroy 1.3.4 - 9 December 2017
Happy birthday, ninjas everywhere.  We have a new update, which is more of a bug fix update than a feature update.  But 
there are some new things, and hopefully some of the glitchiness in 1.3.3 has gone away and not been replaced.

Search and Destroy:
 - Settings like noexp, etc. will be saved between sessions/installations.

 - New feature: xwhere.  It lets you 'where' multiple mobs quickly, which can be useful
   in many different situations.  'xwhere 10 mob' does 'where' starting at 1.mob and
   counting to 10.  'xwhere 10 20 mob' does 'where' starting at 10 and counting to 20.
   Previously I would do this using a command-line "for" loop, but got tired of typing
   them out and just wrote it into an actual command.

Mapper Extender:
- "xrunto" only works with the area keyword.  It no longer tries to match the area long
   name, or to guess the start room.  It still does partial matches on the area keyword.
   If no match is found, it will pull up 'area keywords <your text>' and display any
   matches.

   The problem is that the area keywords and long names have too many words in common
   and with partial matches it gets even worse.  This is why 'xrt desert' or whatever
   would sometimes go to the wrong area.  The "runto roulette" / go to random room in
   area problem can range from annoying to deadly.  I don't have a better answer yet,
   but for now, limiting input to areaid/keyword eliminates the errors and gives
   consistent performance.
 
- Added default start rooms for open clan halls, manor areas, and some other areas.

- Room cp links to non-questable (clan, manor, etc.) areas are no longer displayed.

- Room links are now filtered according to the level the cp was taken, rather than the
   current player level.

- Fixed a bug which spammed GMCP requests and broke target detection upon plugin install.

- Fixed a bug where 'xcp' sometimes sends you to the wrong target while on a room cp.

Mapper Extender GUI:
- 'xset' and 'xgui' are equivalent for window settings and commands.

- Font size and line spacing are saved between sessions/installations.

- Much-improved window resizing and performance.  Special thanks to Ylar for this!
   It's a bit glitchy, probably because fiddled with the code to address some minor
   details, but most of the time it isn't apparent.  To resize the window, use the
   widgit thing in the lower right corner, as with the standard Aardmush plugins.

- Re-added maximize and minimize window functions as right-click menu options.

Once again, thanks to everyone who has given me your support in this project, I've
learned a lot in working on it and I hope you all enjoy the results.  Thanks for all
the ideas, contributions, and technical advice.

To those who haven't supported me (of which there are a few people) your criticism
is valuable because it keeps me evaluating, and helps me moderate my enthusiasm so
that I don't lose perspective or get too carried away.  Thanks for that.

Happy searching and destroying, ninjas of aard.


# Search and Destroy 1.3.3 - 22 October 2017
Good morning ninjas, we have a new update today.  As usual, if there are any problems, let me know and I'll do
what I can.  Here we go:

- The campaign type detect should correctly identify the cp type when a room and the area 
  it's in have the same name.

- The display glitch where targets don't show up should be fixed.  Let me know if not.

- The current 'xcp' target is now highlighted in the GUI window.

- Room cp targets are now sorted by area.  Special thanks to Fiendish for helping me with this.

- The font size and line spacing can now be changed in the GUI window.  The commands are 'xgui fontsize \<number>'
  and 'xgui linespace \<number>'.  Defaults are 8 and 15, respectively.

- The cp list font will change between Lucida Sans Unicode and Segoe depending on cp type.  Segoe is a bit
  narrower than Lucida and it might allow more room cp text to fit in the window.  Xgui fontsize works on
  both.  

- "nx" and "nx-" now do 'quick scan' after the run.

- Removed all but the "?" button from the window title bar.  I never used them, did anyone else?

- Added "send to front/back" to the window title bar as a right-click menu.  The title bar buttons (including
  'bring to front') usually got covered up when sending the window to back, making them un-clickable.  Not helpful.
  As long as you can right click the title bar, it's easy to bring the window to front again.

- Finally removed the 'reset gui' commands and related code.  Their only purpose was to bring the window back after it glitched out and left the screen, but since that bug no longer exists there is nothing to reset anymore.

- Removed much of the spam that happens on Mapper Extender install, and when you take a new cp.  Also removed some
  old debugging output as well as "cp ch" and other echoes when the plugin sends commands to the mud.  The output
  looks and feels a lot cleaner now.

- Continued the trend of more code clean-up, regexp simplification, neater output appearance, and all that.

That's all for now.  Happy searching and destroying, and thanks for all your support!


# Search and Destroy 1.3.2 - 22 September 2017
- Added 'xcp' as an alias for 'xcp 1'.

- 'xcp' will retry if it fails because of "no object or data busy".  

- If you hit 'nx' too many times, you can go back by using 'nx-' or right-clicking
  the 'nx' button.

- Enlarged GUI buttons to make them easier to click.

- S&D now detects which type of CP is active.

- Target list is now filtered according to cp type.  This removes most of the extra 
list items displayed (mostly in area cp's) when a target location is both a valid 
area and room name.  Room cp's can still generate multiple links per target (as they
should) if the same room name exists in different areas.

- Simplified 'xcp' and 'cp check' syntax in Mapper Extender.  I get what WinkleWinkle
was doing with these crazy regexp's, but most wind up being complexity for their 
own sake.  Fiendish certainly doesn't use them in his scripts, and I can see why.
Unless anyone actually requires the complex versions, I'm looking at gutting the 
command interface and making it simpler and more consistent.

- Removed a lot of spammy text output (old debugging messages, etc.) plus other 
general cleaning-up. 

Lastly, on short notice, I'm implementing a change to correct a glaring omission that was brought
to my attention.  A few other things I was working on also made it in.  Hopefully they
aren't horribly broken:

- Hunt trick should now work for Navigators hunting through portals.  Previously, 
it would break because the portal hunt message didn't match the regexp.  It looks
functional to me now, but I'm not a navigator so please let me know if and when this
breaks.  If it works, it should remove the need to patch it yourself.  

- Navigator auto-hunt will be trickier.  For now, when you try to hunt through a portal, you
will be prompted to enter the portal and then autohunt again.

- The autohunt command interface has been redone, in line with the general simplification
plan mentioned above.  If anything goes wrong with it, let me know.  This wasn't rushed,
exactly, it just hasn't had as long to be tested as other things, but I fixed all of the
issues that I was able to identify.  Type "search help" to see the new command syntax.

# Search and Destroy 1.3.1 - 14 June 2017
Bug fixes:
- hunt trick will now correctly terminate after trying to hunt something that doesn't exist.
- hunt trick will now correctly terminate if you try to do it while resting, sitting, or sleeping.
- hunt trick and quick-where will no longer use 1.mob for its first
try.  It will just do 'hunt mob' or 'where mob'.  I don't think it matters which is used,
it seems to target the same thing either way, I just didn't like 1.mob.  If problems with
it let me know and I can change it back.
- campaign target window will now populate when taking a CP from a questor.  Before, it would
only populate when requesting from Commander Barcett.
- the problem with 'xrunto' sometimes taking you to a random-ish room is mostly fixed. If 
xrunto takes you to the wrong area, e.g. Fantasy Fields instead of 'fields' (Killing Fields)
go to (in this case) Killing Fields and 'xset mark' the start room again and that should fix it.

New feature:
- Auto-noexp!  When you're at low TNL and you can take a campaign at your current level, 
 it will turn on noexp and prevent you from over-levelling and missing a campaign.

   When plugin is installed, it defaults to off.  To turn it on, do 'xset noexp (amount)'.
 If you're on a CP but can take a new one at your current level, noexp will kick on 
 when your TNL drops below the given amount.  Noexp will kick back off after you finish
 your current CP and then go and take another one.  You can also toggle noexp off 
 manually via 'noexp' as usual.  For low levels I suggest setting it at 1000 TNL or so,
 and around 500 when you get higher and mobs award less XP.  You may need to go higher
 if there's a lot of double stacking with your daily blessing bonus.
 
# Search and Destroy 1.3.0 - 31 May 2017
- Search and Destroy is once again being actively worked on, and this time I'm in charge!
Good times are ahead!
- The bug causing the GUI window to 'jump' and leave the screen when you try to move it has
been fixed.  It is no longer possible for the window to get lost, stuck, or otherwise go
beyond the edges of the screen.
   
  

