⋆˚✿˖° ✧･ﾟ: \*✧･ﾟ:🍄 ANDROID HARDENING GUIDE 🌻 \*:･ﾟ✧\*:･⋆˚✿˖°
---


Firstly, I'd like to preface this by saying that
no phone is 100% private or secure. Hardening is more about reducing
your attack surface, not achieving absolute anonymity.

This guide points readers towards privacy and security-focused tooling
and configuration. Installing a custom OS and unlocking a bootloader can
void warranties, may trigger carrier locks (e.g., some Verizon Pixels),
and, if done poorly, can brick a device. Always follow the official
install docs for your device. See the GrapheneOS and CalyxOS install
pages for the exact commands and checks.

---

## Table of contents

* I. Choosing the Right Starting Point
* II. Bootloader and Verified Boot
* III. Device Encryption
* IV. Google Services
* V. App Store 
* VI. Network Security
* VII. Permissions Hygiene
* VIII. Profiles & Compartmentalization
* IX. Browser Hardening
* X. Messaging & Communication
* XI. Additional Security Practices
* XII. Advanced Hardening (Optional)
* XIII. Threat Modeling
* XIV. Conclusion/Maintaining Security Habits

---

## I. Choosing the Right Starting Point

First off, your operating system choice matters more than anything else. Stock Android (the one
that comes preinstalled by Google, Samsung, Oneplus, etc.) is convenient
but packed with trackers, unnecessary preinstalled apps (bloatware), and
deep Google integration. If you're serious about privacy and control,
I'd recommend switching.

Side note: Only certain Android phones have good custom ROM support,
with the Google Pixel series being the most notable. There are others,
but it's typically older models with the best support. Opt for a Google
Pixel if you can.

.☘︎ ݁˖ Options:

* Overall BEST for security: GrapheneOS - It has a minimal attack
surface, a hardened kernel, and is actively maintained by a very small
but extremely skilled dev team. However, there are much fewer
conveniences, and some apps may not work perfectly.
* Best for balance (privacy and usability): CalyxOS - Much friendlier for beginners, comes
with microG (so you can still run most apps that need Google services),
but slightly less hardened than Graphene.
* Other option: LineageOS - Highly customizable, but not hardened out of the box and requires
additional steps to lock down.

Pick your OS. If you're serious about hardening, go Graphene. If you
want something that you can daily-drive without too many compromises, go
Calyx.

---

## II. Bootloader and Verified Boot
When you install a custom OS, you'll
need to unlock your bootloader. That's a major security risk if you
leave it unlocked.

* After flashing your OS, relock the bootloader. This ensures verified
boot and prevents malicious tampering.
* On GrapheneOS, relocking is
easy and encouraged. On Calyx, the same applies.

---

## III. Device Encryption
Most modern Android phones come encrypted by
default, but it's worth double-checking.

.☘︎ ݁˖

* On GrapheneOS and CalyxOS, encryption is enforced.
* Choose a strong device unlock method; ideally a passphrase (long password) rather than a
PIN or pattern. Patterns can be guessed via smudge marks and short PINs
are brute-forcable.

A passphrase doesn't have to be painful. Even 4 random words (from a
diceware list) are vastly stronger than a 6-digit PIN.

---

## IV. Google Services: To Keep or to Not Keep? 
This generally depends
on your OS choice.

* GrapheneOS: You can run Google services in a sandbox (separate
profile), which prevents them from having system-level privileges.
However, if you don't need them just skip them entirely.
* CalyxOS: Comes with microG (open-source replacement for Google Play Services).
This allows apps that need Google APIs (e.g., push notifications, maps,
banking apps) to work while still keeping tracking minimal.

Decide if you want Google compatibility (apps "just work") or stricter
privacy (apps may break).

---

## V. App Store 
You may be asking yourself, "If I'm avoiding google
entirely, how am I going to get my apps?" Well, there are a few options.

.☘︎ ݁˖

* F-Droid: Your best bet, however, it only has open-source apps. Great
resource for privacy-friendly tools.
* Aurora Store: Lets you anonymously download apps from Google Play without a Google account (can
be quite buggy, but if you retry installing the same app it'll
eventually work). 
* GrapheneOS Apps Repo: Preinstalled apps vetted by
the Graphene devs.

I personally recommend F-Droid as your primary source and using Aurora
only for unavoidable apps.

---

## VI. Network Security

* VPN: Only use this if you need to hide traffic from your ISP or local
network. A common misconception is that a VPN makes you anonymous, it
doesn't. Use a trustworthy, no-log provider. I don't recommend free
VPNS, they sell data. Only exception to this would be ProtonVPN, but the
free version isn't the best. My favorites are NordVPN and Mullvad. -
* Tor: Use Orbot or the Tor Browser for sensitive browsing. Slower, but
private.
* Private DNS: Go to Settings ➳ Network & internet ➳ Private
DNS. Use providers like Quad9 (9.9.9.9), Mullvad DNS, or NextDNS.

The easiest step is to set a Private DNS provider now. That's free
protection against some trackers and malicious domains.

---

## VII. Permissions Hygiene
This is where a lot of people get sloppy, but
it's truly one of the fastest, easiest, most doable tasks.

.☘︎ ݁˖

* Location: Only grant this when absolutely necessary. Use "only while
using the app" whenever possible. Something like your clock app or
Facebook is not going to need access to your location.
* Microphone & Camera: Disable by default, and only enable for apps that absolutely
need this.
* Background Permissions: Deny background access unless
absolutely essential.

Go through your app list and strip permissions aggressively. Most apps
ask for way more than they actually need.

---

## VIII. Profiles & Compartmentalization
GrapheneOS, CalyxOS, and Stock
Android all support user profiles. Treat them as sandboxes. I personally
hyper-compartmentalize so I have many user profiles. This can be
inconvenient though so I'll give the most basic setup.

‎. ݁⋆ ۶ৎ ݁˖ . ݁

* Use your main profile for personal apps (messaging, banking, etc). 
* Create a work profile or a separate user for experimental or untrusted
apps.
* Keep Google/MicroG (if needed) in a completely separate profile,
so it doesn't see everything you do.

I'd recommend creating at LEAST two profiles: one for essential apps and
one for apps that you don't trust.

---

## IX. Browser Hardening
There are many different choices when it comes
to browsers. I'll list a few I've tried and reccommend.

* Brave Browser: Hardened chromium, requires a little configuration but
overall a solid choice.
* Vanadium (GrapheneOS): Hardened Chromium
maintained by Graphene devs.
* Firefox (with uBlock Origin): Solid
option, especially if you configure privacy.resistFingerprinting.

I'd pick either Vanadium (if on Graphene) or hardened Firefox. Install
uBlock Origin and disable WebRTC leaks.

---

## X. Messaging & Communication

.☘︎ ݁˖

* Signal: Best balance of security and usability. Strong encryption,
but does require a working phone number.
* Session: Decentralized,
doesn't require a number, but slower.
* Element (Matrix): Good for
communities and federated chat.

I'd recommend using Signal for your main comms. If you need more
anonymity, experiment with Session. Molly is an excellent fork of Signal
that's more privacy-focused.

---

## XI. Additional Security Practices
* Updates: Always apply OS and app
updates as quickly as possible. Both GrapheneOS and CalyxOS are good at
delivering security patches fast.
* Disable Bluetooth & NFC when not in
use. Both expand attack surface.
* Avoid biometrics for unlock.
Fingerprints and face unlock are convenient, but not as safe legally
(you can be compelled to unlock with a finger, there are no laws
protecting you if an officer shoves your phone in your face, and this is
harder with a passphrase).
* Backups: GrapheneOS has encrypted backups. If using Calyx/Lineage, use SeedVault or manual encrypted backups.
* The more apps you have, the more risk. Every app is a potential leak.

---

## XII. Advanced Hardening (Optional)

𓂃 ࣪˖ ִֶָ⋅ᡣ𐭩 ་༘࿐

* Firewall: Use RethinkDNS + Firewall OR NetGuard to block background
connections.
* GrapheneOS has a per-app network and sensor permission
toggle. Use it.
* If threat model is high, consider Faraday bags when
traveling, or a hardware kill switch phone (e.g., Librem 5, though less
practical).

---

## XIII. Threat Modeling
Hardening is NOT one-size-fits-all. Ask yourself
who it is you're trying to avoid.

⊹₊ ˚‧︵‿₊୨ ♱ ୧₊‿︵‧ ˚ ₊⊹

* Are you just trying to avoid advertisers? CalyxOS and F-Droid may be
enough.
* Are you worried about government surveillance? GrapheneOS,
Tor, and strict compartmentalization.
* Are you just trying to have
fewer creepy trackers? Basic permission hygiene and Aurora Store.

Remember, your setup be tailored to fit YOUR needs, not someone else\'s
and not a checklist.

---

.𖥔 ݁ ˖ ✦ ‧₊˚ ⋅

(｡˃ ᵕ ˂ )੭♡ Hardening your Android device isn't just a one-and-done
thing. It's a habit. Stay curious, you should be constantly reviewing
permissions, questioning every app you install, and staying updated.
Remember: convenience is always the enemy of security. Balance wisely.

.𖥔 ݁ ˖ ✦ ‧₊˚ ⋅
