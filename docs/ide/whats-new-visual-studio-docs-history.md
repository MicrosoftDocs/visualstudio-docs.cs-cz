---
title: 'Dokumentace k Visual Studiu: historie novinek '
titleSuffix: ''
description: Historie novinek v dokumentaci k sadě Visual Studio
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: b9aba6b9c4be882498535ab96020461f22722c10
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659300"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Historie novinek v dokumentaci k sadě Visual Studio

Vítejte v historii novinek v dokumentaci sady Visual Studio. Toto téma obsahuje hlavní změny v dokumentaci před září 2020 (od července 2020). Nejnovější novinky najdete v tématu [dokumentace k Visual Studiu: co je nového v dokumentaci](whats-new-visual-studio-docs.md).

## <a name="august-2020"></a>Srpen 2020
### <a name="azure"></a>Azure

**Nové články**

- [Přidání Application Insights Azure pomocí propojených služeb, které jsou připojené ke službě Visual Studio Connected Services](../azure/azure-app-insights-add-connected-service.md) pro VS 2019 16,7
- [Přidání mezipaměti Azure pro Redis pomocí připojených služeb Visual Studio Connected](../azure/azure-cache-for-redis-add-connected-service.md) Services pro VS 2019 16,7
- [Přidání Azure Cosmos DB do aplikace pomocí služeb připojených ke službě Visual Studio](../azure/azure-cosmosdb-add-connected-service.md) propojených službami pro VS 2019 16,7
- [Přidání služby Azure Signal pomocí služeb propojených s připojenými službami sady Visual Studio](../azure/azure-signalr-add-connected-service.md) pro VS 2019 16,7
- [Přidání připojení ke](../azure/azure-sql-database-add-connected-service.md) službám připojeným Azure SQL Database pro VS 2019 16,7

**Aktualizované články**

- [Přidání služby Azure Storage pomocí připojených služeb sady Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Připojené služby pro VS 2019 16,7
  - Článek připojené služby Azure Storage: aktualizace uživatelského rozhraní a typů projektů podporovány

### <a name="code-quality"></a>Kvalita kódu

**Nové články**

- [CA1310: zadejte StringComparison pro správnou správnost](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) – přidejte dokumentaci pro CA1310 a aktualizujte dokumentaci pro CA1307.
- [CA1837: místo procesu. GetCurrentProcess () použijte Environment. ProcessID. ID](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) – docs pro CA1837
- [CA1838: Vyhněte se `StringBuilder` parametrům pro volání nespravovaného volání](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) – přidání dokumentace pro CA1838
- [CA2008: Nevytvářejte úlohy bez předávání TaskScheduler](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) – přidejte dokumentaci pro CA2008
- [CA2249: Zvažte použití řetězce. obsahuje místo řetězce. IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) – docs pro CA2249
- [CA2361: Ujistěte se, že automaticky vygenerovaná třída obsahující datovou sadu. ReadXml () se nepoužívá s nedůvěryhodnými daty](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) – další pravidla DataSet/DataTable
- [CA2362: nebezpečná datová sada nebo DataTable v automaticky generovaném serializovatelným typu může být zranitelná proti útokům při vzdáleném spuštění kódu](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) – další pravidla DataSet a DataTable.
- [IL3000: Nepoužívejte přístup k cestě k souboru sestavení při publikování jako Souborová dokumentace pro přidání do jediného souboru](/dotnet/fundamentals/code-analysis/quality-rules/il3000) pro IL3000
- [IL3001: Vyhněte se přístupu k cestě k souboru sestavení při publikování jako jeden soubor](/dotnet/fundamentals/code-analysis/quality-rules/il3001) – přidání dokumentů pro IL3001

**Aktualizuj**

- [CA1002: nezveřejňujte obecné seznamy – přidání nepodporovaného](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) prostoru – oddíl rozhraní API
- [CA1046: nepřetížení operátoru rovnosti na odkazových typech](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) – přidání nenáročného – oddíl rozhraní API
- [CA1307: zadejte StringComparison pro přehlednost](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) – přidejte dokumentaci pro CA1310 a aktualizujte dokumentaci pro CA1307
- [CA1700: Nejmenujte hodnoty výčtu &#39;vyhrazené&#39;](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) -přidat nenáročné – oddíl rozhraní API.
- [CA1707: identifikátory by neměly obsahovat podtržítka](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) – přidání části s omezením – plocha rozhraní API
- [CA1822: označte členy jako statické](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) a přídávající se v sekci rozhraní API.
- [CA2351: Ujistěte se, že vstup DataSet. ReadXml () je důvěryhodný](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) – další pravidla DataSet/DataTable
- [Instalace analyzátorů třetích stran](../code-quality/install-roslyn-analyzers.md) – změna struktury a názvů pro dokumentaci k analýze kódu

### <a name="containers"></a>Containers

**Aktualizované články**

- [Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio](../containers/hosting-web-apps-in-docker.md) – aktualizace kontejnerových nástrojů pro visual Studio 16,7 publikování uživatelského rozhraní
- [Začínáme s Visual Studio Kubernetes Tools](../containers/bridge-to-kubernetes.md) – kurz pro Kubernetes: Přidání kroků pro odebrání

### <a name="deployment"></a>Nasazení

**Nové články**

- [Rozšíření projektů Instalační program pro Visual Studio a .NET core 3,1](../deployment/installer-projects-net-core.md) – vytváření nové stránky s nápovědu pro instalační projekty .net Core 3,1 – funkce

**Aktualizované články**

- [Nasazení aplikace do složky, služby IIS, Azure nebo jiných](../deployment/deploying-applications-services-and-components-resources.md) aktualizací pro nasazení v cíli
- [Nasazení v aplikaci Visual Studio](../deployment/index.yml) – aktualizace nasazení

### <a name="extensibility"></a>Rozšiřitelnost

**Aktualizované články**
- [Podtypy projektů](../extensibility/internals/project-subtypes.md) – oprava odsazení položek seznamu
- [Referenční hodnota barvy pro Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) – AB # 1759333 oprava chybějících záhlaví sloupců

### <a name="get-started"></a>Začínáme

**Aktualizované články**

- [Krok 5: nasazení aplikace ASP.NET Core do Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) – aktualizace kurzů pro nové uživatelské rozhraní připojených služeb

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Nové články**

- [Změna klíče Nápověda F1 v aplikaci Visual Studio](./not-in-toc/change-f1-help-key.md) – výchozí stránka s nápovědum pro F1
- [Nápověda pro klávesu F1 pro textový editor](./not-in-toc/default-f1-text-editor.md) – Refaktorovat výchozí stránku Nápověda F1
- [Převod `typeof` na `nameof` ](./reference/convert-typeof-to-nameof.md) převod typeof na refaktoring nameof
- [Zjednodušit výraz LINQ](./reference/simplify-linq-expression.md) – zjednodušit refaktoring výrazu LINQ

**Aktualizované články**

- [Přizpůsobení rozložení oken v aplikaci Visual Studio](./customizing-window-layouts-in-visual-studio.md) – informace o tom, jak přidat monikery svislé karty dokumentu k přizpůsobení rozložení oken
- [Jak ohlásit problém se sadou Visual Studio nebo Instalační program pro Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Přidání dalších informací do NMI
  - Redid celou sestavu problému stránky
- [Nápověda F1](./not-in-toc/default.md) – výchozí stránka s nápovědu F1
- [Automatické obnovení, prostředí, dialogové okno Možnosti](./reference/autorecover-environment-options-dialog-box.md) – přidání informací o aktualizovaných umístěních souborů automatického ukládání
- [Možnosti, textový editor, Basic (Visual Basic), pokročilá](./reference/options-text-editor-basic-visual-basic.md) základní dokumentace pro vložené parametry název parametru
- [Možnosti, textový editor, C#, pokročilá](./reference/options-text-editor-csharp-advanced.md) základní dokumentace pro názvy vložených parametrů
- [Tipy a triky pro výkon sady Visual Studio](./visual-studio-performance-tips-and-tricks.md) – přidat informace o zakázání režimu mapy a zakázat zalamování slov
- [Co je nového ve Visual studiu 2019](./whats-new-visual-studio-2019.md) – aktualizace novinky v nástroji visual Studio 2019 s 16,7 informace GA

### <a name="rtvs"></a>RTVS

**Aktualizované články**

- Práce s tabulkami opravenými [SQL Server a R](../rtvs/integrating-sql-server-with-r.md) pro zahrnutí záhlaví sloupců

## <a name="july-2020"></a>Červenec 2020
### <a name="code-quality"></a>Kvalita kódu

**Nové články**

- [CA1417: Nepoužívejte `OutAttribute` u řetězcových parametrů pro volání nespravovaného volání](/dotnet/fundamentals/code-analysis/quality-rules/ca1417) – přidání dokumentace pro CA1417
- [CA1805: neinicializujte zbytečně.](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) – Přidání dokumentů pro CA1805
- [CA1836: preferovat v počtu, pokud je k dispozici](/dotnet/fundamentals/code-analysis/quality-rules/ca1836) – přidat dokumentaci pro CA1836 (preferovat nezadatelné přes počet)
- [CA2016: předejte parametr cancellationToken do metod, které přijímají CA2016 jednoho](/dotnet/fundamentals/code-analysis/quality-rules/ca2016) dokumentu – předejte parametr cancellationToken do metod, které jednu z nich přebírají.
- [CA2350: Ujistěte se, že vstup DataTable. ReadXml () je důvěryhodný](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) – počáteční počáteční datová sada/tabulka – pravidla deserializace
- [CA2351: Ujistěte se, že vstup DataSet. ReadXml () je důvěryhodný](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) – počáteční počáteční datová sada/tabulka – pravidla deserializace
- [CA2352: nebezpečná datová sada nebo DataTable v serializovatelným typu může být zranitelná proti útokům při vzdáleném spuštění kódu](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) – počáteční sada dat/DataTable – pravidla deserializace dokumentace
- [CA2353: nezabezpečená datová sada nebo DataTable v serializovatelných typech](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) – počáteční datová sada nebo deserializace – pravidla deserializace
- [CA2354: nebezpečná datová sada nebo DataTable v deserializovaném objektovém grafu může být zranitelná proti vzdálenému spuštění kódu](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) – počáteční datová sada nebo rekonstrukce pravidel deserializace dokumentů.
- [CA2355: nezabezpečená datová sada nebo DataTable v deserializovaném objektu Graph](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) – počáteční datová sada nebo deserializace – pravidla deserializace dokumentů
- [CA2356: nezabezpečená datová sada nebo typ DataTable v objektu web deserializovatelné objekty](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) – počáteční datová sada/tabulka – pravidla deserializace dokumentů

### <a name="containers"></a>Containers

**Nové články**

- [Konfigurace místního procesu pomocí procesu Kubernetes](../containers/configure-bridge-to-kubernetes.md) -local pomocí Kubernetes: YAML Configuration
- [Použití místního procesu s Kubernetes (Preview)](../containers/bridge-to-kubernetes.md) – migrace vývojových prostorů
- [Jak funguje místní proces s Kubernetes](../containers/overview-bridge-to-kubernetes.md)
  - Místní proces pro Kubernetes: Přidání oddílu směrování
  - Migrace vývojových prostorů

### <a name="cross-platform"></a>Různé platformy

**Aktualizované články**

- [Protokol změn (Visual Studio Tools for Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) -VSTU protokolu změn do 4.7.1.0
- [Protokol změn protokolu změn (Visual Studio Tools for Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) – VSTUM protokolu změn na 2.7.1.0

### <a name="get-started"></a>Začínáme

**Nové články**

- [Kurz: rozšíří se jednoduchá aplikace konzoly C#](../get-started/csharp/tutorial-console-part-2.md) – vydaná verze – Sidewalk, první verze kurzu

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Nové články**

- [Pokyny pro komunitu pro vývojáře](./developer-community-guidelines.md) – Přidání pokynů pro DevCom
- [Dokončení technologie IntelliSense pro neimportované typy a metody rozšíření](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Instalace

**Nové články**

- [Aktualizace sady Visual Studio pomocí minimální](../install/update-minimal-layout.md) funkce pro minimální rozložení offline rozložení a dokumentu
- [Příručka pro Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) – příručka Enterprise

### <a name="javascript"></a>JavaScript

**Nové články**

- [Kompilování kódu TypeScript (Node.js)](../javascript/compile-typescript-code-npm.md) – kompilace a sestavení TypeScriptu
- [Kompilování kódu TypeScript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) – kompilace a sestavení TypeScriptu

### <a name="msbuild"></a>MSBuild

**Nové články**

- [Společná metadata položky MSBuild](../msbuild/common-msbuild-item-metadata.md) – MSBuild: přidání tabulky pro volitelná metadata s propojením a propojením
- [Filtry řešení v](../msbuild/solution-filters.md) filtrech řešení MSBuild-MSBuild

### <a name="test"></a>Test

**Nové články**

- [Ladění a analýza testů jednotek pomocí Průzkumníka testů](../test/debug-unit-tests-with-test-explorer.md) – práce s výkonem Průzkumníka testů

**Aktualizované články**

- [Konfigurace testů jednotek pomocí souboru *. runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Aktualizace pro konfiguraci testů jednotek pomocí souboru runsettings
  - Popis možnosti viny byl změněn a byl přidán příklad.