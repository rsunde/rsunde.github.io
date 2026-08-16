# Den nya integritetsmardrömmen: AI-"funktioner" i moderna operativsystem

Teknikjättarna pushar AI överallt – men till vilket pris? Låt oss titta på den obekväma sanningen.

## Innehåll

- [Integritetskrisen med AI](#integritetskrisen-med-ai)
- [Mobile Device Hell](#mobile-device-hell)
- [Min rekommendation](#min-rekommendation)
- [Arch Linux](#arch-linux)
- [Windows 11 LTSC](#windows-11-ltsc)
- [Rensa upp i Windows](#rensa-upp-i-windows)
- [Gaming](#gaming)
- [Final Thoughts](#final-thoughts)

---

## Integritetskrisen med AI

**Windows 11:s AI-invasion:**

- NPU (Neural Processing Unit) – inbyggd hårdvara för datainsamling
- Copilot – alltid "vakande", alltid "lärande"
- AI-komponenter som telefonerar hem
- Cortana är borta, men övervakningen lever kvar i nya former

**Apples neurala motor:**

- Apple Silicon innehåller dedikerad AI-hårdvara i varje chip
- "Privat" bearbetning betyder ändå att dina data analyseras
- Siris "offline"-funktion samlar ändå beteendedata
- Bildanalys sker lokalt, men resultatet stannar sällan där

**Android och ChromeOS:**

- Googles Tensor-chip – designade för AI på enheten
- "Hjälpsamma" funktioner kräver konstant datainsamling
- Varje interaktion tränar deras modeller
- Din enhet är i praktiken en datainsamlingsterminal

**Det verkliga problemet:**

- Du kan inte inaktivera AI-funktionerna på hårdvarunivå
- "Lokal bearbetning" betyder inte privat
- Tillverkarna bygger in övervakningen direkt i kislet
- Även "offline"-AI kräver massiv datainsamling
- Varje "hjälpsam" funktion är ytterligare ett intrång

**Vad du kan göra:**

- Undvik hårdvara med dedikerade AI-chip om möjligt
- Inaktivera alla "smarta" funktioner och assistenter
- Använd ett operativsystem som respekterar dig
- Blockera telemetri på nätverksnivå
- Lita inte på några standardinställningar

> Det finns inte längre någon konsumentversion av något stort operativsystem utan AI-funktioner. Det
> är inte en fråga om att hitta den rena versionen — den finns inte. Antingen väljer du en utgåva som
> aldrig var tänkt för konsumenter, eller så lämnar du skeppet helt. Det är hela urvalet.

---

## Mobile Device Hell

**Android-mardrömmen:**

- Google-tjänster = övervakningstjänster
- Varje app vill åt kamera, plats och kontakter
- "Digital Wellbeing" = beteendespårning
- Att installera egna ROM:ar blir svårare för varje år
- Enhetsintygande blockerar bank- och betalappar på anpassade ROM:ar

**iOS-fängelset:**

- Sidladdning finns numera inom EU, tack vare DMA — men villkoren är utformade för att göra det
  obekvämt, och utanför EU finns det fortfarande inte
- Den neurala motorn är alltid aktiv
- "Integritetsfunktioner" är till stor del marknadsföring
- Säkerhetskopior är okrypterade nog för att vara intressanta

**Faktiska mobilalternativ:**

- GrapheneOS (endast Pixel-telefoner) – det enda som är seriöst genomtänkt
- CalyxOS (begränsat utbud)
- Linux-telefoner (lycka till): PinePhone, Librem 5

**Skadebegränsning:**

- Inaktivera Google Play Services
- Använd F-Droid istället för Play Store
- Använd aldrig förinstallerade kameraprogram
- Överväg en enkel "dum telefon" för samtal

Kom ihåg: din telefon är en spårningsenhet som även kan ringa.

---

## Min rekommendation

Det här är inte en genomgång av alla alternativ. Jag har gått igenom dem — distributionerna,
utgåvorna, de "avbloatade" Windows-varianterna, kompromisserna — och landat i två svar. Resten av
den här sidan handlar om dem.

**Arch Linux är standardvalet, både på skrivbordet och på servern.** Det är där du kommer längst,
och det enda av alternativen där påståendet "jag vet vad som körs på min maskin" faktiskt är sant.

**Windows 11 LTSC är svaret när du behöver Windows** — för spel, eller för program som helt enkelt
inte finns någon annanstans. Det är Windows utan det Microsoft säljer dig som funktioner.

Allt däremellan är kompromisser som kräver samma arbete och ger sämre resultat. De distributioner som
gör det enkelt åt dig gör också valen åt dig, och de avbloatade Windows-varianterna river bort saker
som kommer tillbaka vid nästa uppdatering.

---

## Arch Linux

Arch är inte svårt för sakens skull. Poängen är att ingenting installeras utan att du bett om det.
Det finns ingen leverantörsprogramvara att rensa bort, ingen telemetri att stänga av och ingen
assistent att avinstallera — systemet börjar tomt, och det du bygger är det du får.

Det är också därför det fungerar lika bra i båda rollerna. Ett skrivbord och en server skiljer sig åt
i vad du installerar ovanpå, inte i vad som ligger under.

**Varför Arch och inte något annat:**

- **Du ser precis vad som körs.** Det är hela integritetsargumentet, i praktiken snarare än i en
  inställningsdialog.
- **[Arch Wiki](https://wiki.archlinux.org/)** är den bästa dokumentationen i Linuxvärlden, med bred
  marginal. Den är användbar även om du kör en annan distribution — vilket säger en del.
- **Rullande utgåvor.** Inga stora versionshopp, ingen ominstallation vartannat år, ingen
  distributionsuppgradering som spårar ur halvvägs.
- **AUR** ger dig i praktiken all mjukvara som finns för Linux.
- **Installationen är inte längre ett rite of passage.** `archinstall` följer med i
  installationsmediet och gör grundinstallationen till ett guidat val på tio minuter.

**På skrivbordet** väljer du själv skrivbordsmiljö och kompositor, och slipper den programvara en
distribution annars bestämt att du ska ha. Du får också de senaste grafikdrivrutinerna och den
senaste kärnan utan att vänta på nästa utgåva — vilket märks på ny hårdvara.

**På servern** är den vanliga invändningen att en rullande utgåva är olämplig. Jag håller inte med,
men förbehållet är verkligt: Arch belönar en maskin du håller ett öga på och straffar en du glömmer
bort. Uppdatera regelbundet och läs [Arch news](https://archlinux.org/news/) före en större
uppdatering, så är det ett tacksamt serversystem — minimal bas, inga tjänster du inte startat själv,
och full insyn i angreppsytan. Vill du att en maskin ska stå orörd i tre år är det här fel val, och
då ska du köra Debian.

**Vad det kostar dig:** du behöver läsa. Uppdateringar kan kräva ingripande, och den dagen något går
sönder finns ingen supportavdelning — bara wikin och forumet. Till gengäld går det sällan sönder av
sig självt, vilket är mer än man kan säga om alternativet.

> Kom ihåg: om du inte kan se källkoden, kan du inte lita på den.

---

## Windows 11 LTSC

LTSC står för *Long-Term Servicing Channel*, och det är den utgåva Microsoft gör åt bankomater,
sjukhusutrustning och industrimaskiner. Alltså åt kunder som blir förbannade när ett operativsystem
plötsligt får en chattbot. Det som gör den intressant är precis det som saknas:

- **Ingen Copilot.** Inte avstängd — inte installerad.
- **Ingen Microsoft Store**, och inga förinstallerade konsumentappar. Inga widgets, ingen Teams-knapp,
  ingen Xbox-panel, inget spel du inte bett om.
- **Inga årliga funktionsuppdateringar.** Bara säkerhetsuppdateringar. Systemet du installerar är
  systemet du har kvar om fem år.
- **Långt supportfönster.** IoT Enterprise LTSC 2024 har tio års support, alltså till 2034. Vanlig
  Enterprise LTSC 2024 har fem år.

Det är fortfarande Windows. Drivrutiner fungerar, program fungerar, spel fungerar. Skillnaden är att
det beter sig som ett verktyg istället för en plattform som försöker sälja saker till dig.

**Haken:** LTSC säljs inte i handeln. Det distribueras via volymlicensiering och OEM-kanaler, vilket
gör det avsevärt krångligare att komma över lagligt som privatperson än att klicka hem en vanlig
licens. Det är den verkliga kostnaden för den här vägen — inte pengarna, utan anskaffningen.

> Kör du redan Windows och tänker göra om datorn ändå: det här är den installation som faktiskt är
> värd besväret. Att gå från en Windows-utgåva till en annan är samma jobb oavsett vilken du väljer.

---

## Rensa upp i Windows

Kör du en vanlig Windows-installation istället för LTSC får du städa själv. På LTSC behöver du
merparten av det här betydligt mindre — det mesta finns helt enkelt inte där från början.

**Systemrengöring:**

- [BleachBit](https://www.bleachbit.org/) – öppen källkod som faktiskt tar bort skräp
- [O&O ShutUp10++](https://www.oo-software.com/en/shutup10) – inaktiverar telemetri och oönskade
  funktioner, fungerar även på Windows 11
- [Bulk Crap Uninstaller](https://www.bcuninstaller.com/) – avinstallerar ordentligt, inklusive
  rester

**Nätverksblockering:**

- [simplewall](https://github.com/henrypp/simplewall) – kontrollera Windows-brandväggen på riktigt
- [WindowsSpyBlocker](https://github.com/crazy-max/WindowsSpyBlocker) – blockera spårning
- [StevenBlack/hosts](https://github.com/StevenBlack/hosts) – omfattande hosts-fil mot spårare

**Nödvändiga verktyg:**

- [Autoruns](https://learn.microsoft.com/sysinternals/downloads/autoruns) – se vad som startar
- [Process Explorer](https://learn.microsoft.com/sysinternals/downloads/process-explorer) – se vad
  som faktiskt körs
- [WPD](https://wpd.app/) – integritetsdashboard för Windows

**Om WinUtil:** [WinUtil](https://github.com/ChrisTitusTech/winutil) samlar avbloatning,
telemetriinställningar och appinstallation i ett verktyg, och sparar timmar av manuellt arbete.
Det installeras normalt med `irm christitus.com/win | iex` — alltså genom att hämta ett skript från
internet och köra det direkt med fulla rättigheter.

Det är värt att stanna upp vid. Det är exakt det mönster resten av den här sidan säger åt dig att
vara skeptisk mot, och rådet "lita inte på standardinställningar" är svårt att förena med "kör den
här enradaren utan att titta". WinUtil är välkänt och källkoden finns öppet — men läs skriptet
först, eller hämta en release från GitHub istället. Gör undantaget medvetet, inte av bekvämlighet.

**En varning om CCleaner:** det var utmärkt tills Avast köpte det. Numera är det i praktiken
spionprogram med rengöringsfunktioner — gratisversionen släpar med oönskade program och
premiumversionen tjatar om "optimeringar" du inte behöver. Använd BleachBit istället.

Kom ihåg: på en vanlig Windows-installation kommer Microsoft att försöka återställa dina ändringar
via uppdateringar. Var vaksam. Det är också själva argumentet för LTSC — där kommer uppdateringarna
inte med nya funktioner som ska stängas av igen.

---

## Gaming

Låt oss vara ärliga – spel har andra prioriteringar än integritet, och det går inte att önska bort.

**Windows 11 LTSC är rätt svar för Windows-gaming.** Du får fullt drivrutinsstöd, DirectX 12, Steam
och alla lanserare, men slipper Game Bar, Xbox-panelen och resten av bakgrundsprocesserna. Anti-fusk
fungerar, eftersom det fortfarande är Windows.

- Logga aldrig in med ett Microsoft-konto om du kan undvika det
- Blockera allt utom det som faktiskt behöver internet
- Game Pass kräver Store, som inte finns på LTSC. Är det ett krav för dig är LTSC fel val

**Linux-gaming har blivit riktigt bra**, och Arch råkar sitta bäst till: SteamOS på Steam Deck är
Arch-baserat, vilket innebär att Valves arbete landar i samma ekosystem som du kör.

- Steam Proton hanterar den stora merparten av spelbiblioteket
- Vulkan-stödet är utmärkt
- Prestandan är i nivå med Windows, ibland bättre
- Inga bakgrundsprocesser som stjäl resurser
- [ProtonDB](https://www.protondb.com/) berättar i förväg om ett spel fungerar

**Det som fortfarande inte fungerar:** kärnbaserat anti-fusk. Vanguard, och EAC eller BattlEye i de
konfigurationer där utvecklaren inte aktiverat Linux-stöd, stänger dig ute. Spelar du konkurrensspel
med den typen av skydd är frågan avgjord åt dig — då behöver du Windows.

**Virtuella maskiner:** GPU-passthrough med QEMU/KVM ger nästan native prestanda, men kräver två
grafikkort, IOMMU-stöd och en hel del tålamod. Vanliga virtuella maskiner utan passthrough är inte
användbara för spel. Och anti-fusk upptäcker i regel att du kör i en VM och stänger av dig — räkna
med att det inte fungerar snarare än tvärtom.

**Dual boot, om du behöver båda:**

1. Använd separata SSD:er för varje system
2. Koppla från Windows-disken när du installerar Linux
3. Låt aldrig Windows-uppdateringar röra boot-loadern
4. Dela spelbiblioteket via en monterad NTFS-partition

```bash
# GRUB-konfiguration som faktiskt hittar Windows
GRUB_TIMEOUT=5
GRUB_DISABLE_OS_PROBER=false
GRUB_DISABLE_SUBMENU=y
```

**Om hårdvara:** moderna grafikkort kräver Windows 10, Windows 11 eller Linux. NVIDIA slutade släppa
drivrutiner för Windows 7 och 8.1 under 2023, långt innan dagens kort fanns — det finns alltså ingen
version av ett äldre Windows som ger dig ett modernt kort. NVIDIA har bäst stöd på Windows och
fungerar väl på Linux med de proprietära drivrutinerna; AMD är i praktiken likvärdigt på båda, med
öppna drivrutiner som ligger i kärnan.

---

## Final Thoughts

De stora teknikjättarna är inte dina vänner. Varje "hjälpsam" funktion har osynliga strängar. Ta
tillbaka kontrollen över din dator – den ska vara DITT verktyg, inte deras datainsamlingsmaskin.

Håll systemet offline medan du konfigurerar det. Lita inte på standardinställningarna. Läs det smått
tryckta. Och kom ihåg: om något är gratis, är DU produkten.

> Vill du köra AI på dina egna villkor, lokalt och utan att data lämnar maskinen, se
> [Lokal AI](/ai/localai).
