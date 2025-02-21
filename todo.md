# ToDo for "Dodge the Poop"

This document is a thorough checklist to guide the development of the "Dodge the Poop" game using Phaser.js. Check off each item as you complete it.

---

## Stage A: Project Setup & Basic Phaser Integration

- [ ] **Initialize the Project**
  - [ ] Create a new directory for the project.
  - [ ] Run `npm init` and fill out basic details (name, version, etc.).
  - [ ] Install Phaser: `npm install phaser`.
  - [ ] Install Jest for testing: `npm install --save-dev jest`.
  - [ ] Decide on a bundler or dev server (e.g., Webpack, Vite, or http-server).

- [ ] **Basic Folder Structure**
  - [ ] Create `src/` for source files.
  - [ ] Create `assets/` for images, sounds, etc.
  - [ ] Create `tests/` for unit/integration tests.

- [ ] **Minimal HTML & Game Initialization**
  - [ ] Create `index.html` that references `src/main.js`.
  - [ ] In `src/main.js`, initialize a Phaser game object (`new Phaser.Game(config)`).
  - [ ] Add a single scene that displays "Hello World" or similar text.

- [ ] **Testing & Scripts**
  - [ ] Add/Update `package.json` scripts for:
    - [ ] `npm run build` (if using a bundler).
    - [ ] `npm run start` to serve locally.
    - [ ] `npm test` to run Jest tests.
  - [ ] Write a trivial Jest test to confirm the scene loads without errors.

- [ ] **Verify in Browser**
  - [ ] Run the dev server, open the game in a browser, and confirm "Hello World" appears.

---

## Stage B: Basic Game Scene & Movement

- [ ] **Player Sprite Setup**
  - [ ] Replace "Hello World" with a placeholder sprite or a simple rectangle.
  - [ ] Center it horizontally on the screen.

- [ ] **Keyboard Movement**
  - [ ] Implement left/right movement with arrow keys or A/D.
  - [ ] Decide on movement logic (velocity-based or direct x-position updates).
  - [ ] Add logic to ensure the player stays within game boundaries.

- [ ] **Testing Movement**
  - [ ] Write or update tests that simulate key presses.
  - [ ] Assert that the player's x-position changes.

---

## Stage C: Touch & (Optional) Tilt Controls

- [ ] **Touch Controls**
  - [ ] Add on-screen buttons (left/right) or swipe detection for mobile users.
  - [ ] Map touch inputs to the same movement function used by keyboard.

- [ ] **Optional Tilt Controls**
  - [ ] If feasible, add device orientation event listeners.
  - [ ] Translate tilt input to left/right movement.

- [ ] **Testing Touch/Tilt**
  - [ ] Use integration tests or manual testing on a mobile device or emulator.
  - [ ] Confirm the player moves correctly when tapping or tilting.

---

## Stage D: Poop Spawning & Basic Falling Mechanic

- [ ] **Poop Sprite**
  - [ ] Create or import a poop image for comedic effect (or use a placeholder).
  - [ ] Spawn it at random x-positions at the top of the screen.

- [ ] **Falling Mechanic**
  - [ ] Set a constant downward velocity or increment y-position each frame.
  - [ ] Remove poop from the scene once it’s off the bottom of the screen.

- [ ] **Increasing Spawn Rate**
  - [ ] Implement a spawn timer that decreases over time to increase difficulty.

- [ ] **Testing Poop Spawning**
  - [ ] Write tests verifying random x-positions are within screen bounds.
  - [ ] Check that poop is removed once below the play area.

---

## Stage E: Collision Detection & Health System

- [ ] **Collision Detection**
  - [ ] Use Phaser’s built-in collision or overlap checks between the player and poop.
  - [ ] When overlap is detected, decrement the player’s health by 1.

- [ ] **Health & Hearts UI**
  - [ ] Start the player at 10 health.
  - [ ] Display the current health somewhere on-screen (text or heart icons).

- [ ] **Testing Health & Collisions**
  - [ ] Write tests that simulate collision events.
  - [ ] Confirm player health decreases as expected.

---

## Stage F: Game Over & Score Tracking

- [ ] **Game Timer (Score)**
  - [ ] Track time survived from start to Game Over.
  - [ ] Use an in-game clock or track elapsed time manually.

- [ ] **Game Over State**
  - [ ] When health reaches 0, transition to a “Game Over” scene or overlay.
  - [ ] Stop spawning poop and pause the main game loop (or disable collisions).
  - [ ] Display the final time survived with multiple decimal places (for humor).

- [ ] **Testing Game Over**
  - [ ] Confirm that health == 0 triggers Game Over.
  - [ ] Assert that final time is displayed.
  - [ ] Ensure that no new poop spawns after Game Over.

---

## Stage G: Leaderboard Setup & Submission

- [ ] **Mock Backend / Local Server**
  - [ ] Create a simple Node/Express app (or similar) to accept POST for scores and GET for the leaderboard.
  - [ ] Store scores in an in-memory array or a mock database.

- [ ] **Client Integration**
  - [ ] On Game Over, prompt the player for a nickname (brief text input).
  - [ ] Submit `{ nickname, score }` to the backend.
  - [ ] Filter out offensive words and limit nickname length to 200 characters.

- [ ] **Testing Leaderboard Submission**
  - [ ] Verify the client sends the correct data.
  - [ ] Check that the server stores and returns it on subsequent GET requests.

---

## Stage H: Leaderboard Display & Nickname Handling

- [ ] **Leaderboard UI**
  - [ ] After submitting the score, fetch the top scores from the server.
  - [ ] Display them in a basic list with rank, nickname, and time survived.

- [ ] **Offensive Word Filter**
  - [ ] Define a simple array or method for checking offensive words.
  - [ ] Replace or block input containing these words.

- [ ] **Testing UI & Nickname**
  - [ ] Confirm that scores appear in the correct order (descending by time).
  - [ ] Check that the nickname is sanitized before submission.

---

## Stage I: Custom Character & Background Upload

- [ ] **Upload Forms**
  - [ ] Provide a button/input to let the user upload a character image.
  - [ ] Provide a button/input to let the user upload a background image.

- [ ] **File Validation**
  - [ ] Validate correct file types (e.g., image/png, image/jpeg).
  - [ ] Auto-compress or reject files above a certain size limit.

- [ ] **Displaying Uploaded Assets**
  - [ ] Crop/scale the character sprite to a uniform size.
  - [ ] Replace the game’s background with the user’s uploaded background if available.

- [ ] **Testing File Upload**
  - [ ] Manually test with various image sizes and formats.
  - [ ] Verify fallback to default images if user cancels upload.
  - [ ] Check that large images are handled gracefully (compression or rejection).

---

## Stage J: Offline Caching & PIN-Based Data Recovery

- [ ] **Offline Score Caching**
  - [ ] Detect offline status (e.g., via browser events).
  - [ ] Store nickname and scores locally in `localStorage` or IndexedDB.
  - [ ] On reconnect, automatically submit the cached scores to the server.

- [ ] **PIN-Based Preferences**
  - [ ] On Game Over, let users set a PIN to store preferences (nickname, best score, custom images).
  - [ ] If user enters the same PIN on a future session, retrieve these preferences from the server.
  - [ ] Handle lost PIN scenarios gracefully (data reset).

- [ ] **Testing Offline & PIN**
  - [ ] Test playing the game while offline, then reconnecting.
  - [ ] Verify that scores and preferences are stored and submitted once online.
  - [ ] Check that PIN-based retrieval only works when the correct PIN is entered.

---

## Stage K: Analytics & Deployment

- [ ] **Analytics (Optional)**
  - [ ] Integrate Google Analytics or a similar service.
  - [ ] Track page loads, game sessions, and possibly game overs.

- [ ] **Deployment**
  - [ ] Build a production bundle (minified, optimized).
  - [ ] Deploy to a hosting service (AWS S3, Firebase, or similar).
  - [ ] Confirm the game loads and runs correctly in production.

- [ ] **Final QA & Polish**
  - [ ] Test across multiple browsers (Chrome, Firefox, Edge, Safari).
  - [ ] Test on mobile devices (Android, iOS).
  - [ ] Ensure performance remains smooth under heavy poop spawn conditions.
  - [ ] Verify all features are present: custom uploads, leaderboard, offline caching, PIN.

---

## Bonus: Post-Launch Considerations

- [ ] **Feedback & Bug Tracking**
  - [ ] Set up a form or a simple system to collect user feedback.
  - [ ] Triage bugs and plan hotfixes or patches.

- [ ] **Content Updates**
  - [ ] Consider new “poop” images or variations.
  - [ ] Add or rotate background images for variety.

- [ ] **Security Audit**
  - [ ] Review code for any vulnerabilities.
  - [ ] Ensure file uploads are always validated server-side if used in production.

---

### Using this Checklist

1. Move through each Stage sequentially, marking items as done.
2. Commit changes frequently with descriptive messages.
3. Continually run and update tests.
4. After finishing each stage, do a quick sanity check (or smoke test) in a real browser environment.
5. Refine and polish as needed.

*Happy coding and good luck dodging the poop!*
