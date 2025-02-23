# Web Browsers are evil =)

Skyddar du dig mot privat insyn och tar du din säkerhet på allvar när du surfar runt på nätet? Även om Googles motto "Don't be evil" senare ändrades till "Do the right thing" så finns det mycket att granska. 

[The Incognito Mode Myth Has Fully Unraveled](https://www.wired.com/story/google-chrome-incognito-mode-data-deletion-settlement/) visar att det du tror är privat surfning inte alls är så privat.

OM du gillar - eller inte bryr dig om - att din webbläsare och hemsidor spårar allt du gör, så kan du sluta läsa här och nu. Annars: läs vidare för tips och tricks som hjälper dig stärka din integritet!

## Innehållsförteckning
- [Web Browsers are evil =)](#web-browsers-are-evil-)
  - [Innehållsförteckning](#innehållsförteckning)
  - [Allmänt](#allmänt)
  - [Fingerprinting Protection](#fingerprinting-protection)
  - [Browser Inställningar](#browser-inställningar)
    - [Cookies](#cookies)
    - [Do Not Track](#do-not-track)
    - [Payments Methods och Payment Info](#payments-methods-och-payment-info)
    - [Offer to Manage Passwords](#offer-to-manage-passwords)
    - [Save and fill Addresses](#save-and-fill-addresses)
    - [Site Permissions](#site-permissions)
    - [Javascript](#javascript)
  - [Browser Extensions](#browser-extensions)
    - [Lösenord](#lösenord)
      - [Vanliga](#vanliga)
      - [KeePass-familjen](#keepass-familjen)
    - [Sökmotor](#sökmotor)
    - [Reklam / Ads](#reklam--ads)
    - [Privacy](#privacy)
    - [Terms of Service](#terms-of-service)
    - [Enhancer for YouTube](#enhancer-for-youtube)
    - [Bookmarks Sync](#bookmarks-sync)

## Allmänt
Jag har alltid varit en trogen användare av Google-världen och älskat [Chrome](https://www.google.com/chrome/) sedan starten. Chrome, som bygger på [Chromium](https://www.chromium.org/Home), kräver att du är inloggad och synkad med Googles tjänster, vilket både ger bekvämlighet och integritetsproblem. Därför rekommenderar jag alternativ:
- **Brave** ([länk](https://brave.com/)): En Chromiumbaserad webbläsare med inbyggd annons- och spårningsblockering.
- **Vivaldi** ([länk](https://vivaldi.com/)): Mycket anpassningsbar och rik på funktioner.
- **FireFox** ([länk](https://www.mozilla.org/en-US/firefox/new/)): Ett oberoende alternativ med stort fokus på integritet.  
  > Nytt: Firefox har nyligen införlivat säkerhetsförbättringar inspirerade av Chromiums avancerade sandbox-tekniker. Dessa åtgärder isolerar tillägg och processer bättre, vilket bidrar till högre säkerhet utan att kompromissa med prestanda.
- **LibreWolf** ([länk](https://librewolf.net/)): En variant av Firefox utan onödig spårning och telemetri.
- **Ungoogled Chromium** ([länk](https://ungoogled-software.github.io/ungoogled-chromium/)): Samma prestanda som Chromium men utan Googles spårning.
- **Zen Browser** ([länk](https://zenbrowser.com/)): En ny och minimalistisk webbläsare med hög säkerhet och integritet i fokus.
- **Epic Privacy Browser** ([länk](https://www.epicbrowser.com/)): Designad för maximal integritet och med inbyggt spårningsskydd.

På mobilen kan du även använda [DuckDuckGo](https://duckduckgo.com/app) för ökad säkerhet.

## Fingerprinting Protection

Webbläsare kan samla in unika fingeravtryck trots blockerade cookies. Fingeravtrycksmetoder utnyttjar detaljer som:
- Webbläsartyp, version och operativsystem.
- Installerade typsnitt, plugins, och systeminställningar.
- Skärmupplösning, färgdjup och grafikkort.
- Javascript-egenskaper: Canvas-rendering, WebGL, ljud- och videoformat.
- Användarbeteenden såsom musrörelser och tangenttryckningar.
- Även "utanför webbläsaren": Vissa avancerade tekniker kan försöka analysera skrivbordsbakgrund, systemfärger eller andra unika miljövariabler för att identifiera användare.

För att begränsa fingeravtryckning:
- Använd tillägg som CanvasBlocker (för Firefox) som stoppar eller förvränger Canvas-data.
- I Firefox, aktivera privacy.resistFingerprinting via about:config.
- Välj webbläsare med inbyggt fingeravtrycksskydd, exempelvis Brave eller Epic Privacy Browser.
- Justera sekretessinställningarna manuellt – standardinställningarna är ofta inte tillräckliga.
- Var medveten om att även systeminformation, som skrivbordsbakgrund eller färgscheman, kan utnyttjas för att skapa ett unikt digitalt fingeravtryck.

## Browser Inställningar

### Cookies
Cookies är ett nödvändigt ont på internet – de sparar allt från inloggningsuppgifter till diverse inställningar beroende på hemsida. Eftersom de flesta sidor slutar fungera om du stoppar alla cookies, rekommenderar jag att du:
- Blockerar tredjepartscookies (oftast kopplat till reklam)
- Behåller nödvändiga förstapartscookies

### Do Not Track
Detta skickar en signal till hemsidor att du inte vill bli spårad, men det är helt upp till varje enskild sida om de väljer att respektera det.

### Payments Methods och Payment Info
Varför skall en hemsida veta detta? Du kör med LastPass (eller annat lösenordshanteringsverktyg) ändå.

### Offer to Manage Passwords
Nej, låt inte webbläsaren hantera dina lösenord – överlämna det åt en dedikerad tjänst som LastPass.

### Save and fill Addresses
Använd hellre din lösenordshanterare, så slipp lita på inbyggda formulärfunktioner.

### Site Permissions
Ställ in alla site permissions på *Ask First* för att hålla kontrollen över vad som får åtkomst till din information.

### Javascript
ALLA hemsidor nyttjar idag JavaScript. Vill du undvika spårning och potentiella säkerhetshot kan du stänga av JavaScript, men det blir jobbigt. Mitt råd: aktivera JavaScript endast på välkända sidor och överväg att använda tillägg som blockar oönskade skript.

## Browser Extensions

[Chrome Extensions](https://chrome.google.com/webstore/category/extensions) funkar i alla Chromium-baserade webbläsare.

Följande extensions förbättrar din säkerhet och minskar reklam:

### Lösenord
Installera ett dedikerat Password Vault. LastPass hade länge en stark position, men sedan 2021 har de begränsat gratisversionen till en enhet. Här är några alternativ:

#### Vanliga
- [ZoHo Vault](https://www.zoho.com/vault/) ([Chrome](https://chrome.google.com/webstore/detail/zoho-vault/igkpcodhieompeloncfnbekccinhapdb), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/zoho-vault/), [Android](https://play.google.com/store/apps/details?id=com.zoho.vault)) – bra gratisversion.
- [LastPass](https://www.lastpass.com/) ([Chrome](https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd), [FireFox](https://addons.mozilla.org/en-US/firefox/addon/lastpass-password-manager/), [Android](https://play.google.com/store/apps/details?id=com.lastpass.lpandroid)) – med den nämnda begränsningen.
- [Microsoft Autofill](https://support.microsoft.com/en-us/account-billing/download-and-install-the-microsoft-authenticator-app-351498fc-850a-45da-b7b6-27e523b8702a) ([Chrome](https://chrome.google.com/webstore/detail/microsoft-autofill/fiedbfgcleddlbcmgdigjgdfcggjcion), Edge ingår i webbläsaren, [Android](https://play.google.com/store/apps/details?id=com.azure.authenticator)) – optimal om du redan använder Microsoft Authenticator.
- [NordPass](https://nordpass.com/personal-password-manager/) ([Chrome](https://chrome.google.com/webstore/detail/nordpass%C2%AE-password-manage/fooolghllnmhmmndgjiamiiodkpenpbb), [Firefox](https://addons.mozilla.org/en-US/firefox/addon/nordpass-password-manager/), [Android](https://play.google.com/store/apps/details?id=com.nordpass.android.app.password.manager)) – ett trevligt alternativ för de som gillar NordVPN och deras ekosystem.

#### KeePass-familjen
- [KeePass](https://keepass.info/) ([Chrome](https://chrome.google.com/webstore/search/keepass?_category=extensions), [FireFox](https://addons.mozilla.org/en-US/firefox/search/?q=keepass&type=extension), [Android](https://play.google.com/store/search?q=keepass&c=apps)) – enbart för Windows.
- [KeePassXC](https://keepassxc.org/) ([Chrome](https://chrome.google.com/webstore/search/keepassxc?_category=extensions), [FireFox](https://addons.mozilla.org/en-US/firefox/search/?q=keepassxc&type=extension), [Android](https://play.google.com/store/search?q=keepass&c=apps)) – fungerar på Windows, macOS och Linux. *KeePassXC är aktivare i utvecklingen än KeePass.*

*Det är enkelt att exportera och importera dina lösenord mellan dessa olika plattformar.*

### Sökmotor
Googles motto "Do the right thing" påverkar även sökresultaten. Prova istället:
- [Brave Search](https://search.brave.com/) – spårar inte och manipulerar inte dina resultat.
- [DuckDuckGo](https://duckduckgo.com) – hade samma filosofi som Brave men har på senare tid blivit något mer begränsad.
- [Qwant](https://www.qwant.com/) – "The search engine that doesn't know anything about you."
- [SearXNG](https://searx.space/) – en metasearch som inte spårar eller profilerar sina användare.

### Reklam / Ads
Installera en kraftfull ad-blocker för en renare surfupplevelse, exempelvis:
- [uBlock Origin](https://github.com/gorhill/uBlock#ublock-origin) – tillgängligt för både [Chrome](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm) och [Firefox](https://addons.mozilla.org/addon/ublock-origin/).

### Privacy
För att snabbt få en överblick över hur "säker" en hemsida är, använd:
- [DuckDuckGo Privacy Essentials](https://chrome.google.com/webstore/detail/duckduckgo-privacy-essent/bkdgflcldnnnapblkhphbgpggdiikppg) för Chrome eller [Firefox-versionen](https://addons.mozilla.org/en-US/firefox/addon/duckduckgo-for-firefox/).

### Terms of Service
Vill du hålla koll på hemsidors användarvillkor? Kolla in:
- [Terms of Service; Didn'r Read](https://tosdr.org/) – finns för både [Chrome](https://chrome.google.com/webstore/detail/hjdoplcnndgiblooccencgcggcoihigg) och [Firefox](https://addons.mozilla.org/en-US/firefox/addon/terms-of-service-didnt-read/).

### Enhancer for YouTube
För den ultimata YouTube-upplevelsen finns:
- [Enhancer for YouTube](https://chrome.google.com/webstore/detail/enhancer-for-youtube/ponfpcnoihfmfllpaingbgckeeldkhle) – tillgängligt för [Chrome](https://chrome.google.com/webstore/detail/enhancer-for-youtube/ponfpcnoihfmfllpaingbgckeeldkhle) och [Firefox](https://addons.mozilla.org/addon/enhancer-for-youtube/).

### Bookmarks Sync
xBrowserSync är ett smart verktyg för att anonymt synkronisera dina bokmärken över olika enheter:
- Installera för [Chrome](https://chrome.google.com/webstore/detail/xbrowsersync/lcbjdhceifofjlpecfpeimnnphbcjgnc) och [Firefox](https://addons.mozilla.org/en-US/firefox/addon/xbs/).

xBrowserSync gör att du får ett unikt ID för dina bokmärken som skyddas med ett eget lösenord – perfekt om du vill hålla allt privat och synkroniserat.

*ID: 6bf1e2d8f8ed42cd80dc9b3beeaf5113*
