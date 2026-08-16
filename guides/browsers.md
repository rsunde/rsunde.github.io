# Web Browsers are evil =)

Skyddar du dig mot privat insyn och tar du din säkerhet på allvar när du surfar runt på nätet? Även
om Googles motto "Don't be evil" senare ändrades till "Do the right thing" så finns det mycket att
granska.

[The Incognito Mode Myth Has Fully Unraveled](https://www.wired.com/story/google-chrome-incognito-mode-data-deletion-settlement/)
visar att det du tror är privat surfning inte alls är så privat.

OM du gillar — eller inte bryr dig om — att din webbläsare och hemsidor spårar allt du gör, så kan du
sluta läsa här och nu. Annars: läs vidare.

## Innehåll

- [Webbläsare](#webbläsare)
- [Fingerprinting](#fingerprinting)
- [Inställningar i webbläsaren](#inställningar-i-webbläsaren)
- [Lösenordshanterare](#lösenordshanterare)
- [Tillägg](#tillägg)
- [VPN](#vpn)
- [Bokmärkessynkronisering](#bokmärkessynkronisering)

## Webbläsare

Jag har alltid varit en trogen användare av Google-världen och älskat
[Chrome](https://www.google.com/chrome/) sedan starten. Chrome, som bygger på
[Chromium](https://www.chromium.org/Home), vill att du är inloggad och synkad med Googles tjänster,
vilket både ger bekvämlighet och integritetsproblem. Därför rekommenderar jag alternativ:

- **[Mullvad Browser](https://mullvad.net/browser)** — byggd av Mullvad tillsammans med Tor Project.
  I praktiken Tor Browser utan Tor-nätverket: samma kraftfulla skydd mot fingeravtryckning, men över
  din vanliga uppkoppling. Kräver inget Mullvad-abonnemang och kostar ingenting.
- **[Firefox](https://www.mozilla.org/firefox/new/)** — det oberoende alternativet. Viktigast av
  allt: den egna motorn, som inte är Chromium. Se [Manifest V3](#manifest-v3) nedan.
- **[LibreWolf](https://librewolf.net/)** — Firefox utan telemetri, med hårdare
  standardinställningar från start.
- **[Brave](https://brave.com/)** — Chromiumbaserad med inbyggd annons- och spårningsblockering.
- **[Vivaldi](https://vivaldi.com/)** — mycket anpassningsbar och funktionsrik.
- **[Ungoogled Chromium](https://ungoogled-software.github.io/ungoogled-chromium/)** — samma
  prestanda som Chromium, utan Googles integrationer.

På mobilen fungerar [DuckDuckGo](https://duckduckgo.com/app) eller Firefox Focus bra för vardaglig
surf.

> **Det viktigaste valet är motorn, inte varumärket.** Brave, Vivaldi och Ungoogled Chromium är alla
> Chromium i botten och ärver Googles beslut om vad tillägg får göra. Firefox-familjen gör inte det.

## Fingerprinting

Webbläsare kan identifieras med ett unikt fingeravtryck trots blockerade cookies. Metoderna utnyttjar
detaljer som:

- Webbläsartyp, version och operativsystem.
- Installerade typsnitt, plugins och systeminställningar.
- Skärmupplösning, färgdjup och grafikkort.
- JavaScript-egenskaper: Canvas-rendering, WebGL, ljud- och videoformat.
- Användarbeteenden som musrörelser och tangenttryckningar.

Poängen är att ingen enskild uppgift identifierar dig — men tillsammans blir kombinationen unik.

För att begränsa fingeravtryckning:

- **Använd en webbläsare som är byggd för det.** Mullvad Browser och Tor Browser får alla användare
  att se likadana ut, vilket är det enda som fungerar riktigt bra. Brave har också inbyggt skydd.
- I Firefox: aktivera `privacy.resistFingerprinting` via `about:config`.
- Justera sekretessinställningarna manuellt — standardinställningarna räcker sällan.

> **Motverka inte varandra.** Att stapla tillägg som förvränger Canvas-data gör dig ofta *mer* unik,
> inte mindre — nu är du den enda med precis den kombinationen av lögner. Att smälta in slår att
> gömma sig.

## Inställningar i webbläsaren

### Cookies

Cookies är ett nödvändigt ont — de sparar allt från inloggningar till inställningar. Eftersom de
flesta sidor slutar fungera helt utan dem:

- Blockera tredjepartscookies (oftast kopplade till reklam).
- Behåll nödvändiga förstapartscookies.

### Do Not Track och Global Privacy Control

**Do Not Track är dött.** Signalen skickades i över ett decennium och det stod varje sida fritt att
strunta i den, vilket de också gjorde. Standardiseringsarbetet lades ner och webbläsarna har plockat
bort inställningen.

Efterträdaren heter **Global Privacy Control (GPC)** och skiljer sig på en avgörande punkt: den är
juridiskt bindande i vissa jurisdiktioner, bland annat under Kaliforniens dataskyddslag. Det är
skillnaden mellan en artig förfrågan och ett krav. Aktivera den om din webbläsare stödjer den — men
räkna inte med den utanför de områden där den har rättslig verkan.

### Betalningsuppgifter och adresser

Varför skulle webbläsaren behöva spara detta? Du har en lösenordshanterare ändå. Stäng av både
sparade betalningsmetoder och automatisk ifyllnad av adresser.

### Låt inte webbläsaren hantera lösenorden

Använd en dedikerad lösenordshanterare istället — se [nedan](#lösenordshanterare). Webbläsarens
inbyggda lager är knutet till just den webbläsaren och skyddas ofta bara av att du är inloggad.

### Site Permissions

Ställ in samtliga behörigheter på *Ask First*. Kamera, mikrofon, plats och notiser ska aldrig vara
påslagna som standard.

### JavaScript

Alla hemsidor nyttjar idag JavaScript, och det är också vägen in för både spårning och de flesta
säkerhetshål. Att stänga av det helt gör webben obrukbar. Rimlig medelväg: låt det vara på, men kör
en ordentlig blockerare och var restriktiv med behörigheter.

## Lösenordshanterare

Installera en dedikerad lösenordshanterare. Vilken spelar mindre roll än att du har en — men leta
efter det här, i tur och ordning:

1. **Öppen källkod och granskad** av en oberoende part.
2. **Export utan låsning.** Kan du inte enkelt få ut allt, byter du aldrig igen.
3. **Kryptering på klienten**, så leverantören aldrig ser dina lösenord i klartext.
4. **Fungerar på alla dina enheter** — annars används den inte.

- **[Bitwarden](https://bitwarden.com/)** — öppen källkod, granskad, generös gratisnivå och går att
  driva själv om du vill. Den enklaste rekommendationen för de flesta.
- **[Proton Pass](https://proton.me/pass)** — från Proton, schweizisk och öppen källkod. Kan skapa
  e-postalias, vilket gör att varje tjänst får en egen adress du kan stänga av om den läcker.
- **[KeePassXC](https://keepassxc.org/)** — en lokal krypterad fil, ingen molntjänst alls. Fungerar
  på Windows, macOS och Linux, och du synkar själv om du vill. Mest kontroll.
- **[KeePass](https://keepass.info/)** — originalet, Windows-fokuserat. KeePassXC är aktivare
  underhållet.

> **Molntjänst eller lokal fil?** Med en molntjänst litar du på leverantörens kryptering och
> driftsäkerhet. Med KeePassXC litar du på din egen backup-rutin. Båda är rimliga val — men gör det
> medvetet, och kom ihåg att lösenordsvalv har blivit stulna förr. Ett långt huvudlösenord är det som
> avgör om ett läckt valv går att knäcka.

## Tillägg

### Reklamblockering

- **[uBlock Origin](https://github.com/gorhill/uBlock)** — fortfarande måttstocken, och det enda
  tillägg de flesta behöver.

### Manifest V3

Det här är inte längre en kommande förändring, utan ett avgjort läge.

Chrome har gått över till Manifest V3 och avvecklat den gamla tilläggsarkitekturen. Det API som
blockerare använde för att granska och stoppa nätverksförfrågningar innan de skickades finns inte
kvar — tillägg får nu istället lämna in en lista med regler i förväg som webbläsaren tillämpar åt
dem. Konsekvensen är att den ursprungliga uBlock Origin inte fungerar i Chrome. Kvar finns uBlock
Origin Lite, som gör vad MV3 tillåter, vilket är mindre.

**Firefox stödjer Manifest V3 — men behöll det blockerande API:et.** Det är den avgörande
skillnaden, och den missförstås ofta: frågan är inte vilken manifest-version en webbläsare kör, utan
om den låter tillägg faktiskt stoppa trafik. Firefox gör det. Chromium-baserade webbläsare gör det
inte, oavsett hur integritetsvänliga de marknadsför sig som.

Vill du ha blockering på den nivå du är van vid är valet därmed avgjort åt dig.

### Övriga tillägg

- **[Terms of Service; Didn't Read](https://tosdr.org/)** — betygsätter användarvillkor så du slipper
  läsa dem.
- **[Enhancer for YouTube](https://www.mrfdev.com/enhancer-for-youtube)** — hastighet, ljudnivå och
  utseende på YouTube.

### Sökmotorer

- **[Brave Search](https://search.brave.com/)** — eget index, spårar inte.
- **[Mullvad Leta](https://leta.mullvad.net/)** — sökning utan spårning, för Mullvad-kunder.
- **[DuckDuckGo](https://duckduckgo.com)** — enklast att byta till, men bygger till stor del på Bings
  index.
- **[Qwant](https://www.qwant.com/)** — europeiskt alternativ.
- **[SearXNG](https://searx.space/)** — metasökmotor som varken spårar eller profilerar. Kan köras
  själv.

## VPN

Ett VPN flyttar förtroendet — det tar bort din internetleverantörs insyn och ger den till
VPN-leverantören istället. Det gör dig inte anonym, och det stoppar inte fingeravtryckning. Använt
med rätt förväntningar är det ändå ett av de vassare verktygen.

Leta efter oberoende granskningar, öppen källkod i klienterna och en ägarstruktur du kan se.

- **[Mullvad VPN](https://mullvad.net/)** — kräver varken e-postadress eller namn; du får ett
  kontonummer och kan betala kontant om du vill. Öppen källkod och återkommande externa granskningar.
  Så nära "vet ingenting om dig" som en betaltjänst kommer.
- **[Proton VPN](https://protonvpn.com/)** — schweiziskt, öppen källkod, granskat, och det enda
  seriösa alternativet med en riktig gratisnivå utan datatak.

Samma leverantör har även **[Proton Mail](https://proton.me/mail)**, med kryptering och samma
juridiska hemvist — värt att titta på om du också vill flytta e-posten från en annonsfinansierad
aktör.

> **Ett VPN löser inte det du tror.** Är du inloggad på ditt Google-konto spelar det ingen roll var
> trafiken kommer ut. VPN skyddar mot din nätoperatör och mot att din IP-adress används för att
> koppla ihop dig — inte mot tjänster du frivilligt identifierar dig för.

## Bokmärkessynkronisering

**[xBrowserSync](https://www.xbrowsersync.org/)** synkroniserar bokmärken mellan enheter utan konto.
Du får ett ID och väljer ett eget lösenord; allt krypteras innan det lämnar maskinen.

Kom ihåg att ID:t är nyckeln till din data — behandla det som ett lösenord och dela det aldrig.
Tappar du lösenordet finns ingen återställning, vilket är hela poängen.
