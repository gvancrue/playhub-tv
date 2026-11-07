# PlayHub — your PC games on your LG TV, Apple TV style

> **Heads up:** this is a personal project, vibe coded for my own living room (an LG TV on webOS 4.5 + a Windows gaming PC). It works great for me. If it works for you too, enjoy! It's free, no support promised. The name **PlayHub** is temporary and will change soon.

**The idea:** turn on your TV, open PlayHub, make sure your PC is on with **Sunshine** running, and start playing. No opening Moonlight, no typing IPs, no hunting for the game in a list.

![version](https://img.shields.io/badge/version-1.7.2-8b9bff) ![webOS](https://img.shields.io/badge/webOS-4.5%20(rooted)-555)

---

## What it does

**On the TV**
- An Apple TV–style home screen with your PC games: big backgrounds, logos, descriptions, release year and original console (SNES, N64, PS2…).
- **Pick a game → it starts on your PC and streams**, using Moonlight under the hood (PlayHub reuses Moonlight's pairing).
- **Quit a game from the couch:** hold **SELECT + START** for 2 seconds. The game closes on the PC and you're back in PlayHub.
- **Steam button** at the top: opens Steam in **Big Picture mode**.
- **PC off?** PlayHub tells you, and can wake it up with Wake-on-LAN.
- **Controller-first:** navigate everything with a gamepad. **RT / LT** jump to the next / previous game. The TV remote works too (only arrows, OK and Back, so your color buttons stay yours).
- **Built-in Bluetooth panel** to pair and connect controllers. One controller is rock solid, two is fine. With three or more, the TV's Bluetooth may get flaky (Moonlight itself supports up to 4).
- Each game has its own page with **Play**, **Remove from Continue playing** and **Hide**.

**On the PC ("My library", a small page that opens in your browser)**
- Finds your **Steam, Epic and GOG** games automatically and keeps Sunshine in sync. No more adding apps by hand.
- **Add anything else:** any `.exe`, shortcut (`.lnk` / `.url`) or `.bat`, like emulators, recomps, ports, Xbox/Game Pass, EA, Ubisoft, Battle.net…
- **Choose which games show up on the TV** and drag them into the order you want.
- **Customize each game:** name, year, description (automatic from Steam or Wikipedia), cover, background and logo (from Steam, from **SteamGridDB** with a free key, or your own images), and console icon.
- **Hides the mouse pointer** while you play (automatic for controller games).
- **Fullscreen helper** for games that open in a window (borderless fullscreen, or it presses Alt+Enter / F11 for you).
- Runs hidden and starts with Windows. You only need to open the page when you want to change something.

## What you need

- An **LG TV with rooted webOS** and **[Homebrew Channel](https://github.com/webosbrew/webos-homebrew-channel)**. Built and tested on **webOS 4.5**; other versions may work, no promises.
- **[Moonlight TV](https://github.com/mariotaku/moonlight-tv)** from Homebrew Channel, **paired once** with your PC.
- A **Windows PC** with **[Sunshine](https://github.com/LizardByte/Sunshine)**, with a username and password set in its web page (`https://localhost:47990`).
- Optional: a free **[SteamGridDB](https://www.steamgriddb.com)** API key for lots more art.

## Install

### 1. On the TV
1. Open **Homebrew Channel** → **Settings** → **Add repository**.
2. Enter: `https://gvancrue.github.io/playhub-tv/apps.json`
3. Go back to the app list, find **PlayHub** and install it. Updates arrive the same way.

The first time you open it, PlayHub asks Homebrew Channel for root access for its background service (you'll just see the logo for a moment). Root is needed to read Moonlight's pairing, read controllers and use Bluetooth.

### 2. On the PC
1. Download **[PlayHub-PC.zip](https://gvancrue.github.io/playhub-tv/PlayHub-PC.zip)** and unzip it anywhere (it's 5 small files: a `.bat`, a PowerShell script and the web page).
2. Make sure Sunshine is running, then double-click **`Install.bat`**. Windows asks for administrator permission once, only so the TV can read your library over your home network. (Since it's a downloaded script, Windows SmartScreen may warn you: *More info → Run anyway*. It's all plain text, read it first if you like.)
3. **"My library"** opens in your browser with a 3-step setup: your Sunshine login, an optional SteamGridDB key, and which games you want on the TV.

That's it. From now on: **TV on → PlayHub → play.**

To uninstall from the PC: `PlayHub.ps1 -Uninstall` (your games stay in Sunshine; `PlayHub.ps1 -RemoveGames` removes the ones PlayHub added).

## Recommendations

- **Use a cable** for the PC if you can, and 5 GHz Wi-Fi (or a cable) for the TV. It makes the biggest difference in streaming quality.
- In **Sunshine** → Configuration → Input, set **Emulated Gamepad Type** to **X360 (Xbox 360)**.
- **Steam's on-screen keyboard pops up in non-Steam games?** That's Steam's *Desktop Layout*. In Steam → Settings → Controller, turn off **Guide button focuses Steam** and **Guide Button Chords**, and in **Desktop Layout → Edit** remove the "Show keyboard" binding (or pick the *Gamepad* template).
- **Want to wake the PC from the TV?** Enable Wake-on-LAN in your BIOS and network adapter, and keep the PC on a cable.
- **Something's off?** On the TV go to **Controllers → Diagnostics**. It shows the whole picture, including the service log. A photo of that screen says almost everything.

## Bluetooth for Old webOS (beta) · v0.3.2

A separate, standalone app (it doesn't need PlayHub) for everything Bluetooth on old webOS TVs. Made on webOS 4.5. Install it from the same Homebrew Channel repository.

- **Your devices at a glance:** controllers, speakers & headphones, keyboards & mice, with their status. Pair new ones with step-by-step pairing tips for Xbox, PlayStation, 8BitDo, Switch Pro and audio devices.
- **Notifications over anything you're watching:** "8BitDo Ultimate 2 Wireless connected", "Bose QC45 disconnected"… also for controllers on USB or their own 2.4 GHz receiver.
- **Favorite speaker ★:** reconnects by itself when the TV turns on, and (optionally) sends the TV sound to it.
- **Runs in the background** and starts with the TV, so you don't need to open it.
- **Your controller as a TV remote:** move around the TV menus, your launcher, Netflix, YouTube… with the D-pad or stick (A = OK, B = Back, Guide = Home). It steps aside by itself in Moonlight, PlayHub and RetroArch, which read the controller directly. It learns your LG remote's exact buttons by itself: just use the app once with the LG remote.
- **Replaces the old "Gamepads" app** ([webos-gamepad](https://github.com/Superd22/webos-gamepad)): it fixes controller permissions so Moonlight, RetroArch and other apps can read them, and cleans up stale controller entries at startup. You can uninstall Gamepads.
- If you also use PlayHub, PlayHub reads your controller through it from the very first second.
- **Diagnostics** screen with its log, for when something doesn't connect.

It's a first version: speaker auto-connect and sound switching depend on your TV model.

## Coming soon

- A new name and look.

## Want to tweak it?

It's personal, but feel free to fork it and make it yours. The TV app is plain HTML/CSS/JS (Chromium 53–friendly) plus a small Node.js service (it has to run on the TV's very old Node), and the PC side is a single PowerShell 5.1 script plus a web page.

## Credits & thanks

Made by **Gabo** and **Claudio** 🎮

Standing on the shoulders of: [Moonlight TV](https://github.com/mariotaku/moonlight-tv) by mariotaku, [Sunshine](https://github.com/LizardByte/Sunshine) by LizardByte, [webOS Homebrew Channel](https://github.com/webosbrew/webos-homebrew-channel) by the webosbrew team, [SteamGridDB](https://www.steamgriddb.com), Steam's store data and Wikipedia. The Bluetooth bits were inspired by [webos-gamepad](https://github.com/Superd22/webos-gamepad) by Superd22.

*Not affiliated with LG, Valve, Nintendo, Sony, Microsoft or any of the projects above. Rooting your TV is at your own risk.*
