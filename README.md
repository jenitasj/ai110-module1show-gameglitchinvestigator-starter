# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
   This game is a guessing number game that prompts the user with hints to guess a secret number chosen by the system within a limited number of attempts. The game provides hints after each guess to tell the player whether their guess is too high or too low. The goal is to find the correct number before running out of attempts.

- [ ] Detail which bugs you found.
   While testing the game, I discovered a lot of logic bugs. First, the hint messages were reversed becuase when a guess was too high, the game told the player to go higher, and when the guess was too low, it told the player to go lower. THen the secret number sometimes changed type from an integer to a string during gameplay, which caused inconsistent comparisons in the guessing logic. I also noticed that starting a new game ignored the selected difficulty and always reset the range to 1–100.

- [ ] Explain what fixes you applied.
  I fixed the hint logic in the check_guess() function so that guesses greater than the secret correctly tell the player to go lower and guesses less than the secret tell the player to go higher. I also removed the code that converted the secret number into a string so that comparisons always happen between integers. Finally, I updated the new game reset logic so that it uses the correct number range based on the selected difficulty.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]
![alt text](<Screenshot 2026-03-15 at 10.44.18 PM-1.png>)
![alt text](<Screenshot 2026-03-15 at 10.43.13 PM.png>)


## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
