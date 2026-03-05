# 💭 Reflection: Game Glitch Investigator

## 1. What was broken when you started?

When I first ran the program, I entered 50 while the secret number was 79, but with hints enabled it incorrectly told me to go lower instead of higher. When I submitted a larger number afterward, the hint again gave the opposite direction. The Submit button also does not automatically add guesses to the history. Additionally, the guess history persists between games, and clicking New Game does not properly reset the game state. 

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
I used ChatGPT to organize my responses to the reflection.md. For Coding, I used Claude. The AI suggested that the session state is not updated properly and I verified it by going to those lines of code. It tried to find other bugs I wasn't trying to fix and that was something I did not want. 

---

## 3. Debugging and testing your fixes
I didn't realize this was a question but I initially inspected the code, and then moved onto testing the UI. If the UI matched what should happen then I considered it fixed. I made copilot write tests for me and those passed as well. I now know how to write tests. 


## 4. What did you learn about Streamlit and state?

In the original app, the secret number appeared to change because Streamlit reruns the entire script every time the user interacts with the page. This meant parts of the game logic were re-executed, which caused inconsistent behavior during guesses. Streamlit reruns work by restarting the script from the top, while st.session_state stores values that should persist between those reruns. The fix was storing the secret number in st.session_state and only generating it once (or when starting a new game), which keeps the number stable throughout the game.

## 5. Looking ahead: your developer habits
I want to make use of test cases more often. Instead of relying on UI changes, I want to rely on pytests. I feel like I have the tendency to copy paste code without looking, so I will do that more from now on. I think AI generated code often introduces new bugs and I need to be careful to not make problems worse. 

