# Family Field Guide

A phone game for a family group (about 3 to 12 players). Each person plays on their own phone, with no shouting. One person hosts; everyone else joins with a six-letter code. Plan for about 45 to 70 minutes with six players.

## How to play

1. **Host:** open the site, type the player names (one per line), and tap **Create game**. Share the code or the link in the address bar.
2. **Everyone:** open the site, tap **Join**, enter the code, and tap your own name. The host can also tap their name.
3. **Host:** tap **Start the questionnaire**. Each player gets a number (1, 2, 3…) at random.
4. **Everyone:** first tap your age group (under 10, 10 to 15, 16 to 24, 25 to 39, 40 to 59, or 60 or over). Your age group decides which version of each question you see. Then answer the twelve questions about yourself on your own phone. Until you save your answers, you can tap **Change my age group** to pick again. Tap every answer that fits you, or tap **None of the above**, which clears the other picks. Tapping a regular answer clears **None of the above**. The host starts the game once at least three people have finished. Anyone who hasn't finished sits out.

Each player starts with one **Double** (doubles the points from one vote) and one **Lifeline** (removes two wrong answers from one guess). Each can be used once per game.

### The four chapters

- **Chapter 1, Who Is This?** A three-step clue ladder about one player. Clue 1 appears at once, clue 2 after 15 seconds, and clue 3 after 30 seconds. Guessing during clue 1 is worth 3 points, clue 2 is worth 2, and clue 3 is worth 1. A guess is right if that person fits every clue shown so far, so more than one person can be right. A wrong guess costs 1 point. The ladder stays open until everyone has voted or the host moves on.
- **Chapter 2, How Well Do You Know Me?** A question about one player. Their answer may include more than one choice, and a guess is right if it matches any of them. Before you answer, bet 1, 2, or 3 points. A right answer gains the bet, and a wrong one loses it, so scores can go negative. The Lifeline removes two wrong choices, and never a right one.
- **Chapter 3, Would You Rather.** Everyone picks one of two options. You score 1 point if you match the majority. A tie scores nothing.
- **Chapter 4, Showdown.** The top three players by score become the finalists. Only they vote on three clue ladders, and every point is doubled. Everyone else watches.

The person being described can still guess about themselves, but a guess about yourself scores 0 points.

When everyone who can vote has voted, the round's result appears. Nothing moves on by timer. The host taps **Next question** to continue. If people are taking too long, the host can tap **Move on now** to score the votes in and continue. The result of each round also appears above the next one. The host taps **Start Chapter** between chapters.

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

## Guess the Object

A second game on its own page, `object.html`, with Claude as the one who knows the object.

**Setup (one time).** The game runs as a Supabase Edge Function named `object-game`, with two private tables (`object_games` and `object_questions`). Add your Anthropic API key in Supabase under **Edge Functions → Secrets**, with the name `ANTHROPIC_API_KEY`.

**How to play**
1. Enter at least two player names and tap **Create game**. Share the code.
2. Each player opens the page, joins with the code, and taps their name. Anyone can tap **Start the game** once at least two people have joined.
3. Each round, every player asks one yes-or-no question on their own phone. Claude answers Yes or No. Only the player who asked sees the answer.
4. Once everyone has asked, each player can submit one guess or pass. Guesses are visible to everyone.
5. The first correct guess wins, and the object is revealed. If nobody gets it, the game log says so and the next round starts.

The object is picked at random from a list in the function, and it is never sent to the page. The function has no login, so anyone with the code can take actions, the same as the other games.
