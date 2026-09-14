## TallyUp

<img width="763" height="423" alt="Screenshot 2026-09-14 at 6 40 51 AM" src="https://github.com/user-attachments/assets/bf2d125b-7a2c-4d1f-a888-70729ef071a4" />



━━━━⊱⋆⊰━━━━━━━━⊱⋆⊰━━━━

A collaborative counting app I built for my concession stand job — solving the actual problem of two workers counting the same drinks in two different coolers, then having to hand-combine paper tallies afterward.

I worked this job at a concession stand, where before and after every game we count hundreds of beverages across two coolers in less than 40 minutes. Two people usually count in parallel, in different-sized groups (10s, 20s, 40s), then have to manually add up their subtotals — easy to lose track of who counted what, and easy to make an arithmetic mistake combining numbers under time pressure.

TallyUp fixes that: two coworkers join the same session on their own phones, each picks a cooler, taps through their count in whatever groupings they like, and the app combines both coolers' totals live — no one adds anything up by hand.


## Features

- Create a count with an event name, stand name, and a per-cooler product checklist (a drink can exist in Cooler A only, Cooler B only, or both)
- Join a running count with a 6-character code, then pick which cooler you're counting
- Each worker only sees the products that are actually in their cooler
- Tap-to-count with common increments (+1, +6, +10, +12, +20, +24) or a custom group size, plus a remainder entry for whatever's left over
- Undo removes only your own most recent entry, never a coworker's
- Live combined totals across both coolers, synced every few seconds via Firebase
- Separate Count In / Count Out phases, so pre-event and post-event counts stay independent
- A summary screen showing both phases across both coolers at a glance
- Mark a product "done" per cooler once you've finished counting it

## Demo Link 
https://canva.link/a76ig5kvd1si86u 

## Try it yourself 
https://sundarikanag.github.io/tallyup/



## Built With

- HTML / CSS / JavaScript (no framework, no build step)
- Firebase Realtime Database (accessed via plain `fetch()` calls, not the Firebase SDK)
- GitHub Pages for hosting

## What I Learned

This project helped me practice:

- Structuring a multi-screen app in vanilla JavaScript without a framework
- Designing a shared data schema (sessions, workers, entries, completion state) for a small realtime database
- Talking to a cloud database directly over REST instead of an SDK, and understanding the tradeoffs (no built-in offline caching or push listeners — I approximate "realtime" with polling instead)
- Thinking through concurrent writes from multiple users at once, and keeping each worker's undo/edit actions scoped to only their own entries
- The real difference between a prototype that works for one person and one that has to stay correct when two people are using it on two different phones at the same time

## Status

Built and tested end-to-end across two devices simultaneously. Currently piloting it with coworkers at my concession stand job this season.

## Future Improvements

- Firebase Authentication + real database security rules (currently open read/write for pilot testing)
- Support for more than two coolers/sections
- A live "who's counting what right now" presence indicator
- Exportable/printable summary for handing off to a manager
- True realtime updates via Firebase listeners instead of polling
