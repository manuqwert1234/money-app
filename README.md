# Money

See your bank balance and spending automatically, from your bank's texts and emails. Free, and private: everything is stored in **your own Google account**. Nobody else can see your money, including whoever shared the app with you.

- Balance over time, spending per day, week, month and year
- Spending by category (food, online delivery, shopping, transport, bills, people and more), learns when you correct it
- Works with any Indian bank that sends SMS or email alerts (Canara, HDFC, SBI, ICICI, Axis, Kotak, ESAF and others)
- Imports up to 3 years of past bank emails and texts on first setup

---

## Android (recommended)

1. Download **[Money.apk](https://github.com/manuqwert1234/money-app/releases/latest/download/Money.apk)** on your Android phone and open it. If Android asks, allow installing from your browser.
2. Open **Money** and tap **Start**.
3. Tap **Allow** when it asks to read texts.

That's it. No account and no sign-in. Money reads your bank texts from the last 3 years and every new one as it arrives. Everything stays **on your phone**. Texts from people's phone numbers are never read.

Optional: tap **Sign in with Google** instead (or later) if you also want your bank **emails** included, or want to use Money on more than one phone. That stores your data in your own Google account.

## iPhone

iPhones can't install apps outside the App Store, so Money runs as a home-screen app.

1. Open **https://manuqwert1234.github.io/money-tracker/** in **Safari**.
2. Tap **Sign in with Google** and allow the permission screens (same as Android, steps 4 and 5).
3. When you're back, tap **Share**, then **Add to Home Screen**.

Bank **emails** now work automatically. To also read bank **texts** on iPhone (optional, for instant updates):

1. In Money, go to **Settings**, then **Read bank texts too**, and tap **Copy SMS link**.
2. Tap **Get the shortcut**, then **Add Shortcut**, and paste the SMS link when asked.
3. Open **Shortcuts**, then **Automation**, then **+**, and type:
   `When I get a notification from Messages, run Send to Money with the notification`
4. Set it to run automatically, without asking.

Optional: ask questions about your money with Apple Intelligence from the **Ask** box on the Home screen (needs a shortcut named **Money Check**; the app shows how).

---

## How it works

| Part | Where it runs |
|---|---|
| Your data and server | A Google Sheet and Apps Script in **your** Google account |
| Bank emails | Read every 5 minutes by your server (read-only Gmail access) |
| Bank texts, Android | This app forwards bank SMS to your server |
| Bank texts, iPhone | An iOS Shortcuts automation |
| The app screens | https://manuqwert1234.github.io/money-tracker/ (shown inside the Android app) |

Source for the web app and server: [manuqwert1234/money-tracker](https://github.com/manuqwert1234/money-tracker).

## Build the Android app

```bash
flutter build apk --release --split-per-abi --target-platform android-arm64
```

The native parts are in `android/app/src/main/kotlin/in/moneyapp/money/`: `MainActivity.kt` (app screen and bridge), `SmsReceiver.kt` (new texts), `SmsSender.kt` (sending and the one-time import).
