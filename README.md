# pi-boi — DIY Handheld Retro Gaming & Audio Player

> *A pocket-sized, Raspberry Pi-powered handheld built for retro gaming, high-fidelity audio, FM radio, and wireless connectivity — all in one device.*

---

## Overview

**pi-boi** is a fully custom, handheld consumer electronics device built around the Raspberry Pi Zero 2 W. Inspired by the iconic form factor of the original Game Boy, pi-boi combines a retro gaming console, a lossless audio player, an FM radio receiver, and an FM transmitter into a single pocketable unit. Every hardware and software decision has been made with simplicity, performance, and real-world usability in mind — no off-the-shelf gaming shell, no compromises.

The name is a dual nod: *pi* for the Raspberry Pi at its heart, and *boi* as a playful reference to the Game Boy that inspired its form.

---

## Core Hardware

### Compute
**Raspberry Pi Zero 2 W**
The brain of the device. The Pi Zero 2 W offers a quad-core 64-bit ARM Cortex-A53 processor at 1GHz, 512MB RAM, integrated Wi-Fi, and Bluetooth — all in a stamp-sized board. It is powerful enough to run a wide range of retro emulators (NES, SNES, GBA, PS1 at reduced settings, and more) while remaining power-efficient enough for handheld battery use.

### Display
**2.8-inch SPI Display with ILI9341 Driver + Resistive Touch**
A 240×320 pixel TFT display driven over SPI. With proper driver configuration and DMA-based transfers, this display can be pushed to approximately 50 frames per second — more than adequate for the emulation targets the Pi Zero 2 W can handle. The small physical size is ideal for handheld use, keeping the overall device compact.

The display also features a **resistive touch controller**, discovered during hardware review. This adds a secondary input method across the entire UI — touch interaction is supported via the bundled stylus pen or fingertip. Resistive touch works particularly well with a stylus for precise taps on a small screen.

### Audio — High Quality Playback
**UDA1334A I2S DAC Stereo Decoder Module**
For music playback and game audio at the highest quality, pi-boi uses an I2S DAC rather than relying on the Pi's onboard PWM audio. The UDA1334A delivers clean 24-bit stereo output with a built-in 3.5mm headphone jack, allowing users to plug in any wired earphones or headphones for a premium listening experience.

### Audio — Speaker Amplification
**PAM8403 Digital Audio Amplifier Module**
For on-device speaker output, a PAM8403 class-D stereo amplifier drives two speakers at up to 3W per channel. Class-D amplification is highly efficient, minimising battery drain. The amp is fed from the same I2S DAC signal chain, ensuring consistent audio quality across both headphone and speaker outputs.

### Speakers
**2× 16mm Round Speakers (8Ω, 1W)**
Two compact 16mm diameter full-range speakers are mounted in the device enclosure for stereo sound without headphones. At 1W each, they provide adequate volume for gaming and casual listening within the constraints of the small enclosure.

### FM Radio Reception
**RDA5807M FM Receiver Module**
pi-boi includes a dedicated FM receiver module controlled over I2C. The RDA5807M supports the full FM band and includes RDS (Radio Data System) support for station name and song title display. Because FM reception requires an antenna, a dedicated 3.5mm audio jack is provided exclusively for the FM radio — the wired earphone cable acts as the antenna. This keeps the FM audio path completely separate from the main DAC audio chain, avoiding the need for any audio routing logic or custom switching circuitry. Users simply plug earphones into the FM jack to listen to radio.

### FM Transmission
**Single GPIO (Software FM Transmitter)**
Using a single GPIO pin and the `fm_transmitter` software, pi-boi can broadcast audio as a low-power FM signal on user-selected frequencies. Transmission is restricted to legally available frequencies and operates within a very short range, intended for use within a controlled personal environment (e.g. broadcasting to a nearby car stereo or speaker). In testing, the clarity of the GPIO-based transmission has been found to exceed that of local FM radio stations. This feature is deliberately restrictive and is not intended for wide-area broadcasting.

### Controls
**5-Way Tactile Switch (Directional Input)**
A 5-way tactile joystick switch provides up, down, left, right, and centre press — used as the primary directional input for games and UI navigation.

**Tactile Buttons (Action & System Controls)**
A set of tactile push buttons provides the standard handheld gaming control layout: A, B, X, Y, Select, and Start. Additional buttons may be added for volume, brightness, or mode switching.

---

## Software Architecture

pi-boi runs a layered software stack designed around three distinct operational modes, all accessible from a unified launcher.

### Mode 1 — Retro Gaming (RetroPie / Batocera)
The primary gaming experience is built on either **RetroPie** or **Batocera Linux** — both well-established retro gaming platforms with broad emulator support and active communities. The chosen platform provides EmulationStation as the game library frontend, with RetroArch handling emulation for individual systems.

Supported systems include (but are not limited to):
- NES, SNES, Sega Genesis / Mega Drive
- Game Boy, Game Boy Color, Game Boy Advance
- PlayStation 1 (at compatible performance settings)
- Neo Geo, Atari, and other classic platforms

Both RetroPie and Batocera have existing SPI display and GPIO input support, reducing the integration effort for pi-boi's custom hardware.

### Mode 2 — pi-boi Native Launcher (Custom UI)
A lightweight custom launcher is developed specifically for the Pi Zero 2 W's hardware constraints. Rather than running a heavy desktop environment in the background, this launcher runs directly on the framebuffer or a minimal graphics layer, keeping CPU and RAM usage minimal so that the experience remains fast and responsive.

**Design goals for the native launcher:**
- Visually polished with smooth animations — but performance-first; no compositing overhead
- Fully navigable using only the physical buttons (5-way switch + A/B/Start/Select)
- Also fully navigable using the resistive touchscreen with stylus or fingertip
- Houses shortcuts to: gaming frontend, audio player, FM radio, FM transmitter, settings, and desktop mode
- Displays useful at-a-glance information: battery level, Wi-Fi status, Bluetooth status, current time

**Candidate frameworks for the launcher UI:**
- **Pygame** — Python-based, proven on Pi Zero hardware, renders custom graphics at framebuffer level with minimal setup
- **LVGL** (Light and Versatile Graphics Library) — C-based, extremely lightweight, purpose-built for embedded UIs with built-in touch support
- **SDL2** — Low-level but flexible, direct framebuffer rendering, solid touch and input event handling
- **Dear ImGui** — Immediate-mode GUI, minimal overhead, good for a highly custom-feeling interface

The final framework will be selected based on benchmarking on actual Pi Zero 2 W hardware. Performance on the 240×320 display at target frame rates is the deciding factor.

### Mode 3 — Linux Desktop Mode
pi-boi supports switching into a full Linux desktop environment, giving the user access to a general-purpose computer on the device. This mode is useful for development, file management, web browsing, or any task beyond gaming and audio.

**Desktop environment candidates (lightweight, suitable for Pi Zero 2 W):**
- **LXDE / LXQt** — The lightest full desktop environments; standard on Raspberry Pi OS Lite
- **Openbox** — Minimal window manager only; very fast, very low RAM footprint
- **XFCE** — Slightly heavier but very user-friendly with broad software support

The desktop is fully operable via the resistive touchscreen with the stylus, and navigable via the physical button set with the on-screen keyboard. Switching between the native launcher and desktop mode is done via a designated button combination or a menu option in the launcher, with a smooth transition.

### On-Screen Keyboard (OSK)
Because pi-boi has no physical keyboard, an on-screen keyboard is available system-wide across all three modes.

**Input methods for the OSK:**
- **Physical buttons** — Navigate the key layout using the 5-way directional switch; confirm a key with A; backspace with B. Optimised for thumb use while holding the device.
- **Resistive touchscreen** — Tap keys directly with the stylus pen or fingertip. The stylus is recommended for accuracy on the compact 2.8-inch display.

**OSK candidates:**
- **Matchbox Keyboard** — Lightweight, designed specifically for embedded Linux and small screens, good touch support
- **Onboard** — Feature-rich OSK with good touch support and support for custom layouts
- **Custom OSK** — A bespoke on-screen keyboard built into the native launcher, styled to match the pi-boi UI, with button navigation designed from the ground up

The OSK is accessible at any time via a button shortcut and appears automatically when a text input field is focused in desktop mode.

### Audio Player
The audio player is a dedicated application accessible from the native launcher, routing output through the UDA1334A I2S DAC.

**Supported formats (target):**
- **ALAC** (Apple Lossless Audio Codec) — primary lossless target format
- **FLAC** — open lossless standard
- **WAV** — uncompressed PCM
- **MP3, AAC, OGG Vorbis** — lossy formats for broad compatibility

**Candidate playback backends:**
- **MPD** (Music Player Daemon) + custom lightweight frontend — battle-tested on Pi hardware, native ALAC and FLAC support, runs as a background service that any UI can communicate with
- **GStreamer** — flexible pipeline-based audio framework, supports ALAC via plugins, integrable into a fully custom player UI
- **VLC / libvlc** — supports virtually every audio format, can be driven programmatically from a custom interface
- **ffmpeg / ffplay** — universal format support, usable as a decoding backend behind a custom player

The player UI is designed for the 240×320 display and is navigable via both buttons and touch. It displays track title, artist, album, album art (when available), playback progress, and transport controls.

---

## Audio Architecture

pi-boi uses a deliberately clean, separated audio architecture with no shared routing between the radio and main audio paths:

| Output | Signal Path | Use Case |
|---|---|---|
| Wired headphones / earphones | UDA1334A I2S DAC → 3.5mm Jack | Games, music, Bluetooth relay |
| Onboard speakers | UDA1334A I2S DAC → PAM8403 Amp → 2× Speakers | Games, music (no headphones) |
| FM radio earphones | RDA5807M → Dedicated 3.5mm Jack | FM reception (earphone cable = antenna) |

The FM radio audio never passes through the Pi's audio system. It is received and output entirely by the RDA5807M module. This eliminates the need for audio multiplexers, software routing, or any custom switching circuitry.

---

## Input Architecture

| Input Method | Available In | Primary Use |
|---|---|---|
| 5-way tactile switch | All modes | Directional navigation |
| A / B / X / Y buttons | All modes | Confirm, back, action, context menu |
| Start / Select | All modes | Pause, menu access, mode switching |
| Resistive touchscreen | All modes | Touch navigation, direct UI interaction |
| Stylus pen | All modes | Precise touch input on small display |
| On-screen keyboard (buttons) | All modes | Text entry via button navigation |
| On-screen keyboard (touch) | All modes | Text entry via stylus or fingertip tap |

---

## Current Status

> **Stage: Parts acquired — awaiting assembly.**

All hardware components have been sourced. The project is at the pre-assembly stage, with hardware wiring, OS configuration, driver setup, and all software development still ahead.

---

## Planned Development Phases

1. **Hardware assembly & wiring** — Connect all modules to the Pi Zero 2 W; verify each component independently before full integration.
2. **OS & driver configuration** — Set up Raspberry Pi OS Lite or Batocera base; configure ILI9341 SPI display with DMA; configure resistive touch controller; configure I2S audio via UDA1334A; set up RDA5807M I2C driver.
3. **Gaming frontend** — Install and configure RetroPie or Batocera; map all physical controls; optimise display framerate; benchmark emulator performance per system.
4. **Native launcher** — Build the custom pi-boi launcher UI; implement full button navigation and touch/stylus navigation; integrate shortcuts to all modes and apps.
5. **On-screen keyboard** — Implement or integrate OSK with full button navigation and touch input; hook into system-wide text input for both launcher and desktop mode.
6. **Audio player** — Build lightweight audio player UI backed by MPD or GStreamer; verify ALAC and FLAC playback quality through the I2S DAC.
7. **FM receiver software** — Build FM tuner UI for RDA5807M; display RDS station and track info on screen; implement channel scanning and preset saving.
8. **FM transmitter software** — Integrate `fm_transmitter` into the launcher; add frequency selection and transmission control UI.
9. **Desktop mode integration** — Configure lightweight desktop environment; ensure touch, OSK, and button navigation all function correctly; implement smooth mode switching to and from the native launcher.
10. **Enclosure design** — Design and fabricate a handheld enclosure (3D printed or hand-built) with all ports, buttons, speakers, and the display properly mounted.
11. **Battery & power management** — Integrate a LiPo battery with charging and protection circuitry; implement software battery level monitoring and low-power warnings.
12. **Polish & QA** — Final UI refinement, button debouncing, power optimisation, display brightness control, volume control, and end-to-end user experience testing.

---

*pi-boi — small device, big personality.*
