# pi-boi — Instagram Video Series

> A complete build series. From blank idea to finished handheld. 50+ videos.

---

## Series Structure

The series is divided into **7 chapters**, each covering a phase of the build. Each video has a hook, a core demo or reveal, and a reason to come back for the next one. Episodes within a chapter can be posted across days or weeks depending on build pace.

Videos marked 🔥 are high-engagement "wow" moments — prioritize quality and editing on these.

---

## CHAPTER 1 — The Idea
*Introduce the project, set the tone, and grab the audience with the first demo.*

---

**Video 1 — "I'm building a Game Boy. With a Raspberry Pi."** 🔥
The series opener. Introduce pi-boi: what it is, why you're building it, what it'll do. Show the pile of parts on the table. End with the FM transmission demo — play music on the Pi Zero, tune a radio or phone nearby to the frequency, and show the audio coming out crystal clear. The punchline: "This tiny $15 board is transmitting FM radio. And this is just the beginning."

**Video 2 — "Here's everything going inside this thing"**
Flat-lay parts showcase. Pick up each component, briefly explain what it does and why you chose it. Keep it visual — show the tiny speakers, the DAC board, the little FM receiver chip. End with: "Next video — I blow up one of these. Hopefully not on purpose."

**Video 3 — "The display that almost made me cancel the whole project"**
Close-up focus on the ILI9341 2.8-inch SPI display. Show it lighting up for the first time connected bare to the Pi. Show the default slow refresh, then show the config tweak that pushes it to ~50 FPS. Side-by-side before/after is the payoff here.

**Video 4 — "Wait, this screen has a touchscreen?"**
The moment you discovered the resistive touch controller. Show the stylus, show it registering taps on screen. Light, fun, reactive energy — this is a genuine surprise moment and audiences love those.

**Video 5 — "What should I call it? (already named it)"**
Short, personality-driven video. Talk through the name pi-boi. The Game Boy reference, the pi pun. Show a rough sketch or mockup of what the final device might look like. Ask the audience what they think. Good engagement driver early in the series.

---

## CHAPTER 2 — First Connections
*Each component gets wired up and tested solo. Every video ends with something working (or not).*

---

**Video 6 — "Wiring the brain — Pi Zero 2 W first boot"**
First boot of the Pi Zero 2 W, headless setup over SSH. Show the process, show the terminal, show it responding. Nothing fancy — but satisfying for anyone who's done this before, and educational for those who haven't.

**Video 7 — "Getting the screen to talk to the Pi"**
SPI wiring for the ILI9341. Walk through the connections, the driver install, the first moment it renders something on the tiny screen. Show a test image or colour fill.

**Video 8 — "Wiring the touch controller"**
Connect the resistive touch controller (typically XPT2046 on these panels) to the Pi. Calibrate it. Show a simple drawing test — drawing with the stylus directly on screen. Very visual and satisfying.

**Video 9 — "The DAC that makes it sound like this…"**
Wire up the UDA1334A I2S DAC. Play a 30-second clip of a lossless FLAC or ALAC track through it into headphones. No commentary needed for the payoff — just let the audio quality speak. Compare briefly to the Pi's onboard PWM audio (which sounds rough) to make the difference obvious.

**Video 10 — "Tiny speakers, surprisingly loud"** 🔥
Wire the PAM8403 amplifier and the two 16mm speakers. Play something with bass. Show the reaction. These small speakers at 1W each can get surprisingly loud — this is a good "wait what" moment.

**Video 11 — "FM radio on a $2 chip"**
Wire up the RDA5807M over I2C. Tune to a local station. Show the audio coming out of the dedicated jack. Then show the RDS data printing to the terminal — station name, song title. That detail always gets people.

**Video 12 — "The buttons are alive"**
Wire up the 5-way tactile switch and a few action buttons to GPIO pins. Write a simple Python script that prints the button name to terminal every time one is pressed. Show it live. This is the first time the device has proper input — it's a milestone moment.

**Video 13 — "Does it all work at once?"**
First time everything is wired together on a breadboard or with jumper wires — messy, chaotic, beautiful. Show each system responding simultaneously. It'll be a mess of wires. That's the point — it makes the final clean build feel more earned.

---

## CHAPTER 3 — The OS & Software Foundation
*This chapter is about making the hardware feel like a real device through software. Less soldering, more terminal.*

---

**Video 14 — "RetroPie vs Batocera — which one for pi-boi?"**
Side-by-side comparison of both platforms running on the Pi Zero 2 W with the SPI display. Boot times, RAM usage, emulator compatibility, SPI display support. Conclude with which one you're going with and why.

**Video 15 — "Setting up RetroPie / Batocera on the SPI display"**
The actual config process — fbcp-ili9341 or similar framebuffer copy tool, getting the display output routing correctly, DMA settings. Show the final result: EmulationStation rendering on the tiny 2.8-inch screen.

**Video 16 — "Mapping the buttons to the Pi — making it a real controller"**
GPIO button mapping in RetroPie/Batocera. Walk through the EmulationStation controller setup screen using only pi-boi's physical buttons. First time the device is navigated entirely with its own controls.

**Video 17 — "First game on pi-boi"** 🔥
Load a ROM. Play the first game on the device using the physical controls, looking at the tiny screen. Keep it simple — something iconic like Super Mario Bros or Sonic. This is the first "it's a real Game Boy" moment. Short video, big payoff.

**Video 18 — "How fast can the Pi Zero 2 W actually go?"**
Performance testing across emulator targets. Show which systems run full speed (NES, SNES, GBA), which need tweaks (PS1), and which are too heavy. Sets realistic expectations and is genuinely useful info for the audience.

**Video 19 — "Building the audio player — Part 1: choosing the stack"**
Explain the choice between MPD, GStreamer, VLC, and ffmpeg for the audio backend. Show a quick benchmark or demo of each playing an ALAC file through the I2S DAC. Decide on one.

**Video 20 — "Building the audio player — Part 2: the UI"**
Code and show the first version of the audio player UI rendered on the 240×320 display. Even a basic prototype with track name, progress bar, and play/pause is a satisfying milestone. Show it being navigated with buttons.

**Video 21 — "ALAC on a Raspberry Pi Zero — does it work?"**
Dedicated ALAC playback test. Play Apple Lossless files through the I2S DAC. Show the CPU usage while playing to confirm the Pi Zero 2 W can handle it. Audio quality comparison against MP3 if possible.

**Video 22 — "Building the on-screen keyboard"**
Show the OSK implementation — either Matchbox Keyboard configured and working, or early prototype of a custom one. Demonstrate navigating it using only the 5-way switch + A/B buttons. Then show the same keyboard used with the stylus on the touchscreen.

**Video 23 — "Linux desktop on a 2.8-inch screen"** 🔥
Boot into desktop mode (LXDE or Openbox). Show a full Linux desktop rendered on the tiny display. Open a terminal. Open a browser. It's absurd and delightful. This video will do numbers.

**Video 24 — "Switching between modes — the launcher concept"**
First look at the pi-boi native launcher concept. Show a wireframe or early prototype. Explain the three-mode architecture: Gaming, Audio, Desktop. Talk through the design goals — fast, button-navigable, touch-friendly.

**Video 25 — "Coding the launcher — Part 1: framework choice"**
Walk through the decision between Pygame, LVGL, SDL2, and Dear ImGui. Show a simple animated test on the display for each. Benchmark frame rates. Pick one and commit.

**Video 26 — "Coding the launcher — Part 2: first working build"**
First functional version of the pi-boi launcher running on the device. Even a rough version with the right visual direction is exciting. Show navigation with buttons and with touch.

---

## CHAPTER 4 — The Build
*Hands, solder, and a PCB or perfboard. This is the most visually satisfying chapter.*

---

**Video 27 — "Planning the layout — how do you fit all this in your hands?"**
Sketch or CAD preview of the internal layout. Show how the components will be arranged — display at the top, buttons on either side, battery in the back, boards stacked or side by side. This is the planning video before the physical build begins.

**Video 28 — "Perfboard or custom PCB?"**
Talk through the decision: hand-solder on perfboard vs. design a proper PCB. Show the trade-offs. If going custom PCB, show the first KiCad or EasyEDA design. If perfboard, show the layout plan.

**Video 29 — "Soldering the display headers"**
First soldering session. Keep the camera close. Show the flux, the solder, the heat. Clean, satisfying soldering content performs extremely well in maker communities.

**Video 30 — "The worst part of any build — wire management"**
Honest, relatable video about routing wires inside a tight enclosure. Show the problem, show the solution (cable routing, heatshrink, labelling). The more honest and self-deprecating, the more it resonates.

**Video 31 — "Soldering the audio chain together"**
Wire DAC → amplifier → speakers as a permanent assembly. Final audio test post-solder to confirm nothing was damaged. Show the speaker mounted in an improvised enclosure to hear the bass response.

**Video 32 — "Button panel — building the controls"**
Build and wire the full button array: 5-way switch, A, B, X, Y, Select, Start. Test each button in software. Show the finished button panel from both sides — wired and clean face.

**Video 33 — "Power — choosing a battery and charging circuit"**
Talk through the battery choice (LiPo size, capacity, C-rating), the charging IC (TP4056 or similar), and the 5V boost converter for the Pi. Show the first battery-powered boot — the moment it's truly untethered from USB.

**Video 34 — "It runs on battery!" 🔥**
First full battery-powered session. Pi boots, display lights up, audio plays, buttons work — all running on internal battery with no USB cable. One of the biggest milestone moments of the entire series.

**Video 35 — "Designing the enclosure — Part 1: sketches"**
Show the initial physical design sketches or CAD mockups of the handheld shell. Talk through ergonomics, button placement, port locations, speaker grilles. Ask the audience for input on design choices.

**Video 36 — "Designing the enclosure — Part 2: 3D printing the first prototype"**
Time-lapse of the first 3D print. Show the print coming off the bed. Test-fit all components. Identify what needs to change. It won't be perfect — that's the point.

**Video 37 — "Does it fit?" 🔥**
Show the full hardware assembly slotted into the first enclosure print. Even rough, this is the first time it actually looks like a handheld device. Very shareable moment.

**Video 38 — "Enclosure revision — fixing what didn't fit"**
Show the pain points from the first print and the CAD changes made to fix them. Second print, second test-fit. The iterative process is relatable and honest.

---

## CHAPTER 5 — Feature Deep Dives
*Each major feature of pi-boi gets its own spotlight video.*

---

**Video 39 — "FM radio on pi-boi — full demo"** 🔥
Complete FM radio demo on the assembled device. Plug earphones into the FM jack, tune to a local station, show the RDS info on screen. Walk the audience through the dedicated jack design decision.

**Video 40 — "FM transmission — broadcast your music to any radio"** 🔥
Full FM transmitter demo. Play music from pi-boi, tune a car stereo or FM radio to the same frequency, and show the audio synced up. Drive the range of the signal. This video alone could go viral in the maker community.

**Video 41 — "Bluetooth headphones on a Pi Zero — does it work?"**
Connect a pair of Bluetooth headphones to pi-boi. Walk through the pairing process using the on-screen UI. Show low-latency audio playback. Acknowledge the Pi Zero's Bluetooth limitations honestly — no A2DP aptX, but it works.

**Video 42 — "Wi-Fi — what can pi-boi actually do online?"**
Show practical Wi-Fi use cases: downloading a ROM over Wi-Fi, streaming internet radio, SSH-ing into the device from a phone. Light, fun demo format.

**Video 43 — "The audio player — full demo"**
Complete walkthrough of the finished audio player. Show ALAC playback, album art display, button navigation, touch navigation with the stylus. Play a full 30-second clip to let the audio quality land.

**Video 44 — "The on-screen keyboard — typing on a 2.8-inch screen"**
Full OSK demo — type something using only the buttons, then type the same thing using the stylus. Show it working inside the desktop browser (search something). Slightly absurd, very satisfying.

**Video 45 — "Gaming on pi-boi — a proper session"** 🔥
Sit down and actually play games for a dedicated video. Show multiple systems — SNES game, GBA game, a PS1 game. Show it being held naturally like a handheld. This is the "proof of concept" video for the gaming feature.

---

## CHAPTER 6 — Polish & Problems
*Honest look at the final stretch — bugs, fixes, and refinements.*

---

**Video 46 — "Things I would do differently"**
Mid-to-late-series honest reflection. What hardware choices caused problems, what would be changed in a v2. Audiences respect builders who are honest about mistakes. Also great for engagement — people love giving their opinions.

**Video 47 — "The bug that took 3 days to fix"**
Pick one genuinely tricky software or hardware bug from the build — button debouncing issues, audio popping, SPI display tearing, something real. Walk through the diagnosis and the fix. These "I finally figured it out" videos are deeply satisfying to watch.

**Video 48 — "Battery life test — how long does pi-boi last?"**
Run the device until the battery dies under different use cases: gaming only, audio playback only, mixed. Record the times. Show the low battery warning UI. Gives the audience a real, useful spec.

**Video 49 — "Final assembly — putting it all together"** 🔥
Time-lapse of the final assembly into the finished enclosure. Everything going in, the back closing, screws going in. Slow motion close-up of the display lighting up for the first time fully assembled. One of the most satisfying videos in the series.

**Video 50 — "pi-boi is done." 🔥**
The finale. Full device showcase — show every feature in sequence: gaming, audio player, FM radio, FM transmitter, Bluetooth, desktop mode, on-screen keyboard. Hold it up. It's a real thing. "Part 2 coming eventually." Emotional payoff for everyone who followed the series.

---

## BONUS VIDEOS (51–60+)
*Post-launch content to keep the series alive after the build is done.*

---

**Video 51 — "Can I actually use pi-boi as a daily driver?"**
Week-long real-world use diary. Use it for music, gaming, and as a computer. Report back on what works and what doesn't in practice.

**Video 52 — "pi-boi v2 — what I'm changing"**
If v2 is planned: custom PCB, better battery, larger screen option, hardware power button. Seed the next build arc.

**Video 53 — "You asked, I answered — pi-boi Q&A"**
Compile the most common questions from the comments across the series. Answer them in one video. Great for late-series engagement.

**Video 54 — "Can it run DOOM?"**
It can. Show it.

**Video 55 — "Making pi-boi talk to my phone"**
Explore tethering, Bluetooth audio relay from phone to pi-boi speakers, using pi-boi as a Bluetooth speaker. Silly but fun.

**Video 56 — "What if I gave pi-boi to someone who's never seen it before?"**
Hand the finished device to a friend or family member with no explanation. Film their first interaction. Reaction content that also doubles as a real usability test.

**Video 57 — "The full wiring diagram — how it all connects"**
Dedicated technical video: full schematic walkthrough, GPIO pin mapping, power rail diagram. The resource video that will get saved and shared by builders.

**Video 58 — "Can I make pi-boi louder?"**
Experiment with a higher-power amp module, speaker enclosure tuning, and EQ settings. Pure tinkering content.

**Video 59 — "Open sourcing pi-boi"**
Release the code, the CAD files, and the wiring diagrams. Talk through what's included. This video is the one that turns the series into a community project.

**Video 60 — "Someone built their own pi-boi"**
Community showcase — if anyone replicates the build, feature their version. Massive community engagement moment.

---

## Series Posting Strategy

| Phase | Suggested Cadence | Notes |
|---|---|---|
| Chapter 1 (Videos 1–5) | Every 2–3 days | Hook early followers fast |
| Chapter 2 (Videos 6–13) | 2× per week | Consistent, show parts coming alive |
| Chapter 3 (Videos 14–26) | 2× per week | Longer chapter — software takes time |
| Chapter 4 (Videos 27–38) | 2× per week | Most visual chapter, lean into it |
| Chapter 5 (Videos 39–45) | 2× per week | Feature drops — treat each like a mini-launch |
| Chapter 6 (Videos 46–50) | 3× per week | Build momentum to the finale |
| Bonus (51–60) | 1× per week | Sustain the audience post-build |

---

## Hook Formulas That Work for This Series

- **"I built a [thing] using only [unexpected constraint]"** — works for FM transmission, desktop mode, OSK
- **"This tiny chip costs $2 and does [impressive thing]"** — works for RDA5807M, PAM8403
- **"Wait, this [component] also has a [surprise feature]?"** — works for the touch screen discovery
- **"Day X of building my own Game Boy"** — ongoing format, builds parasocial investment
- **"Nobody told me [problem] would be this hard"** — honest content, drives comments

---

*50 videos. One handheld. Let's build it.*
