---
title: Provozní režimy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4009ab6268140117c8fd1294adcc52ac347b799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153721"
---
# <a name="operational-modes"></a>Provozní režimy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Existují tři režimy, ve kterých může IDE pracovat, následovně:  
  
- [Režim návrhu](#vsconoperationalmodesanchor1)  
  
- [Režim spuštění](#vsconoperationalmodesanchor2)  
  
- [Režim přerušení](#vsconoperationalmodesanchor3)  
  
  Způsob, jakým vaše vlastní moduly ladění (DE) mění mezi těmito režimy, je rozhodnutí o implementaci, které vyžaduje, abyste se seznámili s mechanismy přechodu. DE květen nebo nemusí přímo implementovat tyto režimy. Tyto režimy jsou opravdu ladit režimy balíčku, které se přepínají na základě akce uživatele nebo událostí z DE. Například přechod z režimu spuštění do režimu přerušení je podněcována událostí zastavení z DE. Přechod z přerušení na režim spuštění nebo krok je nápomocen uživatel, který provádí operace, jako je krok nebo provedení. Další informace o zrušení přechodů naleznete v tématu [řízení provádění](../../extensibility/debugger/control-of-execution.md).  
  
## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Režim návrhu  
 Režim návrhu je nespuštěný stav ladění sady Visual Studio, během kterého lze v aplikaci nastavit funkce ladění.  
  
 V režimu návrhu se používá jenom několik funkcí ladění. Vývojář se může rozhodnout pro nastavování zarážek nebo vytváření výrazů kukátka. DE není nikdy načtena nebo volána, když je IDE v režimu návrhu. Interakce s nástrojem DE probíhá pouze v režimu spuštění a přerušení.  
  
## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Režim spuštění  
 Režim spuštění nastane, když se program spustí v ladicí relaci v integrovaném vývojovém prostředí. Aplikace se spustí do ukončení, dokud není dosaženo zarážky nebo dokud není vyvolána výjimka. Když aplikace běží na ukončení, DE přejde do režimu návrhu. Když je dosaženo zarážky nebo je vyvolána výjimka, příkaz DE přejde do režimu přerušení.  
  
## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Režim přerušení  
 Režim přerušení nastane, pokud je spuštění ladicího programu pozastaveno. Režim přerušení nabízí vývojářům snímek aplikace v době přerušení a umožňuje vývojářům analyzovat stav aplikace a změnit způsob, jakým se aplikace spustí. Vývojář může zobrazit a upravit kód, kontrolovat nebo upravovat data, restartovat aplikaci, ukončit provádění nebo pokračovat v provádění ze stejného bodu.  
  
 Režim přerušení je zadán, když DE odešle synchronní událost zastavení. Synchronní zastavení událostí, označovaných také jako zastavování událostí, upozorní správce ladění relace (SDM) a rozhraní IDE, které aplikace Laděna, zastavila provádění kódu. Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady událostí zastavení.  
  
 Zastavení událostí pokračuje voláním jedné z následujících metod, které převedou ladicí program z režimu přerušení na spuštění nebo krokový režim:  
  
- [Spuštění](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
- [Pokračovat](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Režim kroku  
 Krokový režim nastane, pokud program provede kroky na další řádek kódu, nebo do, nad nebo mimo funkci. Krok je proveden voláním [kroku](../../extensibility/debugger/reference/idebugprocess3-step.md)metody. Tato metoda vyžaduje `DWORD` s, aby jako vstupní parametry určovala výčty [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md) .  
  
 Když se program úspěšně doplní na další řádek kódu nebo do funkce nebo se spustí na kurzor nebo na nastavenou zarážku, příkaz DE automaticky přejde zpět do režimu přerušení.  
  
## <a name="see-also"></a>Viz také  
 [Řízení spouštění](../../extensibility/debugger/control-of-execution.md)
