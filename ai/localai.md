# Lokal AI-körning

Att köra språkmodeller på egen hårdvara har blivit förvånansvärt enkelt. Den här sidan är den
praktiska delen — verktygen, hårdvaran och hur du kopplar ihop det med annat.

För koncepten bakom — vad parametrar och kvantisering betyder, och hur du väljer modell — se
[AI - Artificiell Intelligens](/ai).

## Innehåll

- [Varför köra lokalt?](#varför-köra-lokalt)
- [Verktygen](#verktygen)
- [Hårdvaran](#hårdvaran)
- [Kom igång](#kom-igång)
- [Använd modellen från andra program](#använd-modellen-från-andra-program)
- [Praktiska tips](#praktiska-tips)

## Varför köra lokalt?

- **Integritet** — data lämnar aldrig maskinen. Inget skickas till någon annans server.
- **Kostnad** — ingen löpande kostnad per token. Hårdvaran är engångsutgiften.
- **Tillgänglighet** — fungerar offline, och ingen tjänst kan dra tillbaka modellen du använder.
- **Kontroll** — du väljer version och uppgraderar när det passar dig, inte när leverantören vill.

Nackdelen är rak: du är begränsad av ditt eget minne, och de största modellerna får helt enkelt inte
plats. Se [minnestabellen](/ai#räkna-ut-minnesbehovet).

## Verktygen

De flesta bygger på samma motor — [llama.cpp](https://github.com/ggml-org/llama.cpp) — och samma
filformat, GGUF. Skillnaden ligger i gränssnittet.

- **[Ollama](https://ollama.com)** — kommandoradsbaserat, med REST API. Enklast att automatisera och
  det de flesta verktyg förväntar sig. Körs nativt på Windows, macOS och Linux; **inget WSL behövs**.
- **[LM Studio](https://lmstudio.ai)** — grafiskt gränssnitt för att hitta, ladda ner och chatta med
  modeller. Har en inbyggd server som kan köras headless. Bäst för att komma igång.
- **[Jan](https://jan.ai)** — öppen källkod, liknande LM Studio i upplägg. Också med
  OpenAI-kompatibel serverdel.
- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — motorn direkt, utan mellanlager. Mest
  kontroll, minst bekvämlighet.
- **[LocalAI](https://localai.io)** — OpenAI-kompatibelt API i container. Passar när du vill ersätta
  ett moln-API i en befintlig applikation utan att röra koden.

> **Vilket ska du välja?** Vill du bara testa: LM Studio. Ska något annat program prata med modellen:
> Ollama. Kör du redan allt i Docker: LocalAI.

## Hårdvaran

Minnet avgör vad du kan köra. Beräkningskraften avgör hur fort det går. Av de två är minnet nästan
alltid den bindande begränsningen.

- **NVIDIA** — bäst stöd, minst krångel. CUDA fungerar direkt i samtliga verktyg ovan. Titta på VRAM
  före allt annat; ett äldre kort med mer minne slår ofta ett nyare med mindre.
- **AMD** — fungerar bra numera. ROCm ger bäst prestanda på Linux, och verktygen faller tillbaka på
  Vulkan där ROCm inte finns. Räkna med lite mer handpåläggning än med NVIDIA.
- **Apple Silicon** — förvånansvärt stark, tack vare delat minne: GPU:n kommer åt större delen av
  systemminnet. En Mac med mycket RAM kör modeller som skulle kräva ett arbetsstationskort på PC.
- **Intel Arc** — fungerar via Vulkan och SYCL, men är minst beprövat av alternativen.
- **Endast CPU** — fullt möjligt för små modeller. Räkna med några få tokens per sekund, vilket
  duger för bakgrundsjobb men inte för chatt.

Får modellen inte plats i VRAM flyttas delar till systemminnet, och hastigheten faller kraftigt. Det
är bättre att köra en mindre modell som ryms än en större som spiller över.

## Kom igång

1. **Installera drivrutiner.** Senaste från NVIDIA eller AMD. Detta är det vanligaste skälet till att
   GPU:n inte används.
2. **Installera ett verktyg.** LM Studio om du vill ha ett gränssnitt, Ollama om du vill ha ett API.
3. **Ladda ner en modell som ryms.** Börja i storleksordningen 7–14B med Q4-kvantisering — det får
   plats på de flesta kort och är tillräckligt bra för att bedöma om det här är något för dig.
4. **Verifiera att GPU:n används.** Kolla belastningen i Aktivitetshanteraren, `nvidia-smi` eller
   motsvarande under tiden modellen svarar. Ligger GPU:n stilla medan CPU:n går varm körs modellen på
   fel hårdvara — då stämmer inte drivrutinerna eller så fick modellen inte plats.

## Använd modellen från andra program

Både Ollama och LM Studio exponerar ett OpenAI-kompatibelt REST API på localhost. Det innebär att det
mesta som kan prata med OpenAI kan prata med din lokala modell — det räcker oftast att peka om
bas-URL:en.

| Verktyg   | Standardport | Adress                    |
|-----------|--------------|---------------------------|
| Ollama    | 11434        | `http://localhost:11434`  |
| LM Studio | 1234         | `http://localhost:1234/v1`|

**I kodeditorn:**

- **[Continue](https://www.continue.dev/)** — öppen källkod, finns till VS Code och JetBrains. Kan
  peka på en lokal modell för både autocomplete och chatt.
- **[Cline](https://github.com/cline/cline)** — agentbaserat tillägg för VS Code som kan läsa och
  skriva filer och köra kommandon. Fungerar mot lokala modeller, men kräver en någorlunda kapabel
  modell för att bli användbar.

**Webbgränssnitt:**

- **[Open WebUI](https://github.com/open-webui/open-webui)** — komplett chattgränssnitt mot Ollama,
  med användarhantering och dokumentuppladdning.

> **Om lokala modeller för kodning:** de mindre modellerna är klart svagare än molntjänsterna på
> agentbaserat arbete över flera filer. Till autocomplete och avgränsade frågor duger de däremot bra,
> och då stannar koden på maskinen.

## Praktiska tips

- **Kvantisering:** börja på Q4. Går det trögt, ta en mindre modell hellre än hårdare kvantisering —
  under Q4 sjunker kvaliteten snabbt.
- **Kontextfönster:** långa kontextfönster äter minne. Sänk inställningen om du får slut på VRAM; du
  behöver sällan hela fönstret.
- **Testa på svenska.** Kvaliteten varierar mycket mer mellan modeller på svenska än på engelska, och
  ingen leaderboard mäter det åt dig.
- **Mät istället för att gissa.** Tokens per sekund och tid till första token säger mer om
  användbarheten än modellstorleken gör.
- **Isolera om det är känsligt.** Kör i container eller på ett avskilt nät om modellen ska hantera
  data som inte får läcka.
