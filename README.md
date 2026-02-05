# 🖱️ Mouse Tracker & Moving Button Demo

👉🏼 [URL Tracker](https://maestroant.github.io/mouse-tracker-testpage)

An interactive web page for **recording user behavior**, visualizing pointer trajectories, and testing reactions to dynamic UI elements.

The project combines:
- mouse / touch movement and click tracking
- visualization on `<canvas>`
- an interactive button that randomly changes its position
- an architecture ready for **behavioral analysis / anti-bot scenarios**

---

## ✨ Features

- 📍 **Pointer trajectory recording**
  - `pointermove`, `pointerdown`, `pointerup`
  - coordinates, timestamps, event source

- 🎨 **Visualization**
  - movement points — black
  - clicks — green
  - real-time rendering on canvas

- 🔘 **Interactive button**
  - moves to a random position when clicked
  - never goes outside the viewport
  - does not conflict with tracking logic

- 🧠 **Clean event architecture**
  - `document` — global tracking
  - `button` — passive event logging
  - behavior control is separated from logging

---

## 🏗️ Architecture

### Responsibility separation

| Component | Purpose |
|---------|---------|
| `document` listeners | Global behavior collection |
| `button` listeners | Button event logging |
| `moveButtonRandom()` | UI behavior control |
| `logEvent()` | Centralized event recording |
| `canvas` | Visualization layer |

### Design rationale

- `preventDefault()` is used **only where appropriate**
- the button remains fully interactive
- events are neither lost nor duplicated
- the codebase is easy to extend for analytics

---

## 📂 Event data structure

Each event is stored in the `events` array:

```json
{
  "type": "down",
  "x": 512,
  "y": 384,
  "t": 1738600000000,
  "target": "button"
}
