---
title: Provozní režimy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91f3339fd18db8c006855c634e011b14eecc9206
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888925"
---
# <a name="operational-modes"></a>Provozní režimy
Existují tři režimy, ve kterých integrovaného vývojového prostředí můžete pracovat, následujícím způsobem:  
  
- [Režim návrhu](#vsconoperationalmodesanchor1)  
  
- [Režim spuštění](#vsconoperationalmodesanchor2)  
  
- [Režim přerušení](#vsconoperationalmodesanchor3)  
  
  Jak vašeho vlastního ladicího stroje (DE) přechody mezi těmito režimy je rozhodnutí o implementace, která vyžaduje, abyste se seznamte s mechanismy přechodu. DE může nebo nemusí přímo implementaci těchto režimech. Tyto režimy jsou v zásadě ladění balíčku režimy přepínat na základě akce uživatele nebo událostí z DE. Přechod z režimu do režimu pozastavení běhu je třeba podporováno zastavení událostí z DE. Přechod z přerušení buď spustit nebo kroku režimu je podporováno tímto uživatelem, provádění operací, jako je například krok nebo spouštění. Další informace o DE přechody, naleznete v tématu [řízení spouštění](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Režim návrhu  
 Režim návrhu je nonrunning stav ladění sady Visual Studio během této doby můžete nastavit ladění funkcí ve vaší aplikaci.  
  
 Ladění pouze pro několik funkcí, které se používají v režimu návrhu. Vývojář se může rozhodnout nastavit zarážky nebo vytvořit výrazů. DE načtení nebo nikdy volat, dokud integrovaného vývojového prostředí je v režimu návrhu. Interakce s DE probíhá během spuštění a pozastavení režimy.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Režim spuštění  
 Režim spuštění nastane, pokud program pracuje v relaci ladění v rozhraní IDE. Aplikace bude spuštěna až do ukončení, dokud nebude dosaženo zarážky nebo dokud je vyvolána výjimka. Při spuštění aplikace k ukončení, DE přechody do režimu návrhu. Při dosažení zarážky nebo dojde k výjimce, DE přejde do režimu přerušení.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Režim přerušení  
 Při spuštění ladění programu je pozastavený, dojde k režimu pozastavení. Režim přerušení nabízí vývojářům snímek aplikace v době přerušení a umožňuje vývojářům analyzovat stav aplikace a změnit, jak bude aplikace spuštěna. Vývojář můžete zobrazit a upravovat kód, prozkoumat nebo upravovat data, restartování aplikace, ukončení nebo pokračovat v provádění ze stejného místa.  
  
 Režimu pozastavení se zadá, když je DE odešle událostí synchronní ukončení. Synchronní zastavení událostí, také tzv. události zastavení, upozornit správce ladění relace (SDM) a rozhraní IDE, který právě laděné aplikace ukončila provádění kódu. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) rozhraní jsou příklady zastavení událostí.  
  
 Ukončení události pocházejí voláním jedné z následujících metod, které ladicí program v režimu přerušení nebo spusťte režim přechodu:  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Krok režimu  
 Krok režimu nastane, pokud program kroky na další řádek kódu, nebo do, přes nebo mimo funkci. Provádí se krok voláním metody [krok](../../extensibility/debugger/reference/idebugprocess3-step.md). Tato metoda vyžaduje `DWORD`s, zadáte [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md) výčty jako vstupní parametry.  
  
 Když program úspěšně kroky na další řádek kódu nebo na funkci nebo spuštění ke kurzoru nebo nastavit zarážku, DE automaticky přejde zpět do režimu přerušení.  
  
## <a name="see-also"></a>Viz také:  
 [Řízení spouštění](../../extensibility/debugger/control-of-execution.md)