# Fortuna — iOS App (Capacitor)

Native iOS wrapper for Fortuna. Build in Appflow. No Mac required.

## Current TestFlight target
- Marketing version: **1.0**
- Build number: **2**
- Bundle id: `ceo.fortuna.app`
- App Store listing name: Fortuna Coach

## What's inside
- `www/index.html` — the app. `IS_IOS_APP = true` hides Stripe checkout (Apple 3.1.1). Pro bought on fortuna.ceo still unlocks here via the same Supabase login.
- `www/privacy.html` and `www/terms.html` — in-app legal pages
- `capacitor.config.json` — app id `ceo.fortuna.app`, name Fortuna
- `ios/App` — Xcode project used by Appflow

## After this repo update
1. Open Ionic Appflow → Fortuna → Builds
2. Start a new **iOS** production/App Store build from branch `main`
3. Wait for success
4. Deploy / upload the IPA to App Store Connect
5. In TestFlight, the new build shows as **1.0 (2)**
6. Install that build on the phone (pull to refresh TestFlight if it still shows 1.0 (1))

## Rules already baked in
- No in-app Stripe / Buy Pro checkout on iOS
- Encryption compliance flag set: `ITSAppUsesNonExemptEncryption = false`
- Launch screen is a dark Fortuna label (no missing Splash image)
- Junk leftover files from the first upload were removed from the repo root
