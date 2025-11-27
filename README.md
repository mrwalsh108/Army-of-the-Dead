💀 Army of the Dead (The Accelerating Automaton)

A self-contained HTML/JavaScript application demonstrating complex musical sequencing and real-time visual synchronisation using the Web Audio API, accompanied by charmingly crude 8-bit zombie pixel art.

Overview

This project simulates a musical automaton driven by an accelerating clock. The composition begins at a sedate 78 Notes Per Minute (NPM) and ramps up aggressively to 131 NPM, driving both the musical score and the visual animation of the undead horde.

All audio is generated entirely through browser-based synthesis (no external samples or MIDI files). The application is contained within a single index.html file, upholding the principle of maximum portability.

Core Features

100% Synthetic Audio: All sounds—from the bass drum and hi-hats to the melody, organ, and continuous drone—are generated using the Web Audio API (OscillatorNode, GainNode, FilterNode).

Dynamic Tempo Ramp: The rhythm engine features a precise, linear acceleration phase (Notes 32–95) that shifts the entire composition from a crawl to a frantic pace.

Real-Time Visual Synchronisation: The 8-bit zombie sprites "bob" in time with the music. The CSS animation speed is dynamically updated by the JavaScript scheduler via a custom CSS variable (--beat-duration), ensuring perfect sync as the tempo accelerates.

Complex Sequencing: The composition progresses through six distinct phases, featuring:

Melody and Organ modulation (Minor Third Up, Semitone Down).

Pulse Wave Chord ramp down (exponential decay).

Continuous Sawtooth Drone with frequency modulation.

Scheduled, high-frequency Harmonic Bursts with aggressive echo and decay effects.

Audio Effects Rack: Implements a custom reverb impulse response, a high-feedback echo line, and a dynamically modulated phaser filter for the chord sequence.

Technical Implementation Notes

Audio Engine

The sequencer operates on a setTimeout loop that continuously checks the AudioContext.currentTime against nextNoteTime. This "lookahead" method ensures precise timing independent of the browser's main thread rendering, even during rapid tempo changes.

Animation Synchronization

CSS Variable: A custom CSS property, --beat-duration, is defined on the visual container.

JS Update: In the scheduler() function, the necessary beat duration (e.g., 60 / current_NPM) is calculated and set on the container's style.

CSS Animation: The zombie elements utilise a simple zombie-bob keyframe animation with steps(2) to create a jerky, pixelated movement. The duration of this animation is directly bound to var(--beat-duration), ensuring the bobbing perfectly matches the speed of the currently scheduled note.

Getting Started

As this is a single, self-contained HTML file, no build steps are required. Simply download or clone the repository and open index.html in any modern web browser.
