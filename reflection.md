# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

---

Answer: When I first ran the game, the app loaded and looked playable, but the guessing behavior was inconsistent. One bug I noticed was that the hint messages were backwards because when a guess was too high, the game told the player to go higher, and when a guess was too low, it told the player to go lower. Another bug was that the secret number was sometimes converted from an integer to a string during gameplay, which could break the comparison logic and cause wrong results. I also noticed that starting a new game ignored the selected difficulty and always reset the secret number to a range of 1 to 100.

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

---
ANswer: I used chatgpt as an AI teammate to help review the code and identify possible bugs. One correct suggestion it made was that the check_guess() function had reversed hint directions, and I verified that by tracing the if guess > secret branch and seeing that it returned go higher instead of telling the player to go lower. A second correct suggestion was that converting the secret number to a string on even attempts could cause incorrect comparisons, which I verified by reading the submit logic and seeing that the game was mixing string and integer values. One suggestion that was less useful at first was focusing on edge case input testing before fixing the main gameplay bugs, since the bigger issue was the broken comparison logic in the game.

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

Answer: I decided a bug was fixed by testing the specific behavior that was broken before and checking if the result changed after my code edits. I manually tested the game in Streamlit by guessing numbers that were higher and lower than the secret number to see if the hints now gave the correct direction. This helped me confirm that the comparison logic was working correctly. Ai helped me understand what kinds of test cases to write by suggesting simple examples that directly tested the guess comparison behavior.

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

Answer: The secret number kept changing in the original app because streamlit reruns the entire script every time the user interacts with the interface like when we press a button or enter an input. Streamlit reruns are basically like refreshing the program from the top every time the user does something, but session state allows you to store variables that persist between those reruns. I fixed the issue by making sure the secret number was stored in st.session_state.secret and only generated once when the game started or when a new game button was pressed.

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

Answer: One habit I want to reuse in future projects is marking suspicious parts of the code with comments like # FIXME so I can focus on specific areas while debugging. Next time I work with AI on a coding task, I would try to give more precise prompts and verify each suggestion step by step instead of assuming the AI’s solution to the bugs is correct right away. This project helped me realize that AI generated code may look seemingly accurate but can still contain logical bugs that affect how the program behaves.It made me realize that we as developers still need to carefully review and test ai generated code rather than trusting it blindly.