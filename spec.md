Game Specification: "Dodge the Poop"


---

Overview

"Dodge the Poop" is a simple, humorous, and fast-paced 2D web game where players control a character to dodge falling poop. The game supports user-uploaded characters and backgrounds, has an increasing difficulty over time, and tracks scores on a global leaderboard.

Core Gameplay Mechanics

Players move a custom character left and right to avoid poop falling from the top of the screen.

Poop falls at an increasing rate over time.

The game ends when the player's health (represented by hearts) reaches zero.

A "Game Over" screen appears, displaying time survived and a dynamically generated humorous message.

The leaderboard updates with the player’s best survival time.



---

Game Controls

Touchscreen (Mobile): Tap or swipe to move left or right.

Keyboard (Desktop/Laptop): Arrow keys or WASD to move.

Tilt-based (if available on mobile): Tilting the device moves the character.

Pause Button: Device-appropriate (Escape key on desktops, UI button on mobile).



---

Visual & Audio Design

Character: User-uploaded image, cropped and scaled to fit.

Background: User-uploaded image, displayed as-is.

Poop: Fixed-size static cartoon image.

Audio:

"Plop" sound plays when the player is hit.

No background music.




---

Game Logic & Progression

Poop falls straight down at an increasing spawn rate.

Movement is instant and precise with no easing.

Poop disappears upon hitting the ground.

Unlimited number of poops can exist on screen at once.

No animations beyond character movement and falling poop.



---

Health System

Players start with 10 hearts.

Each hit removes one heart.

No way to regain hearts.

No warnings when health is low; game ends immediately when all hearts are lost.



---

Leaderboard & Scoring

Scores are based on time survived.

Displayed in a global leaderboard.

Players enter a nickname (filtered for offensive words, up to 200 characters).

No account system; scores are stored anonymously.

Offline scores are saved locally and submitted when reconnected.



---

Game Flow

1. Character & Background Selection

Players choose or upload a character and background.

Option to skip selection and use randomly chosen previous selections.



2. Gameplay Begins Immediately

No countdown.



3. Game Over Screen

Displays survival time with an unusual number of decimal places.

Shows a dynamically generated humorous/encouraging message.

Proceeds to leaderboard submission.



4. Leaderboard Display

Shows top global scores and the player’s personal best.



5. Restart or Exit

Players can restart with fresh selections or close the game.





---

Data Handling

User Data Storage:

Player choices (character, background) stored in browser session/cookies.

Persistent save option via nickname + 5-digit user-generated PIN.

If PIN is lost, data cannot be recovered.


Leaderboard Storage:

Stored in a cloud-based database.

Submitted upon game over, or when reconnecting if offline.


Caching:

Assets cached for faster loading, with automatic refresh on updates.


Analytics:

Google Analytics (or equivalent) enabled with no opt-out.




---

Error Handling

Invalid File Uploads:

Non-image files rejected.

Oversized images are automatically compressed.


Network Errors:

Scores stored locally and submitted when online.


Game State Corruption:

If data is lost, game resets to a fresh start.


PIN Entry:

No limit on retries.

No feedback on incorrect PIN entries.




---

Testing Plan

1. Gameplay Mechanics

Test movement responsiveness across devices.

Verify poop spawn rate increase over time.

Confirm correct health deduction upon hits.



2. User Uploads

Ensure image uploads work with different formats.

Verify proper scaling/cropping of character images.

Test background images displaying correctly.



3. Leaderboard Functionality

Validate nickname filtering.

Confirm score submission under normal and offline conditions.



4. Performance & Compatibility

Test on various browsers (Chrome, Firefox, Edge, Safari, Mobile).

Ensure smooth performance on both high- and low-end devices.



5. Security & Data Integrity

Test PIN-based data recovery.

Check that cookies/session storage behaves as expected.

Verify proper error handling for network failures.





---

Development Stack

Game Engine: Phaser.js

Backend (Leaderboard Storage): Cloud-based NoSQL database

Frontend: HTML5, JavaScript, CSS

Hosting: Web-based deployment (AWS, Firebase, or similar)



---

Final Notes

This specification provides all necessary details for implementation. The game’s simplicity ensures an engaging experience while maintaining ease of development. The focus on quick playability, humor, and lighthearted fun makes it ideal for a wide audience. The next step is development and iterative testing!

