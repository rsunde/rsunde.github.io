# AI - Artificiell Intelligens

Artificiell intelligens (AI) handlar om att skapa system som kan efterlikna och förstärka mänskliga
kognitiva processer. Den här sidan fokuserar på språkmodeller (LLM:er): hur de fungerar, vad namnen
betyder och hur du väljer rätt modell för dina behov.

> **Om sidan:** Den är medvetet skriven för att hålla över tid. Du hittar inga rankinglistor, priser
> eller versionsnummer här — sådant är inaktuellt inom några månader. För färska siffror, se
> [Var du hittar aktuell information](#var-du-hittar-aktuell-information) längst ner.

## Innehåll

- [Modeller](#modeller)
- [Modellnamn](#modellnamn)
- [Storlek, kvantisering och minne](#storlek-kvantisering-och-minne)
- [Hur du väljer modell](#hur-du-väljer-modell)
- [Lokalt eller via API](#lokalt-eller-via-api)
- [Var du hittar aktuell information](#var-du-hittar-aktuell-information)

## Modeller

Modeller är hjärtat i moderna AI-system — matematiska strukturer som tränas på data för att upptäcka
mönster och göra prediktioner. Tänk på dem som "hjärnor" som kan specialiseras för olika uppgifter.

### Grundläggande koncept

- **Arkitektur**: hur modellen är uppbyggd internt.
  - Består av lager, noder och kopplingar.
  - Olika arkitekturer passar olika användningsområden.
  - Moderna modeller kan ha miljardtals parametrar.
- **Parametrar**: de inlärda vikterna. Fler parametrar ger i regel mer kapacitet — och kräver mer
  minne. Det är den här siffran som står som "7b" eller "70b" i modellnamnet.
- **Kontextfönster**: hur mycket text modellen kan hålla i huvudet samtidigt, mätt i tokens. Avgör om
  du kan mata in ett helt dokument eller bara ett stycke.
- **Token**: den enhet modellen faktiskt läser och skriver. Ungefär motsvarande en halv till en hel
  kort ord på svenska — räkna med fler tokens per ord på svenska än på engelska.

### Typer av modeller

- **Generella modeller**
  - Kan hantera många olika uppgifter.
  - Kräver ofta mer resurser.
- **Specialiserade modeller**
  - Optimerade för specifika uppgifter, till exempel kod eller bild.
  - Ofta mindre och effektivare inom sitt område.
- **Resonerande modeller**
  - Producerar interna resonemangssteg innan svaret.
  - Bättre på matematik, logik och flerstegsproblem — men långsammare och dyrare per svar.

### Träningsprocess

- **Förträning**: modellen lär sig grundläggande språkförståelse från stora mängder ostrukturerad
  data. Det är här merparten av beräkningskostnaden ligger.
- **Finjustering**: anpassning för specifika uppgifter med mindre, specialiserad data.
- **Instruktionsjustering**: modellen lär sig följa instruktioner istället för att bara fortsätta
  text. Skillnaden mellan en *base*-modell och en *instruct*-modell.
- **Utvärdering**: tester mot standardiserade uppgifter för att mäta prestanda och kvalitet.

> **Base eller instruct?** Vill du chatta med modellen eller ge den instruktioner, välj alltid en
> `instruct`- eller `chat`-variant. En ren basmodell fortsätter bara din text och känns trasig om du
> förväntar dig ett svar.

## Modellnamn

Modellnamn ger information om familj, version, storlek och kvantisering. Exempel:

- **GenericModelV2-7b-Instruct-GGUF-Q4**
- **GenericModel-14b-CoT-FP16**

### Vad namnen betyder

1. **Modellfamilj** — `GenericModel` anger modellens namn och ursprung.
2. **Version** — `V2` visar att det är andra generationen.
3. **Parameterstorlek** — `7b` eller `14b` anger antalet parametrar i miljarder.
4. **Variant** — `Instruct`, `Chat`, `Coder`, `CoT` med flera visar vad den är anpassad för.
5. **Format** — `GGUF` är det vanligaste filformatet för lokal körning.
6. **Kvantisering** — `Q4`, `Q8`, `FP16` anger precisionen, och därmed storleken.

Namnen ser röriga ut men följer nästan alltid det här mönstret. När du kan läsa dem ser du direkt
vad en modell kräver av din hårdvara innan du laddar ner flera gigabyte.

## Storlek, kvantisering och minne

### Parameterstorlek

Antalet parametrar är den grövsta indikatorn på kapacitet. Grovt indelat:

- **1–3B** — enkla uppgifter, sammanfattningar, klassificering. Går på nästan vad som helst.
- **7–14B** — bra allround-balans. Den storlek de flesta börjar med lokalt.
- **30–70B** — märkbart bättre på resonemang och kod. Kräver rejält med minne.
- **100B+** — i praktiken molnkörning, om du inte har en serverpark.

### Kvantisering

Kvantisering minskar precisionen i varje vikt för att spara minne. Priset är en viss
kvalitetsförlust, som är förvånansvärt liten ner till Q4 och märkbar därunder.

| Precision | Byte per parameter | Kommentar                                       |
|-----------|--------------------|-------------------------------------------------|
| FP32      | 4                  | Full precision. Används sällan för inferens.    |
| FP16      | 2                  | Referenskvalitet. Standard vid träning.         |
| Q8        | ~1                 | Praktiskt taget omöjlig att skilja från FP16.   |
| Q5        | ~0,65              | Bra kompromiss om Q4 känns för tunn.            |
| Q4        | ~0,5               | Vanligaste valet lokalt. Klart bäst per gigabyte. |
| Q2/Q3     | ~0,3               | Går att köra, men kvaliteten sjunker tydligt.   |

> **Tumregel:** en större modell med hårdare kvantisering slår oftast en mindre modell med mildare.
> En 14B i Q4 är i regel bättre än en 7B i Q8 — och tar ungefär lika mycket plats.

### Räkna ut minnesbehovet

Formeln som inte blir inaktuell:

```
minne ≈ parametrar × byte per parameter × 1,2
```

Faktorn 1,2 täcker overhead. Utöver det tillkommer kontextfönstret, som växer med hur mycket text du
matar in — räkna med några hundra megabyte extra vid normal användning, och betydligt mer om du
utnyttjar hela kontextfönstret.

| Modell | Q4      | Q8      | FP16    |
|--------|---------|---------|---------|
| 3B     | ~2 GB   | ~4 GB   | ~7 GB   |
| 7B     | ~4 GB   | ~8 GB   | ~17 GB  |
| 14B    | ~8 GB   | ~17 GB  | ~34 GB  |
| 32B    | ~19 GB  | ~38 GB  | ~77 GB  |
| 70B    | ~42 GB  | ~84 GB  | ~168 GB |

Jämför med VRAM på ditt grafikkort. Får modellen inte plats hamnar delar av den i systemminnet, och
hastigheten faller dramatiskt — det är skillnaden mellan ett läsbart svarstempo och att vänta.

## Hur du väljer modell

Modellnamnen ändras varje kvartal. Kriterierna gör det inte. Gå igenom dem i den här ordningen:

1. **Vad ska den göra?** Kod, resonemang, sammanfattning, översättning och bildförståelse har olika
   vinnare. En kodspecialiserad modell på 7B slår ofta en generell på 30B — inom just kod.
2. **Hur mycket minne har du?** Se tabellen ovan. Det här sätter det hårda taket, och de flesta av de
   modeller du läser om ryms helt enkelt inte.
3. **Hur långt kontextfönster behöver du?** Ska du mata in hela dokument eller kodbaser är det ofta
   viktigare än rå modellkvalitet.
4. **Latens eller kvalitet?** En resonerande modell tänker innan den svarar — bättre resultat, men
   sekunder till minuter per svar. För autocomplete vill du ha motsatsen.
5. **Hur bra är den på svenska?** De flesta öppna modeller är tränade övervägande på engelska.
   Testa själv: kvaliteten på svenska varierar mycket mer mellan modeller än på engelska.
6. **Vilken licens?** "Öppna vikter" betyder inte alltid fri kommersiell användning. Läs licensen om
   det ska användas i jobbet.

De modellfamiljer som varit stabila över tid och är rimliga att börja söka i: **Llama**, **Qwen**,
**Gemma**, **Mistral**, **DeepSeek** och **Phi**. Vilken version som är bäst just nu ändras hela
tiden — det är därför den här sidan inte försöker svara på det.

## Lokalt eller via API

| | **Lokalt** | **Via API** |
|---|---|---|
| **Integritet** | Data lämnar aldrig maskinen | Data skickas till leverantören |
| **Kostnad** | Engångskostnad för hårdvara | Löpande, per token |
| **Kapacitet** | Begränsad av din VRAM | De största modellerna som finns |
| **Tillgänglighet** | Fungerar offline | Kräver uppkoppling |
| **Underhåll** | Du uppdaterar själv | Uppdateras åt dig — ibland utan förvarning |
| **Kom igång** | Timmar | Minuter |

De två utesluter inte varandra. En vanlig uppdelning är lokal modell för allt som rör känsliga data
eller körs i loop, och API för de svåraste frågorna där kvaliteten faktiskt avgör.

> Vill du köra lokalt, se den praktiska guiden: **[Lokal AI](/ai/localai)**.
>
> För hur AI byggs in i operativsystemen — och vad det innebär för integriteten — se
> [Operating Systems](/guides/operatingsystems).

## Var du hittar aktuell information

Den här sidan förklarar principerna. För siffror som ändras varje vecka, gå direkt till källorna:

- [LM Arena](https://lmarena.ai) — blindtest där användare röstar mellan modellsvar. Bäst mått på
  upplevd kvalitet.
- [Artificial Analysis](https://artificialanalysis.ai/models) — kvalitet, hastighet och pris i samma
  jämförelse.
- [OpenRouter Rankings](https://openrouter.ai/rankings) — vad folk faktiskt använder, i volym.
- [Ollama Library](https://ollama.com/search) — vilka modeller som går att köra lokalt idag, med
  storlekar.
- [Hugging Face](https://huggingface.co/models) — allt annat. Störst, rörigast, mest komplett.
