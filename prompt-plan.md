Below is a structured, iterative approach to building Dodge the Poop, followed by detailed breakdowns and finally a series of prompts for a code-generation LLM. The process starts with a high-level blueprint, breaks that down into stages, and then further breaks each stage into safe, test-driven chunks. Each prompt is provided in a code block so you can feed them directly to a code-generation LLM in sequence.


---

1. High-Level Blueprint

1. Project Initialization & Environment Setup

Create a new Phaser.js project with a basic folder structure.

Initialize package manager, bundler, or build tools (npm, Webpack, Vite, or similar).

Install Phaser.js and any testing frameworks (e.g., Jest or Cypress).

Set up a minimal HTML page that references your JavaScript bundle.



2. Display the Game Canvas & “Hello World”

Render a basic Phaser scene with a “Hello World” text to confirm the environment is working.



3. Basic Player Movement

Add a player sprite (placeholder).

Implement left/right movement using keyboard, touch, or tilt.

Test movement across different input methods.



4. Poop Spawning & Falling Mechanic

Spawn poop at random horizontal positions.

Poop falls at a constant (later, increasing) speed.

Test collision boundaries (poop stays in screen bounds until it disappears at the bottom).



5. Collision Detection & Health System

Detect collisions between player and poop.

Decrement health (hearts) upon collision.

End game when health is zero, triggering a “Game Over” state.



6. Scoring & Leaderboard Backend

Track time survived as the main score.

Set up a simple backend or mock for storing and fetching leaderboard scores.



7. Game Over & Leaderboard Display

On game over, show survival time with an unusual number of decimals.

Display a humorous message.

Allow player to enter a nickname and store the result in the global leaderboard.

Display the top scores.



8. Custom Character & Background Upload

Allow the user to upload images for the character sprite and the background.

Scale/crop the character image appropriately.

Use the background image if provided; otherwise use a default.



9. Offline Score Caching & PIN-based Data Recovery

Store scores locally if offline.

On reconnect, push any stored scores to the leaderboard.

Implement a simple PIN-based system to save progress if desired.



10. Polish, Testing & Deployment



Thorough cross-device testing (touch, tilt, keyboard).

Deploy on a cloud platform (AWS, Firebase, or similar).

Configure analytics (Google Analytics or equivalent).



---

2. Break the Blueprint into Major Stages

We’ll tackle the blueprint in eight major stages that build on one another:

1. Stage A: Project Setup & Basic Phaser Integration


2. Stage B: Basic Game Scene & Movement


3. Stage C: Poop Spawning & Basic Collisions


4. Stage D: Health System & Game Over


5. Stage E: Scoring System & Leaderboard Setup


6. Stage F: Leaderboard Display & Submission


7. Stage G: Custom Uploads (Character & Background)


8. Stage H: Final Integrations (Offline Caching, PIN)




---

3. Further Breakdown into Small, Testable Steps

Below is an outline of how each stage can be broken into small, test-driven tasks.

Stage A: Project Setup & Basic Phaser Integration

1. Initialize the Project

Create a new directory, initialize with npm init.

Install Phaser: npm install phaser.

Set up a testing framework (e.g., Jest).



2. Create a Minimal Phaser Game

Write a small index.html that loads main.js.

In main.js, initialize a Phaser Game object with a single scene.

Display a “Hello World” to confirm everything is connected.



3. Basic Build/Serve & Test

Add an npm script to serve/build the project (e.g., using a simple dev server or bundler).

Verify that the game runs in the browser.

Write a trivial test to confirm the scene loads.




Stage B: Basic Game Scene & Movement

1. Player Sprite Setup

Add a placeholder image or shape for the player.

Position it in the middle of the screen.



2. Keyboard Movement

Capture arrow keys or WASD.

Move the player sprite left/right.

Write a test verifying the player’s x-position changes.



3. Touch Input

Implement a simple left/right button overlay or swipe detection for mobile.

Confirm it behaves the same as keyboard input.



4. Tilt Input (Optional)

If feasible, capture device orientation to move the player.

Test on a real device or simulator.




Stage C: Poop Spawning & Basic Collisions

1. Poop Sprite & Random Position

Define a poop image or placeholder.

Spawn it at random x-positions at the top of the screen.

Have it fall straight down at a constant speed.



2. Collision Detection Setup

Add bounding boxes for player and poop.

Add a test that verifies collisions register when bounding boxes overlap.



3. Increasing Spawn Rate

Start with a simple spawn interval.

Decrease interval over time for increasing difficulty.

Test that spawn intervals shrink properly.




Stage D: Health System & Game Over

1. Health Tracking

Store an integer for health (initially 10).

When a collision is detected, decrement by one.



2. Game Over Condition

If health reaches zero, pause or end the game.

Show a “Game Over” screen with a placeholder message.



3. Game Over Testing

Ensure collisions properly trigger health loss.

Verify game transitions to Game Over state when health is 0.




Stage E: Scoring System & Leaderboard Setup

1. Time Survived

Start a timer when the game begins.

Stop the timer at Game Over.

Display this time to the player.



2. Mock Leaderboard Backend

Create a simple Node/Express or a mock service that can GET and POST scores.

Or use a temporary in-memory array for local development.



3. Testing Score Submission

Write tests to confirm that when the game ends, the score is submitted to the mock backend.




Stage F: Leaderboard Display & Submission

1. Game Over Screen

Show time survived with an unusual number of decimals (e.g., 5 or 6).

Display a humorous message.



2. Name Input & Leaderboard Updating

Prompt the player for a nickname.

Submit the nickname + score to the server.

Display top scores in a simple UI.



3. Testing

Verify that the leaderboard updates correctly.

Confirm name input works with filtering (e.g., no offensive words).




Stage G: Custom Uploads (Character & Background)

1. File Upload Input

Provide UI for the user to select a file.

Reject non-image or oversized files.



2. Character Sprite Update

Crop/scale the uploaded image to a standard size.

Replace the placeholder with the user’s custom character.



3. Background Update

Display the uploaded background if provided; otherwise default.

Test on different size images to ensure scaling or letterboxing works.




Stage H: Final Integrations (Offline Caching, PIN)

1. Offline Score Caching

If offline, store scores locally in localStorage or IndexedDB.

Push them to the server when connection is restored.



2. PIN-based Data Recovery

Prompt the user for a PIN.

If provided, store user preferences in the backend.

Allow retrieval of preferences upon next load.



3. Analytics & Deployment

Integrate Google Analytics for pageviews/game events.

Deploy to a hosting service, ensuring environment variables or config are properly set.





---

4. Iterative Prompts for a Code-Generation LLM

Below are the actual prompts (in Markdown code blocks, tagged as text) you can feed to a code-generation LLM. Each prompt is designed for test-driven, incremental implementation. Use them in order, ensuring that each step is tested and integrated before moving to the next.


---

Prompt 1: Project Setup & Basic Phaser Integration

You are a coding assistant helping me build a Phaser.js game called "Dodge the Poop." 
1. Initialize an npm project.
2. Install Phaser (npm install phaser).
3. Create a basic folder structure: src, assets, tests.
4. Set up a Jest test environment (npm install --save-dev jest).
5. Provide a minimal index.html that loads a bundled main.js from src.
6. In src/main.js, initialize a Phaser.Game with a single scene that displays "Hello World" text on screen.
7. Include instructions to run a development server (like using webpack-dev-server or a basic http-server) so I can see the game in my browser.
8. Write a simple Jest test that ensures the scene is defined and can be instantiated.

Return the code for these files and the necessary commands in one cohesive setup.


---

Prompt 2: Basic Player Movement

We now have a Phaser project with a "Hello World" scene. 
1. Replace the "Hello World" text with a placeholder square or sprite representing the player, centered on the screen.
2. Implement left/right keyboard movement (arrow keys and A/D) that moves the player. 
   - Use a velocity or direct x-position update, whichever is simpler.
3. Write tests (Jest or a preferred test runner for Phaser) to confirm the player's x-position changes appropriately when pressing left/right.

Please provide updated code for src/main.js (or separate scenes if you prefer), a test file verifying movement, and any relevant changes to package.json or config.


---

Prompt 3: Touch & Optional Tilt Controls

Now we have keyboard-based movement. Let's support mobile devices:
1. Add simple on-screen buttons for moving left and right on touch devices. 
2. Optionally, show how to detect device tilt (if available) and map it to player movement.
3. Provide tests where possible for the mobile controls (though some might be more integration/e2e style than unit tests).

Return the updated code with a scene that now supports both keyboard and touch input. Include any relevant test code or notes on how you'd test touch interactions.


---

Prompt 4: Poop Spawning & Basic Falling Mechanic

We can now move the player around. Let's start adding falling poop:
1. Add a poop sprite (or placeholder graphic) that spawns at random x positions at the top of the screen.
2. The poop should fall at a fixed speed and disappear when it goes off the bottom of the screen.
3. Write a test (or multiple tests) that confirm:
   - Poop is spawned at random x positions.
   - Poop is removed when it passes the bottom boundary.

Return the updated code for the scene that handles poop spawning, and any new test files or updates to existing tests.


---

Prompt 5: Collision Detection & Health System

Now let's make the game more interesting:
1. Add collision detection between player and poop. If they overlap, it should decrement the player's health by 1.
2. Display the player's health (start with 10 hearts). 
3. Show a simple text or UI element for current health on the screen.
4. Write tests to confirm that collisions are detected and that the health decrements properly.

Return the updated code and tests.


---

Prompt 6: Game Over & Score Tracking

Next steps:
1. Track the time since the player started (our "score"). 
2. When player health hits 0, trigger a "Game Over" state:
   - Pause poop spawning.
   - Show a "Game Over" message with time survived (use an unusual number of decimals for humor).
3. Write a test ensuring that when health = 0, the game transitions to Game Over state and shows the final time.

Return all updated code for game logic, UI, and relevant tests.


---

Prompt 7: Leaderboard Setup & Submission

Let's add a simple mock backend for the leaderboard:
1. Create a small Node/Express server or an in-memory data store that can accept score submissions (POST) and return top scores (GET).
2. Integrate the game client so it sends the final time survived and a player nickname to the mock server upon Game Over.
3. Write a test verifying the client properly sends the score, and the server correctly stores it.

Return:
- The Node/Express server code (or a lightweight alternative).
- The updated Phaser code that posts to the server on Game Over.
- Example test code verifying the score submission flow.


---

Prompt 8: Leaderboard Display & Nickname Entry

Now we show the scores and capture a nickname:
1. During Game Over, prompt the user for a nickname. Apply a simple filter (e.g., remove offensive words, limit length to 200 characters).
2. After submission, display the top scores returned from the server in a leaderboard.
3. Write tests verifying:
   - Nickname input is sanitized.
   - Leaderboard display updates after submission.

Return the updated code for the client and any relevant server changes, plus tests.


---

Prompt 9: User Uploads (Character & Background)

Let's allow custom user uploads:
1. Add a simple file upload input for both character and background images.
2. Validate file type (must be an image) and file size (auto-compress or reject if too large).
3. Replace the player's placeholder sprite with the user-uploaded image, cropped and scaled to a fixed size.
4. Replace the background with the uploaded image if provided; otherwise use a default background.
5. Write tests or instructions on how you'd test uploading and replacing the sprites.

Return the updated code, highlighting where the upload handling happens, and any new tests or notes.


---

Prompt 10: Offline Caching & PIN-based Data Recovery

Finally, let's implement offline caching and a PIN-based recovery:
1. If the device is offline, store the score (and possibly nickname) locally (e.g., localStorage, IndexedDB).
2. Upon reconnect, automatically submit those offline scores.
3. Allow users to create a PIN on the Game Over screen that stores their data (e.g., nickname, best score, images).
4. If they enter the correct PIN on reload, restore their data from the server.
5. Provide tests (or test strategy) verifying that offline scores are cached and submitted, and that PIN-based retrieval works.

Return the final code changes and tests. Summarize how all the pieces integrate, ensuring no orphaned code.


---

5. Conclusion

By following these prompts in sequence, you’ll build Dodge the Poop incrementally with strong testing and minimal leaps in complexity. Each stage integrates seamlessly with the previous one, ensuring no hanging or orphaned code. Once these steps are complete, you’ll have:

A fully functional Phaser.js game with custom user uploads.

A mock or real leaderboard system.

Robust offline caching and optional PIN-based data recovery.


And that’s it! You now have a structured plan and a set of code-generation prompts that you can feed directly into an LLM to guide its implementation, all while adhering to best practices, test-driven development, and incremental progress.

