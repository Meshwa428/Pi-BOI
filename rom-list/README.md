Alright. Pi Zero 2 W is small… but we can still squeeze a lot out of it.



if \*\*10–25 FPS is fine\*\* for you, then I’ll include borderline systems too.



\---



\# TL;DR



\* \*\*Works great (full speed):\*\* 8-bit and most 16-bit consoles, handhelds (GB/GBC/GBA), PS1 (many games), NeoGeo (2D), many older arcade boards using MAME 2003 / FinalBurn Neo.

\* \*\*Playable (with slowdowns / tweaks):\*\* PSP (many light titles), N64 (select titles), Dreamcast (very limited), Saturn (2D), some DS titles.

\* \*\*Bootable but painful (<25 FPS):\*\* modern 3D arcade (Naomi variants), heavy Dreamcast/Some N64 titles, advanced MAME sets.

\* \*\*Not feasible / pointless:\*\* PS2, GameCube, Wii, Wii U, Xbox, modern arcade boards, Switch.



Now the full, categorized list.



\---



\# A. Recommended — Fullspeed / Very playable on Pi Zero 2 W



(These are the ones you can safely archive completely and play comfortably.)



\* Atari 2600, 5200, 7800

\* NES / Famicom / FDS

\* SNES / Super Famicom (most titles)

\* Sega Master System

\* Sega Genesis / Mega Drive

\* Sega Game Gear

\* Sega 32X (2D library)

\* Neo Geo (arcade 2D)

\* Neo Geo Pocket / Neo Geo Pocket Color

\* Game Boy, Game Boy Color, Game Boy Advance (GBA — many titles fullspeed)

\* PC Engine / TurboGrafx-16 (HuCard)

\* ColecoVision, Intellivision, SG-1000, Vectrex

\* Commodore 64, ZX Spectrum, MSX

\* Atari Lynx, WonderSwan

\* Capcom CPS1 / CPS2 arcade (many titles under FinalBurn Neo or MAME2003)

\* CPS-3 (some titles may be borderline)

\* PS1 (many titles run very well under PCSX-ReARMed). (\[retropie.org.uk]\[2])



\---



\# B. Mostly Playable (tweak / lower res / frameskip recommended)



(You’ll get playable results for many games — expect drops on heavy 3D titles.)



\* MAME (classic sets up to \~2003/2010): choose \*\*MAME 2003 / MAME 2003-Plus / MAME 2010\*\* or \*\*FinalBurn Neo\*\* for best Pi performance. (Large modern MAME merged sets are NOT suitable.) (\[retropie.org.uk]\[3])

\* Neo Geo CD (many run fine at lower res)

\* Sega Saturn — \*\*2D titles\*\* work; hardware 3D fighters struggle

\* Nintendo DS — many \*\*2D\*\* and simpler 3D titles playable (Drastic is heavy)

\* N64 — \*\*select games\*\* (GoldenEye, Mario 64 might run okay with tweaks; many others under 30 FPS)

\* Dreamcast — some 2D/less intensive games can boot; expect low FPS on heavy titles

\* PSP (PPSSPP) — \*\*light and many 2D/less complex 3D titles\*\* can be played; heavy PSP 3D titles will be slow but some surprising titles can be acceptable with low res / frameskip. (You already saw Soul Calibur upscaled — nice.) (\[Reddit]\[1])



\---



\# C. Bootable / Experimental (may run but mostly unplayable; include only if you want to archive for completeness)



\* Sega Naomi / Naomi2 / RingEdge / Lindbergh — some boot in emulators but actual performance is poor to unusable.

\* MAME modern sets (0.200+ merged full sets) — will boot some, but vast majority too heavy.

\* 3DO, Jaguar CD — can boot many titles but framerate varies widely.

\* Arcade later 2000s hardware (System246/574 etc.) — mostly impossible.



\---



\# D. Not feasible on Pi Zero 2 W



(You can still keep ROMs in archive but don’t expect to play them on Zero 2.)



\* PlayStation 2 (PCSX2)

\* GameCube (Dolphin)

\* Wii / Wii U / Switch / Xbox / Xbox 360 / PS3 / modern arcade RingEdge/Lindbergh (complex 3D)



\---



\# E. MAME detail \& recommendation (you asked explicitly for early 80s → 2010)



You can include classic MAME arcade games from the early 80s through the 90s and up to \*\*around 2010\*\*, but do this smartly:



\* \*\*Use MAME 2003 / MAME 2003-Plus\*\* (targets classic arcade — well optimized for Pi Zero 2 W). Good for most 80s/90s boards. (\[YouTube]\[4])

\* \*\*Use FinalBurn Neo\*\* for many 90s CPS/Neo-Geo/Atomiswave titles (lightweight and fast).

\* \*\*Avoid full modern MAME merged sets (latest 0.2xx merged)\*\* — they’re huge (100s of GBs / TBs) and contain many heavy systems Zero2 can’t run. (\[Raspberry Pi Forums]\[5])



\*\*Suggested MAME packs for your Zero2-focused archive:\*\*



\* MAME 2003 (core) — includes thousands of 80s/90s classics — \~5–15GB depending on set choice

\* MAME 2010 or MAME 0.78 curated sets for slightly newer titles

\* FinalBurn Neo full ROM + support (good for arcade 90s) — \~a few GBs depending on selection



\---



\# F. Full “Download Everything” candidates under 20GB



(If you want to download the \*entire\* ROMset for that system and keep it manageable)



These are good fits (approx totals—depends on region/duplicates/merged vs split sets):



\* NES / Famicom — \~250MB

\* SNES — \~1.5GB

\* Sega Genesis / Mega Drive — \~2GB

\* Master System — \~120MB

\* Game Boy / GBC — \~1–1.5GB

\* Game Boy Advance — \~6–10GB (trimmed \~5GB)

\* PC Engine (HuCard) — \~500MB–1GB

\* NeoGeo ROM set (non-CD) — \~6–8GB

\* MAME 2003 curated set — \~5–15GB depending on selection

\* Sega CD — \~15–18GB (fits borderline under 20GB)



Big sets to avoid full-dumping if you want small management:



\* PS1 full set: \*\*\~600GB\*\* (huge — avoid).

\* PSP full set: \*\*1–2TB\*\* (do not full-dump).

\* Modern MAME merged: \*\*100s of GB to multiple TB\*\* — curate.



(Those size estimates mirror common community observations and typical compressed ROMset stats.)



\---



\# G. Exhaustive system list (every system Pi Zero 2 W can realistically run/boot in RetroPie / RetroArch / standalone emus)



I’m listing them ALL — everything that can be run (even if occasionally unplayable). Use this as a checklist for your archive:



\*\*Consoles / Handhelds\*\*



\* Atari 2600 / 5200 / 7800 / Jaguar (some)

\* NES / Famicom / Famicom Disk System

\* SNES / Super Famicom

\* Nintendo 64 (select)

\* GameCube (technically you can compile but not playable — listed for completeness)

\* Nintendo DS (partial / 2D fine)

\* Nintendo 3DS (boot in some cores/emulation layers — mostly unusable)

\* Game Boy, Game Boy Color, Game Boy Advance

\* Neo Geo Pocket / Neo Geo Pocket Color

\* Neo Geo AES/MVS (arcade)

\* PC Engine / TurboGrafx-16 (HuCard + CD variants)

\* Sega Master System

\* Sega Genesis / Mega Drive

\* Sega 32X

\* Sega CD

\* Sega Saturn (2D mostly)

\* Sega Dreamcast (some titles)

\* PlayStation 1 (PSX) — very playable.

\* PlayStation 2 (PS2) — \*\*not playable\*\* (archive-only).

\* PlayStation Portable (PSP) — light titles playable via PPSSPP.

\* PlayStation 3 / PS4 / PS5 — not feasible.

\* Xbox (Original) — not feasible for play, but you can store ROMs.

\* Atari Lynx, Atari ST, Lynx, Jaguar (partial), Jaguar CD

\* ColecoVision, Intellivision, Vectrex

\* 3DO (some titles boot)

\* TurboGrafx CD / PC Engine CD — playable (with caveats)



\*\*Arcade (MAME / FBA / FinalBurn Neo related)\*\*



\* MAME 2003 / 2003-Plus / 2010 (classic era) — \*recommended\*

\* MAME modern (0.2xx, merged) — bootable but huge / slow => curate

\* Capcom CPS1 / CPS2 / CPS3 (CPS3 heavy)

\* Neo Geo (including CD/ROM) — works well (2D)

\* Konami System boards (most 2D)

\* Sega System16 / System32 / Naomi (Naomi very limited)

\* Cave shmups (some run, often slow)

\* Atomiswave (some via FinalBurn Neo)

\* Many other arcade boards that are 2D / older



\*\*Computers / Others\*\*



\* Amiga (via UAE) — lighter Amiga titles okay

\* Commodore 64 — works well

\* ZX Spectrum / MSX — works well

\* Amstrad CPC / Apple II — works well

\* DOSBox (DOS) — many lightweight DOS games run ok, heavy ones struggle



(That is an exhaustive actionable list for Pi Zero 2 W usage; RetroPie packages cover most of these.) (\[retropie.org.uk]\[2])



\---



\# H. How I’d structure your homelab archive (compact, manageable)



You have 8TB — awesome. But you want ROMs manageable and pullable. Use a single consistent layout and metadata:



```

/homeserver/roms/

&#x20; ├─ nes/               # zipped roms, region folders optionally

&#x20; ├─ snes/

&#x20; ├─ genesis/

&#x20; ├─ gb/

&#x20; ├─ gbc/

&#x20; ├─ gba/

&#x20; ├─ pc\_engine/

&#x20; ├─ neo-geo/

&#x20; ├─ mame2003/          # curated mame2003 set + CHDs

&#x20; ├─ finalburn-neo/     # FBNeo roms

&#x20; ├─ psx/               # PCSX ReARMed compatible images (ISO/bin/cue)

&#x20; ├─ psp/               # only curated PSP titles you want; avoid full dump

&#x20; ├─ sega-cd/

&#x20; └─ snapshots/         # saves, screenshots, metadata backups

```



\*\*Tips:\*\*



\* Use zip for cartridge ROMs (RetroPie expects zipped .nes/.sfc/.gb/.gba etc.).

\* Keep PS1/PSP as a curated selection (your “must-have” list) — don’t full-dump.

\* For MAME, maintain a \*MAME2003\* directory with the exact XML/zip set you use; store CHDs separately.

\* Use a small database file (CSV/JSON) with columns: `system,rom\_filename,region,crc,notes` so you can query \& pull quickly.



\---



\# I. Suggested download + sync workflow



\* On homelab: store master archive (organized by system).

\* On Pi Zero 2 W: keep only the systems/sets you actually want locally (e.g., psx, nes, snes, genesis, gba, mame2003).

\* Use `rsync`/SFTP or NFS mounts to pull on demand. Example:



&#x20; \* `rsync -avh --progress user@homeserver:/roms/psx/ /home/pi/RetroPie/roms/psx/`

\* For very large sets (MAME/CDs), only sync the subset you plan to play.



\---



\# J. Practical recommendations \& emulator choices (to maximize playability)



\* \*\*PS1:\*\* PCSX-ReARMed (RetroPie default) — use lower resolution, frameskip off first then tune. (\[Reddit]\[6])

\* \*\*PSP:\*\* PPSSPP (standalone) — pick low rendering resolution, turn off post-processing.

\* \*\*MAME:\*\* lr-mame2003 / lr-mame2003-plus for classic arcade; FinalBurn Neo (FBNeo) for many 90s arcade boards. (\[YouTube]\[4])

\* \*\*N64:\*\* mupen64plus with low res \& frame limiting; choose FPS-friendly games.

\* \*\*GBA/SNES/Genesis:\*\* libretro cores (mGBA, snes9x, genesis\_plus\_gx).

\* \*\*DS:\*\* melonDS/libretro DS cores — 2D great, 3D slow.



\[1]: https://www.reddit.com/r/RetroPie/comments/1dm59x9/mame\_for\_raspberry\_pi\_zero\_2\_w/?utm\_source=chatgpt.com "Mame for Raspberry Pi Zero 2 W : r/RetroPie"

\[2]: https://retropie.org.uk/about/systems/?utm\_source=chatgpt.com "Systems in RetroPie"

\[3]: https://retropie.org.uk/forum/topic/32388/mame2003-doesn-t-quite-work-on-pi-zero-2-w?utm\_source=chatgpt.com "Mame2003 doesn't quite work on Pi Zero 2 W"

\[4]: https://www.youtube.com/watch?v=wyonq8TQdYo\&utm\_source=chatgpt.com "Rebuilding MAME romsets - for MAME 2003-Plus on RetroPie ..."

\[5]: https://forums.raspberrypi.com/viewtopic.php?t=246430\&utm\_source=chatgpt.com "Is there any working version of Mame for RPI4 in any form?"

\[6]: https://www.reddit.com/r/RetroPie/comments/17fm3dg/is\_the\_raspberry\_pi\_zero\_w\_2\_capable\_of\_running/?utm\_source=chatgpt.com "Is the Raspberry pi zero w 2 capable of running ps1?"



