---
title: "The fallback won"
description: "My keyboard's i key died. I wrote a dictionary autocorrect, then a second script to replace it, then a key counter to find out which workaround I actually use. 95% of it is the one I called the backup."
pubDate: "Oct 6 2026"
---

The i key on my keyboard is dead. Across the five days from September 19 to 24 that the counter logged in full, it registered twice, on days when I typed up to 4,432 keys. That's a keyboard with one working i per three days of use, and it's the only letter I've ever had a personal relationship with.

Replacing the keyboard would have taken one purchase. Instead I wrote an autocorrect around a 370,105-word dictionary, then a second script to replace the first one, then a third piece of the same script to count my keystrokes. I'm told this is called engineering.

## The first fix guessed

Version 1 of `i-restore.ahk` watched what I typed, checked each word against the dictionary, and put the missing i back. For three days (September 8 to 10) it logged every fix: 483 of them.

Most were right. `wth` became `with` 41 times and `ths` became `this` 33 times. I felt like a wizard for about a day.

Then `dne` became `dine` 13 times. I meant `done`. `befre` became `befire` and `sme` became `sime`, six times each. Further down the log, `mstly` became `mistily` four times and `lks` became `ilks` four times, and I'd like it noted that I have never once wanted either word. By my rough count about 60 of the 483 fixes were plainly wrong, and the script reported every one with total confidence. The o key was dropping too, and the script had no way to know that. It only knew how to add an i, so it added one.

`dine` is a real word, so nothing in the script could tell it was wrong. A dictionary check says a word exists. It can't say whether I meant it. A guesser answers with the same confidence whether or not it has the information, which is the failure I wrote about in the Luddite post, and I'd just built a small one. I wrote that essay and then immediately did the thing in it, which I'd call a personal best.

## Two deterministic inputs

Version 5 dropped the dictionary. Now I type the i myself, one of two ways:

- Right Alt sends i (Shift+Right Alt sends I).
- Typing `kj` anywhere, even mid-word, turns into i, so "write" is `wrkjte` and "I think" is `Kj thkjnk`.

Yes, it looks like a cat walked across the keyboard. Right Alt was meant to be the main input. `kj` was the fallback for when my thumb was somewhere else.

The first version's controls were F6, F7 and F11 hotkeys, which collided with Total Commander, and my hands know those keys better than they'll ever know a script. Everything moved to the tray menu. Then I added one global toggle, Ctrl+Alt+Shift+F8, which I haven't committed yet. So the commit message that says "no global hotkeys left" is now technically lying, and I'm leaving it there.

## Then I counted

The script also tallies keys per day into a CSV, so I'd pick remaps from data instead of vibes. Here's every day it has logged:

| Date | Right Alt → i | kj → i |
| --- | ---: | ---: |
| Sep 19 | 97 | 3 |
| Sep 20 | 34 | 221 |
| Sep 21 | 77 | 656 |
| Sep 22 | 17 | 959 |
| Sep 23 | 0 | 650 |
| Sep 24 | 26 | 539 |
| Sep 25 | 13 | 497 |
| Sep 26 | 8 | 284 |
| Sep 27 | 4 | 342 |
| Sep 28 | 19 | 264 |
| Sep 29 | 5 | 756 |
| Sep 30 | 0 | 535 |
| Oct 1 | 2 | 368 |
| Oct 2 | 0 | 16 |
| Oct 3 | 17 | 251 |
| Oct 4 | 2 | 248 |
| Oct 5 | 0 | 2 |
| Oct 6 | 1 | 58 |

The plan said Right Alt. The CSV said otherwise by the second day: on September 20, `kj` beat it 221 to 34. It won 17 of the 18 days, and the one it lost was the day the fallback was twelve minutes old. Through today the totals are 322 for Right Alt and 6,649 for `kj`, so the backup does 95% of the work and the main input has been doing community theatre.

`kj` is on the home row, and my fingers are already there. Right Alt means moving a thumb, and I stopped bothering. That's the whole finding. I'd like it to be more sophisticated, and I'd like a refund on the thumb.

Six of those days have no total row, because the part of the script that counts every keystroke quietly stopped, and I haven't worked out why. So my keystroke counter has a keystroke-counting problem. The `kj` and Right Alt counts come from a different part of the script and are fine.

The counts show what I did, not what's better. They can't tell me whether `kj` slows me down. That would take a timer, and I'm not building a fourth script.

## What I'd keep

Count before you optimise. My plan said Right Alt, and the CSV had overruled it by day two.

The dictionary version failed for the same reason a lot of generated code fails: it filled the gap with the most likely answer, and likely isn't right.

Through October 6, Right Alt has 322 presses and `kj` has 6,649.