---
title: Součásti ladicího programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739007"
---
# <a name="debugger-components"></a>Součásti ladicího programu
Ladicí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program je implementován jako VSPackage a spravuje celou relaci ladění. Relace ladění obsahuje následující prvky:

- **Ladicí balíček:** Ladicí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program poskytuje stejné uživatelské rozhraní bez ohledu na to, co je laděno.

- **Správce ladění relace (SDM):** Poskytuje konzistentní programové rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger pro správu různých ladicích modulů. Je implementována společností [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Správce ladění procesů (PDM):** Spravuje pro všechny spuštěné [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instance aplikace seznam všech programů, které mohou být nebo jsou laděny. Je implementována společností [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Ladicí modul (DE):** Je zodpovědný za sledování programu, který je laděn, komunikaci stavu spuštěného programu s SDM a PDM a interakci s vyhodnocenívýrazu a poskytovatele symbol poskytnout analýzu v reálném čase stavu paměti programu a proměnné. Je implementována [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pro jazyky, které podporuje) a dodavateli třetích stran, kteří chtějí podporovat vlastní běhový čas.

- **Vyhodnocení výrazu (EE):** Poskytuje podporu pro dynamické vyhodnocení proměnných a výrazů dodaných uživatelem, pokud byl program zastaven v určitém bodě. Je implementována [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pro jazyky, které podporuje) a dodavateli třetích stran, kteří chtějí podporovat své vlastní jazyky.

- **Zprostředkovatel symbolů (SP):** Také se nazývá obslužná rutina symbolu, mapuje ladicí symboly programu na spuštěnou instanci programu, aby bylo možné poskytnout smysluplné informace (například ladění na úrovni zdrojového kódu a vyhodnocení výrazu). Je implementována [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pro symboly Clr [CLR] společného jazyka a formát souboru symbolů Program DataBase [PDB] a dodavateli třetích stran, kteří mají vlastní proprietární metodu ukládání informací o ladění.

  Následující diagram znázorňuje vztah mezi těmito prvky ladicího programu sady Visual Studio.

  ![Přehled ladění součástí](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>V tomto oddílu
 [Ladicí balíček](../../extensibility/debugger/debug-package.md) Popisuje balíček ladění, který běží [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve skořápce a zpracovává všechny ui.

 [Správce ladění procesu](../../extensibility/debugger/process-debug-manager.md) Poskytuje přehled funkcí PDM, který je správcem procesů, které lze ladit.

 [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md) Definuje SDM, který poskytuje jednotné zobrazení relace ladění rozhraní IDE. SDM spravuje DE.

 [Ladicí modul](../../extensibility/debugger/debug-engine.md) Dokumentuje ladicí služby, které de poskytuje.

 [Provozní režimy](../../extensibility/debugger/operational-modes.md) Poskytuje přehled tří režimů, ve kterých může rozhraní IDE pracovat: režim návrhu, režim spuštění a režim přerušení. Jsou také diskutovány mechanismy přechodu.

 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md) Vysvětluje účel EE v době běhu.

 [Poskytovatel symbolů](../../extensibility/debugger/symbol-provider.md) Popisuje, jak při implementaci zprostředkovatel symbolu vyhodnocuje proměnné a výrazy.

 [Typ vizualizéru a vlastního prohlížeče](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Popisuje, co typ vizualizér a vlastní prohlížeč jsou a jakou roli výraz vyhodnocení hraje v podpoře obou.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní ladění architektonických konceptů.

 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak DE pracuje současně v rámci kontextu kódování kódu, dokumentace a výrazu. Popisuje pro každý ze tří kontextů umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

 [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocení výrazů.

## <a name="see-also"></a>Viz také
- [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
