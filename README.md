# Family Field Guide

A phone game for a family group (about 3 to 12 players). Each person plays on their own phone, with no shouting. One person hosts; everyone else joins with a six-letter code. Plan for about 45 to 70 minutes with six players.

## How to play

1. **Host:** open the site, type the player names (one per line), and tap **Create game**. Share the code or the link in the address bar.
2. **Everyone:** open the site, tap **Join**, enter the code, and tap your own name. The host can also tap their name.
3. **Host:** tap **Start the questionnaire**. Each player gets a number (1, 2, 3…) at random.
4. **Everyone:** answer the twelve questions about yourself on your own phone. Tap every answer that fits you, or tap **None of the above**, which clears the other picks. Tapping a regular answer clears **None of the above**. The host starts the game once at least three people have finished. Anyone who hasn't finished sits out.

Each player starts with one **Double** (doubles the points from one vote) and one **Lifeline** (removes two wrong answers from one guess). Each can be used once per game.

### The four chapters

- **Chapter 1, Who Is This?** A three-step clue ladder about one player. Clue 1 appears at once, clue 2 after 15 seconds, and clue 3 after 30 seconds. Guessing during clue 1 is worth 3 points, clue 2 is worth 2, and clue 3 is worth 1. A wrong guess costs 1 point. The ladder closes after 60 seconds.
- **Chapter 2, How Well Do You Know Me?** A question about one player. Their answer may include more than one choice, and a guess is right if it matches any of them. Before you answer, bet 1, 2, or 3 points. A right answer gains the bet, and a wrong one loses it, so scores can go negative. The Lifeline removes two wrong choices, and never a right one.
- **Chapter 3, Would You Rather.** Everyone picks one of two options. You score 1 point if you match the majority. A tie scores nothing.
- **Chapter 4, Showdown.** The top three players by score become the finalists. Only they vote on three clue ladders, and every point is doubled. Everyone else watches.

Votes are revealed when everyone who can vote has voted, or when the host taps **Reveal now**. Ladders also close on their own after 60 seconds. The host taps **Start Chapter** between chapters.

## Setup (one time)

This is a static site with no build step. It uses a Supabase project for shared game state.

1. Put `index.html`, `config.js`, and `README.md` in the root of this repository.
2. In GitHub, go to **Settings → Pages**, choose the `main` branch and the root folder, and save. The site appears at `https://jjb94941.github.io/Thanksgiving-Game/`.
3. The Supabase URL and public key are in `config.js`. The database table `games` is already created in the "Family Field Guide" project.

## Notes and limits

- The host's phone has the controls that move the game forward. If the host's phone is lost, start a new game.
- Votes are stored in the shared game record until they're revealed. They're hidden in the app, but someone with access to the database could see them.
- The public key in `config.js` is meant to be public. The table's current rules let anyone with that key read or change any game. That's fine for a family game with an unguessable six-letter code, but tighter rules can be added later.
- Ladder timing uses each phone's clock. Phones with badly wrong clocks may see the clue step change at slightly different times.
- Use **Leave game on this phone** to exit. Refreshing keeps everyone in the game.
