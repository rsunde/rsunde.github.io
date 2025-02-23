# AI - Artificiell Intelligens

Artificiell intelligens (AI) handlar om att skapa system som kan efterlikna och förstärka mänskliga kognitiva processer. Detta dokument fokuserar på språkmodeller (LLMs) och hur du kan använda dem både online och lokalt.

## Innehållsförteckning
- [AI - Artificiell Intelligens](#ai---artificiell-intelligens)
  - [Innehållsförteckning](#innehållsförteckning)
  - [Modeller](#modeller)
    - [Grundläggande Koncept](#grundläggande-koncept)
    - [Typer av Modeller](#typer-av-modeller)
    - [Träningsprocess](#träningsprocess)
  - [Modellnamn](#modellnamn)
    - [Vad namnen betyder](#vad-namnen-betyder)
  - [Översikt för Modellstorlekar, Kvantisering och Utrymme](#översikt-för-modellstorlekar-kvantisering-och-utrymme)
    - [Modellstorlekar](#modellstorlekar)
    - [Kvantisering](#kvantisering)
    - [Disk och minneskrav](#disk-och-minneskrav)
  - [Kombinationer – För- och Nackdelar](#kombinationer--för--och-nackdelar)
    - [Liten Modell: 350M med Q4](#liten-modell-350m-med-q4)
    - [Medelmodell: 7B med Q8](#medelmodell-7b-med-q8)
    - [Stor Modell: 175B med FP32](#stor-modell-175b-med-fp32)
    - [Jämför modeller online - rankings](#jämför-modeller-online---rankings)
    - [Basmodeller för Hemmasnickare](#basmodeller-för-hemmasnickare)
      - [Populära Plattformar](#populära-plattformar)
      - [Fördelar med Open Source Modeller](#fördelar-med-open-source-modeller)
      - [Populära Startmodeller](#populära-startmodeller)
    - [Modeller (basmodeller)](#modeller-basmodeller)
    - [Ytterligare modeller och dess varianter](#ytterligare-modeller-och-dess-varianter)
  - [Användning - Online och Lokalt](#användning---online-och-lokalt)
    - [Online](#online)
    - [Lokalt](#lokalt)
  - [Användning i Arbetssyfte](#användning-i-arbetssyfte)
    - [Verktyg](#verktyg)
      - [Copilot (GitHub Copilot)](#copilot-github-copilot)
      - [Andra AI Plugins i Kodeditorer](#andra-ai-plugins-i-kodeditorer)
      - [Sammanfattning](#sammanfattning)

## Modeller

Modeller är hjärtat i moderna AI-system - de är matematiska eller datorbaserade strukturer som tränas på data för att upptäcka mönster och göra prediktioner. Tänk på dem som "hjärnor" som kan specialiseras för olika uppgifter:

> **Tips**: När du väljer en modell, börja med att identifiera dina behov (textgenerering, kod, chat) och tillgängliga resurser (minne, processorkraft).

### Grundläggande Koncept
- **Arkitektur**: Hur modellen är uppbyggd internt
  - Består av lager, noder och kopplingar
  - Olika arkitekturer passar olika användningsområden
  - Moderna modeller kan ha miljardtals parametrar

### Typer av Modeller
- **Generella Modeller**: 
  - Kan hantera många olika uppgifter
  - Kräver ofta mer resurser
  - Exempel: GPT-familjen, BERT
  
- **Specialiserade Modeller**:
  - Optimerade för specifika uppgifter
  - Ofta mindre och effektivare
  - Exempel: Kodmodeller, bildmodeller

### Träningsprocess
- **Förträning**: 
  - Modellen lär sig grundläggande förståelse
  - Tränas på stora mängder ostrukturerad data
  
- **Finjustering**:
  - Anpassning för specifika uppgifter
  - Använder mindre, specialiserad data
  
- **Utvärdering**:
  - Tester mot standardiserade uppgifter
  - Mätning av prestanda och kvalitet

## Modellnamn

Modellnamn ger information om arkitektur, version, storlek och kvantisering. Exempel:

- **GenericModelV2-7b-MGRPO-GGUF-Q4**
- **GenericModel-14b-CoT-FP32**

### Vad namnen betyder

1. **Modellfamilj**: "GenericModel" anger modellens namn.
2. **Version**: "V2" visar att det är version 2.
3. **Parameterstorlek**: "7b" eller "14b" anger antalet parametrar i miljarder.
4. **Specialfunktioner**: "MGRPO" eller "CoT" visar unika egenskaper.
5. **Kvantisering**: Indikeras med "Q4", "Q8", "F16", "FP32" för precisionen.

Dessa namn hjälper användaren att snabbt se modellens egenskaper och göra rätt val för sina behov.

> **Observera**: Modellnamn kan verka komplexa men följer oftast ett logiskt mönster som hjälper dig förstå modellens kapacitet och resurskrav.

## Översikt för Modellstorlekar, Kvantisering och Utrymme

### Modellstorlekar
- **350M**: Liten modell – passar enkla uppgifter.
- **7B**: Medelmodell – bra balans mellan prestanda och resurser.
- **175B**: Stor modell – hög kapacitet, men kräver mycket resurser.

### Kvantisering
- **Q4**: Låg precision, mycket liten filstorlek.
- **Q8**: Medelprecision, lagom stor fil.
- **FP32**: Hög precision, större filstorlek.

### Disk och minneskrav
Modellens filstorlek och minneskrav beror på vald parameterstorlek och kvantisering; hög precision och fler parametrar kräver mer utrymme.

> **Viktigt**: Kvantisering är ett sätt att minska modellens storlek med viss precisionsförlust. Välj nivå baserat på dina behov av precision vs. resurskrav.

## Kombinationer – För- och Nackdelar

### Liten Modell: 350M med Q4
- **Fördelar:** Mycket låg lagrings- och minnesanvändning. Passar realtidsapplikationer.
- **Nackdelar:** Lägre precision – kanske inte för komplexa uppgifter.

### Medelmodell: 7B med Q8
- **Fördelar:** Bra balans mellan prestanda och resursanvändning.
- **Nackdelar:** Kompromiss mellan hastighet och precision.

### Stor Modell: 175B med FP32
- **Fördelar:** Hög noggrannhet och kapacitet.
- **Nackdelar:** Höga krav på minne och disk, och ofta långsammare.

> **Praktiskt exempel**: En 7B-modell med Q8 kvantisering är ofta en bra startpunkt för lokala experiment, då den balanserar prestanda och resurskrav.

### Jämför modeller online - rankings
- [Artificial Analysis](https://artificialanalysis.ai) – Övergripande analys.
- [Modellöversikt](https://artificialanalysis.ai/models) – Detaljerad modellinformation.
- [YourGPT AI](https://yourgpt.ai/tools/llm-comparison-and-leaderboard) – Jämförelse och leaderboard.
- [OpenRouter Rankings](https://openrouter.ai/rankings) – Prestandaöversikt.
- [LM Arena](https://lmarena.ai) – Arena för LLM-jämförelse.

### Basmodeller för Hemmasnickare
Det finns flera platser där man kan hitta och experimentera med AI-modeller:

#### Populära Plattformar
- [**Ollama**](https://ollama.com/search): Enkelt gränssnitt för att köra modeller lokalt
  - Snabb installation och användning
  - Bred samling av optimerade modeller
  - Perfekt för nybörjare och experiment

- [**Hugging Face**](https://huggingface.co): Den största plattformen för AI-modeller
  - Omfattande modelldatabas
  - Detaljerad dokumentation
  - Aktiv community och forskning
  - Möjlighet att träna egna modeller

#### Fördelar med Open Source Modeller
- **Transparens**: Öppen källkod möjliggör granskning
- **Anpassningsbarhet**: Kan modifieras för specifika behov
- **Kostnadsfritt**: Inga licensavgifter
- **Community-stöd**: Aktiv utveckling och förbättring
- **Lokal körning**: Full kontroll över data och prestanda

#### Populära Startmodeller
- **För Textgenerering**: Llama, Mistral
- **För Kodning**: StarCoder, CodeLlama
- **För Översättning**: NLLB, M2M-100
- **För Chatbot**: Vicuna, OpenHermes
- **För Lätt Användning**: Phi-2, TinyLlama

### Modeller (basmodeller)
- Llama (t.ex. Llama 3.x) – Populär för sin flexibilitet och stora community.
- Qwen – Känd för snabbhet och effektivitet.
- Phi – Används för sin enkelhet och låga resurskrav.
- Deepseek – Erbjuder robust prestanda.
- Gemma – Känd för sin snabba inferens och effektivitet.
- ...och flera andra open source-modeller.

### Ytterligare modeller och dess varianter
- **deepscaler** – En finjusterad version av Deepseek-R1-Distilled-Qwen-1.5B som överträffar prestandan hos OpenAI:s o1-preview med bara 1.5B parametrar på populära matematikutvärderingar.
- **deepseek-r1** – DeepSeeks första generation av resonemangsmodeller med jämförbar prestanda mot OpenAI-o1, inklusive sex täta modeller destillerade från DeepSeek-R1 baserade på Llama och Qwen.
- **command-r7b** – Den minsta modellen i Cohere:s R-serie som levererar topphastighet, effektivitet och kvalitet för AI-applikationer på vanliga GPU:er och edge-enheter.
- **deepseek-v3** – En stark Mixture-of-Experts (MoE) språkmodell med totalt 671B parametrar, med 37B aktiverade för varje token.
- **phi4** – En 14B parametrars, state-of-the-art öppen modell från Microsoft.
- **llama3.3** – En ny state-of-the-art 70B-modell som erbjuder prestanda liknande Llama 3.1 405B.
- **llama3.2-vision** – Instruktionsanpassade modeller för bildresonemang, tillgängliga i storlekarna 11B och 90B.
- **llama3.2** – Metas Llama 3.2 som erbjuder mindre varianter med 1B och 3B parametrar.
- **qwen2.5-coder** – Kodspecificerade Qwen-modeller med betydande förbättringar inom kodgenerering, kodresonemang och kodkorrigering.
- **qwen2.5** – Qwen2.5-modeller förtränade på Alibabas senaste stora dataset, med stöd upp till 128K tokens och flerspråkigt stöd.

## Användning - Online och Lokalt

### Online
Populära tjänster (Gratis med begränsningar):
1. [ChatGPT](https://chat.openai.com) (Plus: $20/månad, Team: $30/användare/månad)
1. [Microsoft CoPilot](https://copilot.cloud.microsoft/) (Pro: $30/månad)
1. [Google Gemini](https://gemini.google.com/app) (Advanced: $10/månad)
1. [Anthropic Claude](https://claude.ai/) (Pro: $20/månad)
1. [X Grok](https://grok.com/) (Premium X: $16/månad)
1. [Meta AI](https://meta.ai/llama) (Gratis)
- [Hugging Face](https://huggingface.co) - Öppen plattform för AI och maskininlärning (Pro: från $9/månad).
- [Replicate](https://replicate.com) - Plattform för att köra AI-modeller i molnet (Pay-per-use).

> **Kom ihåg**: Online-tjänster är enklast att komma igång med, medan lokala installationer ger mer kontroll och integritet.

### Lokalt
För att köra AI-modeller lokalt och få ut maximal prestanda, se vår dedikerade guide: [Lokal AI](/localai).

> För dig som även vill förstå hur säkerhet och AI integreras i operativsystem, kika i [Operating Systems](/operatingsystems).

## Användning i Arbetssyfte

- Effektivisering av arbetsflöden genom automatisering.
- Analys och visualisering av stora datamängder.
- Förbättrad beslutsfattande med hjälp av prediktiva modeller.

> **Pro-tips för AI-användning**
> 
> För enklaste vägen in, börja med någon av onlinestjänsterna direkt i webbläsaren - det kräver minimal setup och ger snabba resultat, med det kräver mycket copy/paste. Om du behöver mer kontroll eller vill experimentera, testa lokala modeller via Ollama eller LM Studio.
>
> När du jobbar med källkod, använd gärna plugins direkt i din IDE. Kom ihåg att inkludera relevant kontext när du ställer frågor, och spara dina bästa prompts för återanvändning. För dokumentation, låt AI:n hjälpa till att expandera dina utkast men behåll din personliga stil.
>
> Det viktigaste är att börja enkelt och utöka användningen i din egen takt - AI är ett verktyg som ska underlätta ditt arbete, inte komplicera det.

### Verktyg

- Visual Studio Code: Editor med stöd för AI, Copilot och olika plugins.
  - [Copilot](https://copilot.cloud.microsoft/) erbjuder följande modeller (2025 Mars):
    - Claude 3.5 Sonnet (Preview)
    - Gemini 2.0 Flash (Preview)
    - GPT 4o
    - o1 (Preview)
    - o3-mini (Preview)
  - [Cline](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) Autonomous coding agent right in your IDE, capable of creating/editing files, running commands, using the browser, and more with your permission every step of the way.
  - [Ollama Script Code](https://marketplace.visualstudio.com/items?itemName=OllamaScriptCode.ollama-script-code) Ollama Script Code provides autocompletion and chat for code using the Ollama models.
  - [Continue](https://marketplace.visualstudio.com/items?itemName=Continue.continue) The leading open-source AI code assistant
- Visual Studio 2022: Editor med stöd för AI (Copilot).
  - [Copilot](https://copilot.cloud.microsoft/) erbjuder följande modeller (2025 Mars):
    - GPT 4o
    - o1 (Preview)
    - o3-mini (Preview)
    - Claude 3.5 Sonnet (Preview)
  - [LLMCopilot2022](https://marketplace.visualstudio.com/items?itemName=foyoung365.LLMCopilot2022) Code using Ollama models
  - [EntwineLLM](https://marketplace.visualstudio.com/items?itemName=EmilianoMusso.EntwineLLM) LLM coding assistant (code writing and review, refactor, unit tests generation, documentation)
- LM Studio
  - Användarvänligt gränssnitt för att:
    - Hitta och ladda ner modeller
    - Chatta med modeller direkt i programmet
    - Hantera flera modeller samtidigt
  - Inkluderar serverkomponent som:
    - Kör modeller separat från användargränssnittet
    - Stödjer API-anrop från externa applikationer
    - Kan köras headless för serverinstallationer

- Ollama
  - Fokuserad serverkomponent som:
    - Erbjuder robust API för modellhantering
    - Stödjer många olika modellformat
    - Enkel kommandoradshantering
  - Populära webb-baserade gränssnitt:
    - [OpenWebUI](https://github.com/open-webui/open-webui)
    - [Amica](https://github.com/semperai/amica)

- LM Studio / Ollama - Serverintegration
  - Gemensamma egenskaper:
    - REST API på localhost (standard)
    - Konfigurerbar port (LM Studio: 1234, Ollama: 11434)
    - Kompatibla med de flesta IDE-plugins
    - Stöd för olika modellformat (GGUF, GGML)

#### Copilot (GitHub Copilot)
GitHub Copilot är en **AI-assistent** som är djupt integrerad i kodeditorer som **Visual Studio Code** och **Visual Studio** och sätter ett tydligt exempel för hur en sådan integration bör fungera.  

#### Andra AI Plugins i Kodeditorer
Utöver Copilot finns det flera andra AI-baserade plugins som hjälper utvecklare att skriva kod mer effektivt och på ett mer intelligent sätt, dessa har oftast inte lika bra integration som Copilot, en fördel de har är att de kan nyttja lokala modeller från Ollama eller LM Studio.

#### Sammanfattning
AI-baserade plugins för kodeditorer är en kraftfull hjälp för att skriva kod snabbare och mer effektivt. Även om dessa verktyg har många fördelar, som snabbare kodning och realtidsförslag, måste utvecklare vara medvetna om att AI:n inte alltid är perfekt och att de bör granska förslagen noggrant.