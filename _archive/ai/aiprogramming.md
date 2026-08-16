# AI-Assisterad Programmering

Artificiell intelligens (AI) transformerar programmeringsvärlden genom att erbjuda kraftfulla verktyg som kan assistera utvecklare i deras dagliga arbete. Dessa verktyg, ofta kallade AI-kodassistenter, kan hjälpa till med allt från att skriva kod och generera tester till att förklara komplexa kodavsnitt och hitta buggar.

## GitHub Copilot

GitHub Copilot är en av de mest framträdande AI-kodassistenterna, utvecklad av GitHub och OpenAI. Den är djupt integrerad i populära kodeditorer som Visual Studio Code och Visual Studio, och erbjuder realtidsförslag medan du skriver kod.

### Modeller Tillgängliga i Copilot Chat (Exempel från VS Code Insiders)

Tillgängligheten och namngivningen av modeller kan variera och uppdateras frekvent av Microsoft/GitHub. Modeller som inte är direkt valbara i Copilot Chat men som är relevanta för webbutveckling från leaderboards har lagts till för jämförelse.

| WebDev Elo (LM Arena) | Modell & Modellbas                 | Assistant | Open Source Modell | Beskrivning/Styrkor                                                                                                                                                       |
| :-------------------- | :---------------------------------- | :-------- | :----------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1612 (GISSAD)         | Claude 3.7 Sonnet Thinking / Anthropic Claude 3.7 Sonnet | VSCP, VS22 |                  | I Copilot. Variant av Claude 3.7 Sonnet optimerad för mer komplexa resonemangsuppgifter. (Rank approximerad: 57:48 relativt Sonnet, dvs ca 1612 Elo [[Info](https://artificialanalysis.ai/models/comparisons/claude-3-7-sonnet-thinking-vs-claude-3-7-sonnet)])                      |
| 1420 (1)              | Gemini 2.5 Pro (Preview) / Google Gemini 2.5 Pro | VSCP, VS22 | Gemma-2.5 | I Copilot. Kapabel modell i Gemini-familjen, bra prestanda på komplexa resonemang och kod. (Kan motsvara Gemini 1.5 Pro på leaderboards)                                  |
| 1357 (2)              | Claude 3.7 Sonnet / Anthropic Claude 3.7 Sonnet | VSCP, VS22 |                  | I Copilot. Nyare version i Sonnet-familjen, förväntas ha förbättringar över 3.5, potentiellt närmare Opus i vissa avseenden.                                              |
| 1273 (3)              | Gemini-2.5-Pro-Exp-03-25 / Google   | VSCP, VS22 | Gemma-2.5 | Google. Experimentell version av Gemini 2.5 Pro.                                                                                                                          |
| 1261 (4)              | GPT-4.1 (Preview) / OpenAI GPT-4-variant | VSCP, VS22 |                  | I Copilot. Iterativ förbättring/anpassad version av GPT-4.                                                                                                                |
| 1238 (5)              | Claude 3.5 Sonnet / Anthropic Claude 3.5 Sonnet | VSCP, VS22 |                  | I Copilot. Kraftfull och snabb modell från Anthropic, balanserar prestanda och effektivitet.                                                                              |
| 1207 (6)              | DeepSeek-V3-0324 / DeepSeek         |  | DeepSeek-Coder-V3-32B | Kodspecialiserad modell från DeepSeek.                                                                                                            |
| 1199 (7)              | DeepSeek-R1 / DeepSeek              |  | DeepSeek-Coder-R1 | Kodspecialiserad modell från DeepSeek.                                                                                                            |
| 1189 (8)              | GPT-4.1-mini-2025-04-14 / OpenAI    |  |                  | Mindre variant av GPT-4.1.                                                                                                                       |
| 1187 (9)              | o3-2025-04-16 / OpenAI              |  |                  | Intern variant.                                                                                                                                   |
| 1186 (10)             | Qwen3-235B-A22B / Alibaba           |  | Qwen3-235B | Stor öppen modell från Alibaba.                                                                                                                   |
| 1145 (11)             | Gemini 2.0 Flash / Google Gemini 2.0 Flash | VSCP, VS22 | Gemma-2.0-Flash | I Copilot. Snabb och effektiv modell från Googles Gemini-familj, för uppgifter som kräver låg latens. (Kan motsvara Gemini 1.5 Flash på leaderboards)                       |
| 1136 (12)             | o3-mini-high (20250131) / OpenAI    |  |                  | Intern variant.                                                                                                                                   |
| 1133 (13)             | Claude 3.5 Haiku (20241022) / Anthropic | VSCP, VS22 |                  | Snabbaste modellen i Claude 3.5-familjen.                                                                                                                     |
| 1093 (14)             | o4-mini (Preview) / Anpassad OpenAI/Microsoft-modell | VSCP, VS22 |                  | I Copilot. Intern, ytterligare mindre modell för snabba svar; ej på publika leaderboards.                                                                                 |
| 1092 (15)             | o3-mini / Anpassad OpenAI/Microsoft-modell | VSCP, VS22 |                  | I Copilot. Intern, mindre modell för snabba interaktioner; ej på publika leaderboards.                                                                                    |
| 1089 (16)             | Gemini-2.0-Pro-Exp-02-05 / Google   | VSCP | Gemma-2.0 | Experimentell version av Gemini 2.0 Pro.                                                                                                                         |
| 1045 (17)             | o1 (Preview) / Anpassad OpenAI/Microsoft-modell | VSCP, VS22 |                  | I Copilot. Specialanpassad modell för Copilot-specifika uppgifter.                                                                                                        |
| 1042 (18)             | o1-mini (20240912) / OpenAI         |  |                  | Mindre intern variant.                                                                                                                            |
| 1039 (19)             | Gemini-2.0-Flash-001 / Google       | VSCP | Gemma-2.0-Flash | Flash-variant.                                                                                                                                                   |
| 1030 (20)             | Gemini-2.0-Flash-Thinking-01-21 / Google | VSCP | Gemma-2.0-Flash | Flash-variant.                                                                                                                                                   |
| 1015 (21)             | Llama-4-Maverick-17B-128E-Instruct / Meta |  | Llama-4 | Llama 4.                                                                                                                                                           |
| 980 (22)              | Gemini-2.0-Flash-Exp / Google       | VSCP | Gemma-2.0-Flash | Flash-variant.                                                                                                                                                   |
| 975 (23)              | Qwen2.5-Max / Alibaba               |  | Qwen2.5-72B | Stor öppen modell från Alibaba.                                                                                                                                              |
| 964 (24)              | GPT-4o / OpenAI GPT-4o              | VSCP, VS22 |                  | I Copilot. Senaste flaggskeppsmodellen från OpenAI, känd för stark resonemangsförmåga, multimodalitet och kodkvalitet.                                                    |
| 960 (25)              | DeepSeek-V3 / DeepSeek              |  | DeepSeek-Coder-V3 | Kodspecialiserad modell från DeepSeek.                                                                                                                                        |
| 902 (26)              | Qwen2.5-Coder-32B-Instruct / Alibaba |  | Qwen2.5-32B | Kodspecialiserad modell från Alibaba.                                                                                                                                        |
| 900 (27)              | Llama-4-Scout-17B-16E-Instruct / Meta |  | Llama-4 | Llama 4.                                                                                                                                                           |
| 893 (28)              | Gemini-1.5-Pro-002 / Google         | VSCP | Gemma-1.5 | Tidigare Gemini Pro.                                                                                                                                             |
| 810 (29)              | Llama-3.1-405B-Instruct / Meta      |  | Llama-3.1 | Llama 3.1.                                                                                                                                                         |


**Assistant-förkortningar:**

- VSCP = Visual Studio Code Copilot (GitHub Copilot i VS Code)
- VS22 = Visual Studio 2022 Copilot (GitHub Copilot i Visual Studio 2022)
- RIDR = JetBrains Rider AI Assistant

**Viktigt att Notera:**
*   **"Preview"**: Indikerar att modellen är under utvärdering och kan ändras eller tas bort.
*   **Modellval**: I vissa versioner av Copilot Chat kan användaren ha möjlighet att välja vilken modell som ska användas för en specifik fråga genom att använda `/` följt av modellens alias (t.ex. `/gpt-4o`).
*   **Dynamiskt Utbud**: Microsoft och GitHub uppdaterar kontinuerligt de modeller som driver Copilot för att förbättra prestanda och introducera nya funktioner. Den exakta listan och deras benämningar kan därför ändras över tid.
*   **WebDev Elo (LM Arena)**: **Denna kolumn innehåller platshållare.** Du måste själv hämta de aktuella Elo-poängen och rankinginformationen från [LMSys Chatbot Arena Leaderboard (WebDev)](https://beta.lmarena.ai/leaderboard/webdev). Exakta poäng och ranking varierar och uppdateras kontinuerligt. Vissa modeller i Copilot är anpassade eller interna och kommer inte att finnas på publika leaderboards (markerade som "Ej tillämpligt").

## Andra AI-Programmeringsverktyg
Förutom GitHub Copilot finns det ett växande ekosystem av andra AI-drivna verktyg och plugins för kodeditorer, såsom Tabnine, Codeium, och lösningar som använder lokalt körda modeller via Ollama eller LM Studio (t.ex. Continue-plugin). Dessa erbjuder varierande funktioner och kan vara anpassade för olika behov och preferenser.

## Ranking av Modeller för Webbkodsgenerering

För att få en uppfattning om hur olika AI-modeller presterar specifikt när det gäller generering av webbutvecklingskod (HTML, CSS, JavaScript), finns det plattformar som kontinuerligt utvärderar och rangordnar dem. En sådan resurs är LM Arena.

-   **Webbplats**: [LMSys Chatbot Arena Leaderboard (WebDev)](https://beta.lmarena.ai/leaderboard/webdev)
-   **Rankingdatum**: Se webbplatsen för det senast uppdaterade datumet. Observera att modellnamn kan skilja sig något mellan Copilot och leaderboarden (t.ex. "Gemini 2.0 Flash" i Copilot kan motsvara "Gemini 1.5 Flash" på leaderboarden).

Denna typ av leaderboard kan ge insikter i vilka modeller som för närvarande anses vara mest kapabla för webbutvecklingsuppgifter, baserat på specifika benchmarks och användarutvärderingar. Det är ett bra komplement till de generella modellerna som erbjuds i verktyg som Copilot, särskilt om man letar efter den absolut bästa prestandan för just webbkod.
