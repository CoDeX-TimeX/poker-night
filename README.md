# ♦️ Poker Night OS

**Poker Night OS** is a modern, web-based digital chip tracking system designed for home Texas Hold'em games. It replaces physical poker chips with a networked "Virtual Casino" experience, allowing you to play with real cards while handling all financial transactions, betting logic, and pot calculations digitally.

Built with **HTML5, CSS3 (Luxury UI), and Firebase Realtime Database**.

---

## 🌟 Features

### 📺 The Host Table (iPad/TV Display)

Designed to sit in the center of the table, acting as the "Dealer" and "Pot."

* **Realistic Pot Visuals:** Uses an algorithm to visually render 3D chips in a messy pile based on the actual pot value.
* **Real-Time Admin:**
* **🏆 Win Button:** Instantly awards the pot to a specific player.
* **ワ New Hand:** Clears the pot and bets, unfolds all players, but **keeps** player chip stacks intact.
* **楳 Split Mode:** Select multiple players to automatically calculate and distribute a split pot (ties).
* **竊ｻ Reset Game:** Factory reset that restores everyone to the starting $1000 stack.


* **Player Grid:** Shows live status of every player (Active, Folded, Current Bet).

### 📱 The Player Interface (Phone Controller)

A landscape-first mobile interface that acts as the player's wallet and betting controls.

* **Smart "Call" Button:** Automatically calculates the difference between your current bet and the table's highest bet to let you match instantly.
* **Staging Area:** Click chips ($1, $5, $25, $100) to prepare a bet locally, then slide "BET" to push it to the server (prevents accidental clicks).
* **All-In Protection:** Prevents players from betting more chips than they actually hold.
* **Fold System:** Darkens the screen when a player folds to prevent accidental betting. Includes an "Undo" button.
* **Live Wallet:** Updates your balance instantly when you win a pot.

---

## 🛠 Tech Stack

* **Frontend:** Vanilla JavaScript (ES6 Modules), HTML5, CSS3 (Flexbox/Grid).
* **Backend:** Google Firebase Realtime Database (Serverless).
* **Styling:** "Dark Mode" luxury aesthetic with Gold/Green accents and neumorphic shadows.

---

## 📂 Project Structure

```text
/PokerApp
│
├── index.html      # The Landing Hub (Choose Host or Player role)
├── host.html       # The Admin/Table View (Run this on an iPad/Laptop)
└── player.html     # The Controller View (Run this on Phones)

```

---

## 🚀 Setup Guide

### 1. Configure Firebase

1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Create a new project.
3. Add a **Web App** (`</>`) to get your `firebaseConfig`.
4. Enable **Realtime Database** and set rules to **Test Mode** (read/write: true).
5. **Important:** Open `host.html` and `player.html` and replace the `const firebaseConfig = { ... }` block with your own keys.

### 2. Host the Files

Since this uses ES6 Modules, you cannot just double-click the HTML files. You must serve them.

* **Option A (GitHub Pages - Recommended):** Upload these 3 files to a GitHub Repository and enable "Pages" in settings.
* **Option B (Tiiny.host):** Drag and drop the files to a static host.
* **Option C (Local):** Run a local server (e.g., Live Server in VS Code).

---

## 🎮 How to Play

1. **Start the Host:** Open `index.html` on an iPad or Laptop and select **"OPEN HOST"**.
* Create a Room Name (e.g., `TABLE1`) and a numeric Password (e.g., `1234`).
* Click **START**.


2. **Join as Players:** Have friends open `index.html` on their phones and select **"OPEN PLAYER"**.
* Enter the same Room Name and Password.
* Enter their own Name.


3. **Betting:**
* Players tap chips to stage a bet.
* Click **BET** to push chips to the center.
* Use **CALL** to match the current high bet.


4. **Winning:**
* At the end of the hand, the Host taps the **🏆 WIN** button on the winning player's card.
* The chips fly from the pot to that player's wallet.


5. **Next Round:**
* Host clicks **NEW HAND** to reset the board for the next deal.



---

## 📸 Screen Logic

* **Logic Handling:** The Host file performs the heavy lifting for pot distribution to ensure data consistency.
* **Synchronization:** All screens update within milliseconds via WebSockets (Firebase).

---

*Built for the ultimate Poker Night experience.*
