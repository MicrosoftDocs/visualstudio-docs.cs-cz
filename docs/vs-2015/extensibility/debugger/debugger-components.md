---
title: Komponenty ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200660"
---
# <a name="debugger-components"></a>Komponenty ladicího programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Ladicí program je implementován jako VSPackage a spravuje celou relaci ladění. Ladicí relace zahrnuje následující prvky:  
  
- **Balíček pro ladění:** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Ladicí program poskytuje stejné uživatelské rozhraní bez ohledu na to, co je právě laděno.  
  
- **Správce ladění relace (SDM):** Poskytuje konzistentní programové rozhraní k [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladicímu programu pro správu nejrůznějších ladicích modulů. Je implementována nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Správce ladění procesů (PDM):** Spravuje pro všechny spuštěné instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] seznam všech programů, které mohou být nebo právě laděny. Je implementována nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Ladicí stroj (de):** Zodpovídá za monitorování laděného programu, který komunikuje se stavem běžícího programu s modelem SDM a PDM, a spolupracuje s vyhodnocovacím filtrem výrazů a poskytovatelem symbolů, aby poskytoval analýzu stavu paměti a proměnných programu v reálném čase. Implementuje se nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pro jazyky, které podporuje) a dodavatelům třetích stran, kteří chtějí podporovat vlastní dobu běhu.  
  
- **Vyhodnocení výrazu (EE):** Poskytuje podporu pro dynamické vyhodnocení proměnných a výrazů dodaných uživatelem při zastavení programu v určitém bodě. Implementuje ho [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pro jazyky, které podporuje) a dodavatele třetích stran, kteří chtějí podporovat své vlastní jazyky.  
  
- **Zprostředkovatel symbolů (SP):** Označuje se také jako obslužná rutina symbolů, mapuje symboly ladění programu na běžící instanci programu tak, aby bylo možné poskytnout smysluplné informace (například ladění zdrojového kódu a vyhodnocení výrazu). Je implementováno nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pro symboly společného jazykového modulu runtime [CLR] a formát souboru symbolů programu databáze aplikace [PDB]) a prodejci třetích stran, kteří mají vlastní proprietární metodu ukládání ladicích informací.  
  
  Následující diagram znázorňuje vztah mezi těmito prvky ladicího programu sady Visual Studio.  
  
  ![Přehled komponent ladění](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ladění balíčku](../../extensibility/debugger/debug-package.md)  
 Popisuje balíček ladění, který běží v prostředí, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a zpracovává všechna rozhraní.  
  
 [Správce ladění procesu](../../extensibility/debugger/process-debug-manager.md)  
 Poskytuje přehled funkcí PDM, což je správce procesů, které je možné ladit.  
  
 [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)  
 Definuje SDM, který poskytuje jednotný pohled na ladicí relaci k rozhraní IDE. SDM spravuje DE.  
  
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)  
 Dokumentuje ladicí služby, které DE poskytuje.  
  
 [Provozní režimy](../../extensibility/debugger/operational-modes.md)  
 Poskytuje přehled tří režimů, ve kterých může IDE pracovat: režim návrhu, režim běhu a režim přerušení. Jsou zde také popsány mechanismy přechodu.  
  
 [Vyhodnocovač výrazů](../../extensibility/debugger/expression-evaluator.md)  
 Vysvětluje účel EE v době běhu.  
  
 [Poskytovatel symbolů](../../extensibility/debugger/symbol-provider.md)  
 Popisuje, jak, v implementaci, poskytovatel symbolů vyhodnocuje proměnné a výrazy.  
  
 [Vizualizér typů a vlastní prohlížeč](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Popisuje, co je Vizualizér typu a vlastní prohlížeč a jaká role je vyhodnocovací filtr výrazů přehráván v podpoře obou.  
  
## <a name="related-sections"></a>Související oddíly  
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)  
 Popisuje hlavní koncepty architektury ladění.  
  
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)  
 Vysvětluje, jak DE funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.  
  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)  
 Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
