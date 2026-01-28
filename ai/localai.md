# Lokal AI-körning

## Innehållsförteckning
- [Lokal AI-körning](#lokal-ai-körning)
  - [Innehållsförteckning](#innehållsförteckning)
  - [Varför köra AI lokalt?](#varför-köra-ai-lokalt)
  - [Rekommenderade verktyg](#rekommenderade-verktyg)
  - [GPU Accelererad AI-Inference med Ollama](#gpu-accelererad-ai-inference-med-ollama)
  - [GPU-acceleration](#gpu-acceleration)
  - [Installationssteg för lokal AI](#installationssteg-för-lokal-ai)
  - [Ytterligare tips](#ytterligare-tips)

## Varför köra AI lokalt?
- **Integritet:** Håll data lokalt och undvik molnets spårning.
- **Prestanda:** Utnyttja din GPU (NVIDIA/AMD) fullt ut med avancerade drivrutiner.
- **Kontroll:** Full insyn och kontroll över konfiguration och drift.

## Rekommenderade verktyg
- [Jan](https://jan.ai) 
  - Användarvänligt GUI för modellhantering.
  - Inbyggd chat och API-server.
  - Fungerar på Windows, macOS och Linux.
- [LM Studio](https://lmstudio.ai) 
  - Användarvänligt GUI för modellhantering.
  - Inbyggd chat och API-server.
  - Fungerar på Windows, macOS och Linux.
- [Ollama](https://ollama.ai)
  - Kommandoradsbaserad modellhantering.
  - REST API för integration.
  - Stöder macOS, Linux och Windows (via WSL).
- [GPT4All](https://gpt4all.io)
  - Fokuserar på enkelhet.
  - Inbyggd modellnedladdning.
  - Cross-platform desktop-app (Windows, macOS, Linux).
- [LocalAI](https://localai.io)
  - API-kompatibelt med OpenAI.
  - Containeriserad lösning.
  - Stöd för många modelltyper med Docker.

## GPU Accelererad AI-Inference med Ollama
För att få ut maximal prestanda från din GPU, överväg att köra lokala AI-applikationer som Ollama, som drar nytta av GPU-acceleration. Genom att köra AI-inferens lokalt:
- Minskar du latensen genom att undvika molnet.
- Sparar du bandbredd och ökar säkerheten eftersom data förblir lokalt.
- Utnyttjar avancerade GPU-drivrutiner (från både NVIDIA och AMD) för snabbare beräkningar.

**Så här gör du:**
1. Installera uppdaterade GPU-drivrutiner från NVIDIA/AMD.
2. Ladda ner och installera Ollama (eller liknande lokal AI-plattform).
3. Konfigurera applikationen för att använda GPU-acceleration (granska konfigurationsfiler eller GUI-inställningar).
4. Testa med exempelmodeller för att säkerställa att din GPU används korrekt.

## GPU-acceleration
- Se till att installera de senaste drivrutinerna för din GPU (NVIDIA eller AMD) för att möjliggöra snabb AI-inferens.
- Konfigurera din lokala AI-applikation (t.ex. Ollama) för att utnyttja GPU:ns fulla kapacitet genom att justera konfigurationsfiler eller använda GUI-inställningar.

## Installationssteg för lokal AI
1. Uppdatera och installera GPU-drivrutiner.
2. Ladda ner den önskade lokala AI-lösningen (t.ex. Ollama eller LM Studio).
3. Följ installationsanvisningarna: konfigurera API-portar, välj önskad modell och aktivera GPU-acceleration.
4. Testa med exempelmodeller för att säkerställa att prestandan möter dina krav.

## Ytterligare tips
- **Benchmarking:** Jämför lokal AI-prestanda genom att köra benchmark-skript.
- **Optimering:** Experimentera med kvantisering och modellstorlekar för att hitta en bra balans mellan precision och hastighet.
- **Säkerhet:** Kör din lokala AI-installation i ett isolerat nätverk eller container för extra säkerhet.

---

Fortsätt att utvidga denna guide med nya erfarenheter och verktyg allteftersom tekniken utvecklas.
