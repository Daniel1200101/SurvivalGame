SurviveGame - Project Walkthrough
==================================

1) Decompilation Steps
-----------------------
- Decompiled the APK using the website "Android APK Decompiler".
- Extracted and copied two Java classes into Android Studio:
  • Activity_Game.java
  • Activity_Menu.java
- Also copied their corresponding XML layout files.

2) Resolving Compilation Issues
-------------------------------
General:
- In build.gradle:
  • Changed compileSdkVersion from 34 to 35.

- In AndroidManifest.xml:
  • Applied minor adjustments to match the new SDK configuration.

Activity_Game.java:
- Imported the missing R class manually.
- In the `finishGame()` method:
  • Updated Toast duration from raw value `1` to `Toast.LENGTH_LONG`.

Activity_Menu.java:
- No major changes required beyond integrating string and theme resources.

Resources (res/values):
- In `strings.xml`:
  • Added `app_name`.
  • Added `url` for state data.

- In `styles.xml`:
  • Defined new theme: `Theme.SurviveGame`.

3) Code Structure and Logic
----------------------------

Activity_Menu:
- UI includes a text box for entering an ID and a button to start the game.
- On button click:
  • Extracts the character at index 7 of the entered ID.
  • Uses that character to select a corresponding state (country setup).

Activity_Game:
- Receives the ID from Activity_Menu.
- Generates a "steps" array that represents the required arrow input sequence.

  Step Generation Logic:
  -----------------------
  • If ID length < 9:
     Use default steps: [1, 1, 1, 2, 2, 2, 3, 3, 3]
  
  • If ID length == 9:
    → Convert each character in the ID to an integer.
    → Apply `% 4` to each integer.
    → Resulting values populate the custom steps array.

  Arrow Mapping:
  --------------
    0 - Left
    1 - Right
    2 - Up
    3 - Down

 

