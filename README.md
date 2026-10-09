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

- [x] Describe the game's purpose.
- [x] Detail which bugs you found.
- [x] Explain what fixes you applied.

**Purpose:** A Streamlit number-guessing game. The player picks a difficulty, then guesses a secret number within that range, getting "higher" or "lower" hints after each guess. Each difficulty allows a set number of attempts, and the score depends on how quickly the player wins.

**Bugs found:**

1. **The hints were backwards.** A guess that was too high said "Go HIGHER!", and a guess that was too low said "Go LOWER!"
2. **The secret changed type on every other guess.** On even-numbered attempts, `app.py` turned the secret into a string (`str(st.session_state.secret)`) before checking the guess. Comparing an int to a string raised a `TypeError`, and the fallback code then compared both as text. Text is compared character by character, so `"9" > "10"` is true. As a result, a guess of 9 against a secret of 10 was called "Too High", and the outcome of a guess could depend on which attempt it was.
3. **The tests didn't match the code.** `check_guess` returns an `(outcome, message)` pair, but the tests compared the whole result to a single string such as `"Win"`, so they could never pass.

**Fixes applied:**

1. Swapped the hint messages, so "Too High" now says "Go LOWER!" and "Too Low" now says "Go HIGHER!"
2. Removed the even-attempt string conversion in `app.py`, so the real integer secret is always passed in. `check_guess` now converts both values with `int()` and compares them as numbers, and the `try/except` text fallback is gone.
3. Moved `get_range_for_difficulty`, `parse_guess`, `check_guess` and `update_score` from `app.py` into `logic_utils.py`, and changed `app.py` to import them.
4. Updated the existing tests to unpack `outcome, _ = check_guess(...)`, and added regression tests for the hint direction and for a string secret (`check_guess(9, "10")` must be "Too Low").

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. The user enters a guess of 50
2. Game returns "Too Low"
3. User enters a guess of 70 → "Too High"
4. Score updates correctly after each guess
5. The game ends after tthe user correctly guesses the number

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

tests/test_game_logic.py::test_winning_guess PASSED                                                                                       [ 14%]
tests/test_game_logic.py::test_guess_too_high PASSED                                                                                      [ 28%]
tests/test_game_logic.py::test_guess_too_low PASSED                                                                                       [ 42%]
tests/test_game_logic.py::test_too_high_hint_says_go_lower PASSED                                                                         [ 57%]
tests/test_game_logic.py::test_too_low_hint_says_go_higher PASSED                                                                         [ 71%]
tests/test_game_logic.py::test_string_secret_compares_numerically PASSED                                                                  [ 85%]
tests/test_game_logic.py::test_string_secret_win PASSED                                                                                   [100%]

============================================================== 7 passed in 0.07s ===============================================================

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
