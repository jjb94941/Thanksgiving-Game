# Family Field Guide

A phone game for a family group (about 3 to 12 players). Each person plays on their own phone. One person hosts; everyone else joins with a six-letter code.

## How to play

1. **Host:** open the site, type the player names (one per line), and tap **Create game**. Share the code or the link shown in the address bar.
2. **Everyone:** open the site, tap **Join**, enter the code, and tap your own name.
3. **Host:** tap **Make teams and start writing cards** once everyone has joined.
4. **Everyone:** write three cards privately on your own phone: a strength, a quirk, and a fact most people don't know.
5. **Host:** tap **Start Round 1** (needs at least 3 people's cards).

Rounds:
- **Round 1, Who Is This?** The fact cards are read aloud and the group guesses who wrote each one. The host reveals the author and awards a point to the team that guessed first.
- **Round 2, Team Charades.** Teams take turns acting out strength and quirk cards in 60-second turns. Only the acting team sees the card. "Got it" scores a point; "Pass" skips.
- **Round 3, Family Awards.** The host taps the winner of each award.

Final scores and the awards list appear at the end.

## Setup (one time)

This is a static site with no build step. It uses a Supabase project for shared game state.

1. Put `index.html` and `config.js` in the root of this repository.
2. In GitHub, go to **Settings → Pages**, choose the `main` branch and the root folder, and save. The site appears at `https://jjb94941.github.io/thanksgiving-game/`.
3. The Supabase URL and public key are in `config.js`. The database table `games` is already created in the "Family Field Guide" project.

## Notes and limits

- The host's phone has the controls for advancing the game. If the host's phone is lost, the game can't advance; start a new game instead.
- The public key in `config.js` is meant to be public. The table's current rules let anyone with that key read or change any game. That's fine for a family game with an unguessable six-letter code, but tighter rules can be added later.
- Game state lives in the database, so refreshing a phone's browser keeps everyone in the game. Use **Leave game on this phone** to exit.
