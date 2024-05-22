# Web Browsers are evil =)

Skyddar du dig mot privat insyn och tar du din säkerhet på allvar när du surfar runt på nätet?

Googles motto "Don't be evil" byttes mot "Do the right thing", vilket kan tolkas lite hur du vill.

[The Incognito Mode Myth Has Fully Unraveled](https://www.wired.com/story/google-chrome-incognito-mode-data-deletion-settlement/)

OM du gillar eller inte bryr dig om att din Browser eller alla hemsidor spårar allt du gör så kan du sluta läsa här och nu, annars följ lite tips och tricks nedan...

## Allmänt

### Browsers
Själv är jag väldigt inlåst i Google världen och har gillat och uppskattat [Chrome](https://www.google.com/chrome/) sen start, Chrome är Googles skal som bygger på [Chromium](https://www.chromium.org/Home), Microsoft bytte till att använda Googles Chromium i [Edge](https://www.microsoftedgeinsider.com) vilket inte är oväntat då Chromium är väldigt bra, Både Chrome och Edge påtvingar lite att du måste vara inloggad och syncad med deras tjänster, vilket har sina för och nackdelar. Jag rekommenderar därför ett par alternativ, [Brave](https://brave.com/), [Vivaldi](https://vivaldi.com/).

[Chrome Extensions](https://chrome.google.com/webstore/category/extensions) funkar i alla Chromium browsers.

Sen har du givetvis [FireFox](http://www.mozilla.org/en-US/firefox/new/).

På mobilen kan du även använda [DuckDuckGo](https://duckduckgo.com/app) vilket ger dig mer säkerhet.

## Browser Inställningar

### Cookies
Cookies är ett nödvändigt ont på internet, cookies sparar in-loggnings uppgifter och en massa andra saker(vilket helt beror på hemsidan) det som är jobbigt dock är att nästan alla hemsidor slutar fungera om du stoppar alla cookies, därför bör du i alla fall stoppa tredje-part cookies, vilket oftast är reklam.

### Do Not Track
Detta handlar om reklam, din browser skickar en request till hemsidan att du inte vill bli spårad, det är helt upp till hemsidan att bry sig.

### Payments Methods och Payment Info
Varför skall en hemsida veta detta ? Du kör med LastPass ändå.

### Offer to Manage Passwords
Nej, gör inte det, du använder LastPass istället.

### Save and fill Addresses
Nej, gör inte det, du använder LastPass istället.

### Site Permissions
Alla inställningar bör vara *Ask First*.

### Javascript
ALLA hemsidor idag nyttjar Javascript, om du verkligen vill stoppa all form av spårning och andra potentiella farliga saker bör du stänga av Javascript. Kommer bli lite jobbigt en stund men efter att du tillåtit Javascript på dina vanliga hemsidor så är du relativt säker när du besöker nya och okända hemsidor.

## Browser Extensions
Följande Extensions ger dig en mer säker och reklamfri upplevelse när du snurrar runt på nätet.

### Lösenord
Installera ett Password Vault, lastpass var bäst (för mig) väldigt många år, men 2021 så gick dem och begränsade gratis versionen till en enhet, laptop eller mobil, så tänk på det när du väljer:

#### Allmänt

[ZoHo Vault](https://www.zoho.com/vault/) ([Chrome](https://chrome.google.com/webstore/detail/zoho-vault/igkpcodhieompeloncfnbekccinhapdb), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/zoho-vault/), [Android](https://play.google.com/store/apps/details?id=com.zoho.vault)), bra gratis version.

[LastPass](https://www.lastpass.com/) ([Chrome](https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/lastpass-password-manager/), [Android](https://play.google.com/store/apps/details?id=com.lastpass.lpandroid)), begränsad gratis version.

[Microsoft Autofill](https://support.microsoft.com/en-us/account-billing/download-and-install-the-microsoft-authenticator-app-351498fc-850a-45da-b7b6-27e523b8702a) ([Chrome](https://chrome.google.com/webstore/detail/microsoft-autofill/fiedbfgcleddlbcmgdigjgdfcggjcion), Edge ingår i browser, Firefox saknas, [Android](https://play.google.com/store/apps/details?id=com.azure.authenticator)), om Microsoft Authenticator redan sköter dina multi factor logins (mfa/2fa), så varför inte kombinera med lösenord också.

[NordPass](https://nordpass.com/personal-password-manager/) ([Chrome](https://chrome.google.com/webstore/detail/nordpass%C2%AE-password-manage/fooolghllnmhmmndgjiamiiodkpenpbb), [Firefox](https://addons.mozilla.org/en-US/firefox/addon/nordpass-password-manager/), [Android](https://play.google.com/store/apps/details?id=com.nordpass.android.app.password.manager)), du kanske redan använder NordVPN och gillar Nord appar, annars ett trevligt alternativ till de andra.

#### KeePass familjen
Helt gratis och open source *offline* Password Vault, men man måste sköta hanteringen av sin lösenordsfil själv, kopiera eller synca till olika enheter för användning.

[KeePass](https://keepass.info/) ([Chrome](https://chrome.google.com/webstore/search/keepass?_category=extensions), [FireFox](https://addons.mozilla.org/en-US/firefox/search/?q=keepass&type=extension), [Android](https://play.google.com/store/search?q=keepass&c=apps)), enbart för Windows.

[KeePassXC](https://keepassxc.org/) ([Chrome](https://chrome.google.com/webstore/search/keepassxc?_category=extensions), [FireFox](https://addons.mozilla.org/en-US/firefox/search/?q=keepassxc&type=extension), [Android](https://play.google.com/store/search?q=keepass&c=apps)), för Windows, osX och Linux. *KeePassXC verkar vara mer aktiv i utvecklingen än KeePass.*

*Det är enkelt att exportera och importera dina lösenord mellan de olika platformarna.*

### Sökmotor
Googles motto "Do the right thing" påverkar dina sökresultat, därför rekommenderar jag att byta till;

[Brave](https://search.brave.com/) som varken spårar eller "gömmer" vissa resultat,

[DuckDuckGo](https://duckduckgo.com) brukade vara som Brave, men har bevisligen gått o blivit mer "begränsad",

[Qwant](https://www.qwant.com/) "The search engine that doesn't know anything about you",

[SearXNG](https://searx.space/) "SearXNG is a free internet metasearch engine which aggregates results from various search services and databases. Users are neither tracked nor profiled.".

### Reklam / Ads
Installera en BRA Ad-blocker, jag rekommenderar [uBlock](https://github.com/gorhill/uBlock#ublock-origin), installera till [Chrome](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm), [Firefox](https://addons.mozilla.org/addon/ublock-origin/).

### Privacy
DuckDuckGo har en egen extension som visar dig ett betyg på hur "säker" en hemsida är, [Chrome](https://chrome.google.com/webstore/detail/duckduckgo-privacy-essent/bkdgflcldnnnapblkhphbgpggdiikppg), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/duckduckgo-for-firefox/).

### Terms of Service
[Terms of Service; Didn'r Read](https://tosdr.org/) är en hemsida för att hålla koll på hur hemsidors användarvilkor är skrivna och hur dem ändras. Installera för [Chrome](https://chrome.google.com/webstore/detail/hjdoplcnndgiblooccencgcggcoihigg), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/terms-of-service-didnt-read/).

### Enhancer for YouTube
Enhancer for YouTube är en extension som förbättrar YouTube genom lite hacks, den tar även bort reklam, installera för [Chrome](https://chrome.google.com/webstore/detail/enhancer-for-youtube/ponfpcnoihfmfllpaingbgckeeldkhle), [FireFox](https://addons.mozilla.org/addon/enhancer-for-youtube/).

### Bookmarks Sync
xBrowserSync är inget säkerhetsverktyg, men det är smart att säkra upp dina bookmarks, installera för [Chrome](https://chrome.google.com/webstore/detail/xbrowsersync/lcbjdhceifofjlpecfpeimnnphbcjgnc), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/xbs/).

xBrowserSync är helt anonymt, du får ett unikt ID för dina bookmarks som du skyddar med ett eget lösenord, och med detta ID kan du sen ställa in varje dator och browser med samma bookmarks.

ID: 6bf1e2d8f8ed42cd80dc9b3beeaf5113
