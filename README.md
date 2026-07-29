markdown_content = """# 🎙️🧩 Code Clash

**Code Clash** is a fast-paced, 1v1 multiplayer puzzle game built in Unity, inspired by classic code-breaking games like *Mastermind*. Players go head-to-head to crack their opponent's 4-digit secret code using text or voice commands before time runs out!

## 🎮 Game Concept

1. **Set the Code:** At the start of the match, each player selects a secret 4-digit number (e.g., `5281`). Players cannot see each other's codes.
2. **Take Turns:** The game is turn-based. When it's a player's turn, they have **30 seconds** to guess the opponent's secret code.
3. **Make a Guess:** Guesses can be entered via the keyboard or spoken into the **microphone** using speech recognition (e.g., *"Five Two Eight One"*).
4. **Instant Feedback:** The system compares the guess against the opponent's code. If a digit is correct *and* in the exact right position, it is revealed. 
   - *Example:* Secret is `5281`. Guess is `5284`.
   - *Result:* `5 2 * *` (The exact matches are shown in green, while incorrect digits remain hidden as asterisks/underscores).
5. **Winning:** The first player to successfully guess the full 4-digit code (`5 2 8 1`) wins the game, while the opponent loses.

## ✨ Key Features

- **1v1 Online Multiplayer:** Secure, server-authoritative turn-based gameplay where secret codes are never exposed to the client.
- **Voice Recognition (Speech-to-Text):** Hands-free guessing by just speaking the numbers into the microphone.
- **Turn-based Timer:** A strict 30-second countdown per turn to keep the pressure high.
- **Interactive UI:** Clean and intuitive Main Menu, Matchmaking Lobby, Code Selection screen, and Gameplay dashboard.

## 🛠️ Tech Stack & Requirements

- **Engine:** Unity (2D or 3D)
- **Language:** C#
- **Networking:** Unity Netcode for GameObjects / Mirror / Photon (PUN/Fusion)
- **Voice Integration:** Native Unity `UnityEngine.Windows.Speech` or third-party Speech-to-Text APIs (e.g., Google Cloud Speech, Whisper).

## 🚀 Development Roadmap

Following an iterative development process, the project is structured into logical phases:

- [x] **Phase 1: Core Mechanics (Offline)**
  - Setup the Unity project and basic UI flow (Menu -> Code Selection -> Gameplay).
  - Implement the core code comparison logic (string matching).
- [ ] **Phase 2: Game Loop & Timers**
  - Integrate the 30-second countdown timer.
  - Implement local turn-switching logic.
- [ ] **Phase 3: Online Multiplayer**
  - Integrate a networking solution (e.g., Photon or Netcode).
  - Implement server-side verification: clients send guesses to the server, and the server returns the parsed result.
  - Synchronize the timer and turn states across the network.
- [ ] **Phase 4: Voice Recognition**
  - Add microphone recording capabilities.
  - Process voice input to convert spoken numbers into a 4-digit string.

## 💻 Core Logic Snippet

A sneak peek at the simplified logic used to verify a player's guess against a secret code:

```csharp
string secret = "5281";
string guess = "5384";
string result = "";

for(int i = 0; i < 4; i++)
{
    if(secret[i] == guess[i])
        result += secret[i]; // Correct digit & position (Green)
    else
        result += "*";       // Incorrect (Hidden)
}

// Output: "5*8*"
