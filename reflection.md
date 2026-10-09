# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
|Guess of 45 |Too low  |Too high |none |
|You got the number right |score is 15 |score is -15 |none|
|none | Guess a number between 1 and 100. Attempts left: 8

|Guess a number between 1 and 100. Attempts left: 7

 | none|

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). The AI tool I used is Claude, and the sugession it gave me was the changing of the hints that the game gave the player
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest) 
I decided a bug was fixed after doing the same thing I did before hand to see if the problem still occured. 
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?
The AI helped me understand what was wrong and how it wrong and save me time running some of the test myself. 

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Streamlit makes a local website that you can edit and run effiecently. You can make changes in real time.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git. 
  Using AI hand in hand while making projects and usding it to explain problems and concepts to me.
- What is one thing you would do differently next time you work with AI on a coding task?
Ask it to explain how to do something in concept instead of having it do it for me to get a more hands on approch.

- In one or two sentences, describe how this project changed the way you think about AI generated code.
Ai generated code can be to much at times when it is not neeeded, but can really percise with what you want it to do.