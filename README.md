# Twitch Crosshair Overlay

![Preview Crosshair 2x2px white dot](screenshot.jpg)

A lightweight JavaScript snippet that injects a customizable center-screen crosshair dot directly into the Twitch video player. Perfect for FPS streams when the streamer has their in-game crosshair disabled or hidden.

## Features

* **Click-Through:** Uses `pointer-events: none` so you can still click the video to pause or unpause.
* **Responsive:** Anchored directly to the player overlay, keeping the dot centered in default, theater, and fullscreen modes.
* **Zero Dependencies:** Pure vanilla JavaScript—no extensions required.

## Usage

1. Open the Twitch stream you want to watch.
2. Open your browser's Developer Tools (`F12` or `Ctrl + Shift + I` / `Cmd + Option + I` on Mac).
3. Switch to the **Console** tab.
4. Copy and paste the following code into the console and press **Enter**:

```javascript
const playerOverlay = document.querySelector('[data-a-target="player-overlay-click-handler"]');

if (playerOverlay) {
  const crosshair = document.createElement("div");
  crosshair.style.width = "2px";
  crosshair.style.height = "2px";
  crosshair.style.backgroundColor = "white";
  crosshair.style.position = "absolute";
  crosshair.style.top = "50%";
  crosshair.style.left = "50%";
  crosshair.style.borderRadius = "50%";
  crosshair.style.transform = "translate(-50%, -50%)";
  crosshair.style.pointerEvents = "none";
  crosshair.style.zIndex = "9999";
  
  playerOverlay.appendChild(crosshair);
}
```

## Customization

You can easily tweak the look of the crosshair by changing these values in the script before running it:

* **Size:** Adjust `width` and `height` (e.g., `"4px"` or `"6px"` for better visibility).
* **Color:** Change `backgroundColor` to any CSS color (e.g., `"red"`, `"lime"`, `"#00ffcc"`).
* **Visibility:** Add `crosshair.style.boxShadow = "0 0 2px black";` to give the white dot a dark outline on bright backgrounds.

## Notes

* Refreshing the page (`F5`) will remove the crosshair. Simply paste the snippet again to restore it.
* Some browsers (like Chrome or Firefox) might require you to type `allow pasting` into the console before pasting code for the first time.
