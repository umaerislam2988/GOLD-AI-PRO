# GOLD AI PRO — Android source project

This is an early, signal-only Android prototype for XAUUSD M1. It uses the public BiQuote REST endpoints:
- `https://biquote.io/api/XAUUSD?allowStale=false`
- `https://biquote.io/api/XAUUSD/ohlc?interval=1m&limit=260`

## Important limitations
- BiQuote is an independent aggregated MT5 feed, not the user's Exness quote. Price and spread can differ.
- The app estimates liquidity from recent candle swing highs/lows. It does not see a true global order book, stop-loss clusters, or institutional resting liquidity.
- The signal logic is a simple experimental rule (EMA20/EMA200 + RSI14 + 20-bar sweep). It is not a trained AI model and does not predict profits.
- Data is refreshed while the app is open. This first version does not promise background monitoring after Android suspends/closes the app.
- Notifications are generated for new BUY/SELL states while the app is running and notification permission is granted.
- No trade execution, broker login, or credentials are used.

## Build APK in GitHub Actions (phone-friendly cloud build)
1. Create a private GitHub repository and upload this project folder's contents.
2. Open the repository's **Actions** tab.
3. Run **Build GOLD AI PRO APK** (or push to `main`).
4. Download the `GOLD-AI-PRO-debug-apk` artifact and extract `app-debug.apk`.
5. Install on Android. Android may ask you to allow installation from your browser/file manager.

For local Android Studio builds, run `gradle assembleDebug` with JDK 17 and Android SDK 35 installed.
