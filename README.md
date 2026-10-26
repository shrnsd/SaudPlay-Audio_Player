# SaudPlay-Audio_Player
# Audio Forensics Deck

A sleek, offline-first web audio player built entirely in a single file with zero dependencies. 

I built this because I wanted a lightweight local audio player that doesn't rely on bloated frameworks or cloud services, but still has the granular controls you don't typically find in a basic browser player (like pushing volume past 100%, A/B loop locking, and a built-in focus noise layer).

## Features

* **Single-File Architecture:** No React, no NPM, no external assets. Everything (HTML, CSS, Vanilla JS) lives inside `index.html`. It works completely offline.
* **200% Volume Overdrive:** Bypasses the standard HTML5 audio limits using a Web Audio API `GainNode` to amplify quiet tracks.
* **Real-Time EQ:** Bass and treble biquad filters with quick "0 reset" toggles.
* **A/B Looping:** Mark a start and end point to infinitely loop a specific section of a track.
* **Brown Noise Engine:** A built-in, mathematically generated brown noise layer you can toggle on to mask background room noise while working.
* **Data-Driven UI:** Real-time frequency canvas visualizer, playback speed control (0.5x to 2.0x), and sample rate monitoring.
* **Drag-and-Drop Queue:** Drop local files directly from your OS into the browser, and drag the handles (☰) to reorder the playlist.

## How to use

It doesn't get simpler than this:
1. Clone the repo or just download the `index.html` file.
2. Double-click `index.html` to open it in any modern browser (Chrome, Edge, Firefox, Safari).
3. Drag and drop some local `.mp3` or `.wav` files into the queue on the right.

Since the app uses the native browser File API, your audio files are just loaded into local memory. Nothing is ever uploaded to the internet.

## Under the Hood

The audio routing relies entirely on the native Web Audio API. Instead of just playing an `<audio>` tag, the signal is routed through a custom graph: `MediaElementSource -> Bass Filter -> Treble Filter -> Master Gain -> Analyser -> Destination`. 

The brown noise generator isn't an audio file; it's generated algorithmically on the fly using an audio buffer and randomized values to create an infinite, seamless loop.

## Contributing

Feel free to fork this, open issues, or submit PRs if you want to add more tools to the deck. I wanted to keep it to one file, but if you have ideas for useful web audio tweaks, let me know!
