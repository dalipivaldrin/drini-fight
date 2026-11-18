# Drini Fight 🥊

A 1-vs-1 online fighting game that runs in the browser – on phone or computer. One player creates a room with a code, the other joins with the same code, and you fight each other live.

**▶ Play now:** https://dalipivaldrin.github.io/drini-fight/

## How to Play Online
1. Player 1 enters a name and **picks a room code** (e.g. `BMW850`) → taps **Raum erstellen**
2. Player 2 enters the **same code** → taps **Beitreten**
3. Fight! Best of 3 rounds – first to win 2 rounds wins the match. Then hit **Revanche** for a rematch.

There's also a **training mode against the CPU**.

Watch the sky: hearts and weapons drop in by parachute – grab them first!

## Controls
| Action | Keyboard | Phone |
|---|---|---|
| Move | A / D (or ← →) | ◀ ▶ |
| Jump | W / ↑ / Space | ▲ |
| Block | S / ↓ | BLOCK |
| Punch | J | SCHLAG |
| Kick | K | TRITT |
| Special (energy bar full) | L | SPEZIAL |

On phones, hold the device in landscape.

## How I Built It
- **Single file:** `index.html` – HTML5 Canvas + plain JavaScript, no images or audio files
- **Online multiplayer:** peer-to-peer connection via WebRTC using [PeerJS](https://peerjs.com). The room code becomes the host's peer ID, so the second player can connect directly
- **Host-authoritative netcode:** the host runs the game simulation at 60 FPS; the guest only sends its button inputs and receives the game state ~30 times per second (smoothed on screen). This keeps both screens in sync and fair
- **Fighting mechanics:** punch, kick, block (reduces damage by 85%), jump, knockback, hit stun, energy meter that fills when you land or take hits, and a projectile special attack
- **Rounds:** 60-second timer, K.O. or most health wins the round, best of 3
- **Sky drops:** every few seconds a parachute drops a random item – a **heart** (+25 HP) or a **weapon** (sword, axe, hammer, spear). A weapon replaces your punch with a stronger, longer-range attack, but it only lasts **15 seconds** and only one player can hold it
- **No accidental zoom:** pinch and double-tap zoom are blocked so the view never shifts during a fight
- **CPU opponent:** simple AI that approaches, attacks in range, blocks and uses specials
- **Effects:** hit sparks, screen shake, generated sound effects (Web Audio API)
- **Mobile:** multi-touch on-screen buttons, scales to any screen

> Note: in rare cases, strict networks (some mobile carriers or company Wi-Fi) can block peer-to-peer connections. If it doesn't connect, try switching to Wi-Fi.

---

Developed by **Valdrin Dalipi** – with AI assistance (Claude).
