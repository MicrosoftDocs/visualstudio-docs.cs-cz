---
title: Komponenty ladicího programu | Microsoft Docs
description: Seznamte se s prvky, které tvoří relaci ladění, kterou spravuje ladicí program sady Visual Studio, implementovaný jako VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c246bc00ee4f6fcead8404b3174da39f7b5ca2d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903980"
---
# <a name="debugger-components"></a>Komponenty ladicího programu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ladicí program je implementován jako VSPackage a spravuje celou relaci ladění. Ladicí relace zahrnuje následující prvky:

- **Balíček pro ladění:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ladicí program poskytuje stejné uživatelské rozhraní bez ohledu na to, co je právě laděno.

- **Správce ladění relace (SDM):** Poskytuje konzistentní programové rozhraní k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicímu programu pro správu nejrůznějších ladicích modulů. Je implementována nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Správce ladění procesů (PDM):** Spravuje pro všechny spuštěné instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seznam všech programů, které mohou být nebo právě laděny. Je implementována nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Ladicí stroj (de):** Zodpovídá za monitorování laděného programu, který komunikuje se stavem běžícího programu s modelem SDM a PDM, a spolupracuje s vyhodnocovacím filtrem výrazů a poskytovatelem symbolů, aby poskytoval analýzu stavu paměti a proměnných programu v reálném čase. Implementuje se nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pro jazyky, které podporuje) a dodavatelům třetích stran, kteří chtějí podporovat vlastní dobu běhu.

- **Vyhodnocení výrazu (EE):** Poskytuje podporu pro dynamické vyhodnocení proměnných a výrazů dodaných uživatelem při zastavení programu v určitém bodě. Implementuje ho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pro jazyky, které podporuje) a dodavatele třetích stran, kteří chtějí podporovat své vlastní jazyky.

- **Zprostředkovatel symbolů (SP):** Označuje se také jako obslužná rutina symbolů, mapuje symboly ladění programu na běžící instanci programu tak, aby bylo možné poskytnout smysluplné informace (například ladění zdrojového kódu a vyhodnocení výrazu). Je implementováno nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pro symboly společného jazykového modulu runtime [CLR] a formát souboru symbolů programu databáze aplikace [PDB]) a prodejci třetích stran, kteří mají vlastní proprietární metodu ukládání ladicích informací.

  Následující diagram znázorňuje vztah mezi těmito prvky ladicího programu sady Visual Studio.

  ![Přehled komponent ladění](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>V této části
 [Ladit balíček](../../extensibility/debugger/debug-package.md) Popisuje balíček ladění, který běží v prostředí, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a zpracovává všechna rozhraní.

 [Správce ladění procesů](../../extensibility/debugger/process-debug-manager.md) Poskytuje přehled funkcí PDM, což je správce procesů, které je možné ladit.

 [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md) Definuje SDM, který poskytuje jednotný pohled na ladicí relaci k rozhraní IDE. SDM spravuje DE.

 [Ladicí stroj](../../extensibility/debugger/debug-engine.md) Dokumentuje ladicí služby, které DE poskytuje.

 [Provozní režimy](../../extensibility/debugger/operational-modes.md) Poskytuje přehled tří režimů, ve kterých může IDE pracovat: režim návrhu, režim běhu a režim přerušení. Jsou zde také popsány mechanismy přechodu.

 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md) Vysvětluje účel EE v době běhu.

 [Zprostředkovatel symbolů](../../extensibility/debugger/symbol-provider.md) Popisuje, jak, v implementaci, poskytovatel symbolů vyhodnocuje proměnné a výrazy.

 [Vizualizér typů a vlastní prohlížeč](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Popisuje, co je Vizualizér typu a vlastní prohlížeč a jaká role je vyhodnocovací filtr výrazů přehráván v podpoře obou.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní koncepty architektury ladění.

 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak DE funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.

## <a name="see-also"></a>Viz také
- [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
