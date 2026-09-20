# Fortuna — iOS App (Capacitor)

This wraps your existing `Fortuna.html` into a native iOS app. No Mac needed — you'll build in the cloud.

## What's inside
- `www/index.html` — the app (iOS build: Stripe buy buttons are hidden to comply with Apple guideline 3.1.1; Pro purchased on fortuna.ceo still unlocks in the app since it shares the same Supabase account)
- `capacitor.config.json` — app id `ceo.fortuna.app`, name "Fortuna"
- `package.json` — Capacitor 6 dependencies

## Build in the cloud (no Mac)

### Option A — Ionic Appflow (easiest for Capacitor)
1. Create a free GitHub account and push this folder to a new repo:
   - On github.com → New repository → name it `fortuna-app` → upload these files (Add file → Upload files)
2. Sign up at ionic.io/appflow (free tier works for a few builds)
3. Connect your GitHub repo → create an **iOS build** (Appflow builds on their Macs)
4. For App Store signing, Appflow walks you through connecting your Apple Developer account and generating certificates/profiles automatically
5. Download the `.ipa` → upload to App Store Connect via Appflow's direct deploy, or Apple's Transporter web/API flow

### Option B — Codemagic
1. Push this folder to GitHub (same as above)
2. Sign up at codemagic.io (free build minutes)
3. It auto-detects Capacitor; pick the iOS workflow, connect your Apple Developer account (API key from App Store Connect → Users and Access → Keys)
4. Run the build → it can publish straight to App Store Connect

## Before submitting to the App Store
- [ ] App icon: add `ios/App/App/Assets.xcassets` icons (the cloud build tools can generate from one 1024×1024 PNG — ask me and I'll make the icon)
- [ ] Privacy policy live at https://fortuna.ceo/privacy.html (file provided separately — upload to Netlify)
- [ ] App Store Connect: create the app record (bundle id `ceo.fortuna.app`), fill in description, keywords, screenshots (use an iPhone simulator screenshot service or take them from the build's emulator), age rating
- [ ] In-App Purchase: Pro subscriptions in the iOS app must use Apple IAP (RevenueCat recommended). Until that's integrated, the iOS build hides purchase buttons — users subscribe on the web and it unlocks in-app. Decide before launch whether to ship v1 like this or add IAP first.

## Updating the app later
Replace `www/index.html` with a new Fortuna build, push to GitHub, trigger a new cloud build, submit the update in App Store Connect.
