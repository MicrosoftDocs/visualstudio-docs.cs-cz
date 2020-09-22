---
title: 'Dokumentace k Visual Studiu: co je nového pro srpen 2020 '
titleSuffix: ''
description: Novinky v dokumentaci sady Visual Studio pro srpen 2020.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808978"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Dokumentace k Visual Studiu: co je nového pro srpen 2020

Vítá vás novinky v dokumentaci sady Visual Studio pro srpen 2020. V tomto článku jsou uvedené některé hlavní změny v dokumentaci v průběhu tohoto období. Informace o tom, co bylo v předchozích měsících nového, najdete v tématu [co je nového v historii](whats-new-visual-studio-docs-history.md) .

## <a name="azure"></a>Azure

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

## <a name="code-quality"></a>Kvalita kódu

**Nové články**

- [CA1310: zadejte StringComparison pro správnou správnost](../code-quality/ca1310.md) – přidejte dokumentaci pro CA1310 a aktualizujte dokumentaci pro CA1307.
- [CA1837: místo procesu. GetCurrentProcess () použijte Environment. ProcessID. ID](../code-quality/ca1837.md) – docs pro CA1837
- [CA1838: Vyhněte se `StringBuilder` parametrům pro volání nespravovaného volání](../code-quality/ca1838.md) – přidání dokumentace pro CA1838
- [CA2008: Nevytvářejte úlohy bez předávání TaskScheduler](../code-quality/ca2008.md) – přidejte dokumentaci pro CA2008
- [CA2249: Zvažte použití řetězce. obsahuje místo řetězce. IndexOf](../code-quality/ca2249.md) – docs pro CA2249
- [CA2361: Ujistěte se, že automaticky vygenerovaná třída obsahující datovou sadu. ReadXml () se nepoužívá s nedůvěryhodnými daty](../code-quality/ca2361.md) – další pravidla DataSet/DataTable
- [CA2362: nebezpečná datová sada nebo DataTable v automaticky generovaném serializovatelným typu může být zranitelná proti útokům při vzdáleném spuštění kódu](../code-quality/ca2362.md) – další pravidla DataSet a DataTable.
- [IL3000: Nepoužívejte přístup k cestě k souboru sestavení při publikování jako Souborová dokumentace pro přidání do jediného souboru](../code-quality/il3000.md) pro IL3000
- [IL3001: Vyhněte se přístupu k cestě k souboru sestavení při publikování jako jeden soubor](../code-quality/il3001.md) – přidání dokumentů pro IL3001

**Aktualizuj**

- [CA1002: nezveřejňujte obecné seznamy – přidání nepodporovaného](../code-quality/ca1002.md) prostoru – oddíl rozhraní API
- [CA1046: nepřetížení operátoru rovnosti na odkazových typech](../code-quality/ca1046.md) – přidání nenáročného – oddíl rozhraní API
- [CA1307: zadejte StringComparison pro přehlednost](../code-quality/ca1307.md) – přidejte dokumentaci pro CA1310 a aktualizujte dokumentaci pro CA1307
- [CA1700: Nejmenujte hodnoty výčtu &#39;vyhrazené&#39;](../code-quality/ca1700.md) -přidat nenáročné – oddíl rozhraní API.
- [CA1707: identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707.md) – přidání části s omezením – plocha rozhraní API
- [CA1822: označte členy jako statické](../code-quality/ca1822.md) a přídávající se v sekci rozhraní API.
- [CA2351: Ujistěte se, že vstup DataSet. ReadXml () je důvěryhodný](../code-quality/ca2351.md) – další pravidla DataSet/DataTable
- [Instalace analyzátorů třetích stran](../code-quality/install-roslyn-analyzers.md) – změna struktury a názvů pro dokumentaci k analýze kódu

## <a name="containers"></a>Kontejnery

**Aktualizované články**

- [Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio](../containers/hosting-web-apps-in-docker.md) – aktualizace kontejnerových nástrojů pro visual Studio 16,7 publikování uživatelského rozhraní
- [Začínáme s Visual Studio Kubernetes Tools](../containers/tutorial-kubernetes-tools.md) – kurz pro Kubernetes: Přidání kroků pro odebrání

## <a name="deployment"></a>Nasazení

**Nové články**

- [Rozšíření projektů Instalační program pro Visual Studio a .NET core 3,1](../deployment/installer-projects-net-core.md) – vytváření nové stránky s nápovědu pro instalační projekty .net Core 3,1 – funkce

**Aktualizované články**

- [Nasazení aplikace do složky, služby IIS, Azure nebo jiných](../deployment/deploying-applications-services-and-components-resources.md) aktualizací pro nasazení v cíli
- [Nasazení v aplikaci Visual Studio](../deployment/index.yml) – aktualizace nasazení

## <a name="extensibility"></a>Rozšiřitelnost

**Aktualizované články**
- [Podtypy projektů](../extensibility/internals/project-subtypes.md) – oprava odsazení položek seznamu
- [Referenční hodnota barvy pro Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) – AB # 1759333 oprava chybějících záhlaví sloupců

## <a name="get-started"></a>Začínáme

**Aktualizované články**

- [Krok 5: nasazení aplikace ASP.NET Core do Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) – aktualizace kurzů pro nové uživatelské rozhraní připojených služeb

## <a name="ide"></a>IDE – integrované vývojové prostředí

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

## <a name="rtvs"></a>RTVS

**Aktualizované články**

- Práce s tabulkami opravenými [SQL Server a R](../rtvs/integrating-sql-server-with-r.md) pro zahrnutí záhlaví sloupců

## <a name="community-contributors"></a>Přispěvatelé komunity

Následující lidé přispěli během této doby do dokumentace sady Visual Studio. Děkujeme! Naučte se přispívat do dokumentů sady Visual Studio podle pokynů v příručce pro [přispěvatele](/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) -Alex Black (11)
- [Youssef1313](https://github.com/Youssef1313) -Youssef vítěz (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) -Qian lu (čokoláda) (1)
- [athyunnath](https://github.com/athyunnath) -athyunnath Eleti (1)
- [Caro-Oviedo](https://github.com/caro-oviedo) -Caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink) -Amaury levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) -Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89) -Robert de St Paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) -Timo Cornelius Metzger (1)
- [Weitzhandler](https://github.com/weitzhandler) -shimmy (1)