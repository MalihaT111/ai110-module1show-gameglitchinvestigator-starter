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
### ✅ Game's Purpose
This is a number guessing game built with Streamlit where players try to guess a randomly generated secret number within a specific range. The game offers three difficulty levels:
- **Easy**: Range 1-20, 8 attempts
- **Normal**: Range 1-100, 6 attempts  
- **Hard**: Range 1-1000, 4 attempts

Players receive directional hints (higher/lower) after each guess and earn points based on their performance. The goal is to guess the correct number before running out of attempts while maximizing your score.

### ✅ Bugs Found
1. **Inverted Hint Logic**: When guessing a number, the hints gave opposite directions (told to go lower when should go higher, and vice versa)
2. **Inconsistent Secret Number**: The secret number appeared to change between guesses due to Streamlit's rerun behavior not properly using session state
3. **Persistent Game History**: Guess history carried over between games instead of resetting
4. **Incomplete Reset**: The "New Game" button did not properly reset all game state variables
5. **Type Conversion Bug**: Code alternated the secret between string and integer types on even/odd attempts, causing comparison issues

### ✅ Fixes Applied
1. **Fixed hint direction** in the `check_guess()` function in logic_utils.py to correctly compare guess vs secret and return proper messages
2. **Implemented proper session state management** by storing the secret number in `st.session_state.secret` and only generating it once at initialization or on new game
3. **Reset history on new game** by clearing `st.session_state.history = []` in the `start_new_game()` function
4. **Complete state reset** by ensuring all session state variables (attempts, score, status, history) are properly reset when starting a new game
5. **Removed type alternation bug** and ensured consistent integer comparison throughout the guess checking logic
6. **Refactored game logic** into logic_utils.py for better code organization and testability

---

## 📸 Demo
<img width="1440" height="900" alt="Screenshot 2026-03-04 at 11 22 49 PM" src="https://github.com/user-attachments/assets/16856b3a-299d-406e-a032-cc2807672e90" />



