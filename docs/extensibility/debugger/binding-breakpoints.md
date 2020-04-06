---
title: Závazná zarážky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739233"
---
# <a name="bind-breakpoints"></a>Zarážky vazby
Pokud uživatel nastaví zarážku, například stisknutím klávesy **F9**, ide zformuluje požadavek a vyzve relaci ladění k vytvoření zarážky.

## <a name="set-a-breakpoint"></a>Nastavení zarážky
 Nastavení zarážky je dvoustupňový proces, protože kód nebo data ovlivněná zarážkou ještě nemusí být k dispozici. Nejprve musí být popsána zarážka a poté, jakmile bude kód nebo data k dispozici, musí být vázána na tento kód nebo data takto:

1. Zarážka je požadována z příslušných ladicích modulů (DEs) a pak je zarážka vázána na kód nebo data, jakmile bude k dispozici.

2. Požadavek na zarážku je odeslán do relace ladění, která jej odešle všem příslušným dees. Všechny DE, který se rozhodne zpracovat zarážku vytvoří odpovídající čekající zarážka.

3. Relace ladění shromažďuje čekající zarážky a odešle je zpět do balíčku ladění (ladicí součást sady Visual Studio).

4. Ladicí balíček vyzve relaci ladění k vytvoření vazby čekající zarážky na kód nebo data. Relace ladění odešle tento požadavek všem příslušným des.

5. Pokud DE je schopen svázat zarážku, odešle událost vázanou na zarážku zpět do relace ladění. Pokud ne, odešle místo toho událost chyby zarážky.

## <a name="pending-breakpoints"></a>Čekající zarážky
 Čekající zarážka může vázat na více umístění kódu. Například řádek zdrojového kódu pro šablonu Jazyka C++ může být vytvořen na každou sekvenci kódu generovanou ze šablony. Relace ladění můžete použít událost vázanou na zarazán k výčet kontextu kódu vázané na zarážku v době, kdy byla událost odeslána. Další kontexty kódu mohou být vázány později, takže DE může odeslat více událostí vázaných na zarážky pro každý požadavek na vazby. De by však měla odeslat pouze jednu událost chyby zarážky na požadavek na vazby.

## <a name="implementation"></a>Implementace
 Programově ladicí balíček volá správce ladění relace (SDM) a poskytuje rozhraní [IDebugBreakpointRequest2,](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) které zabalí [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) strukturu, která popisuje zarážku, která má být nastavena. Přestože zarážky mohou být z mnoha forem, nakonec vyřešit do kontextu kódu nebo dat.

 SDM předá toto volání každé příslušné DE voláním jeho [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metoda. Pokud DE se rozhodne zpracovat zarážku, vytvoří a vrátí rozhraní [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) SDM shromažďuje tato rozhraní a předá je zpět do `IDebugPendingBreakpoint2` balíčku ladění jako jediné rozhraní.

 Zatím nebyly generovány žádné události.

 Ladicí balíček se pak pokusí svázat čekající zarážku s kódem nebo daty voláním [bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), který je implementován DE.

 Pokud je zarážka vázána, DE odešle rozhraní události [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) do ladicího balíčku. Ladicí balíček používá toto rozhraní k vytvoření výčtu všech kontextů kódu (nebo jednoho datového kontextu) vázaných na zarážku voláním [enumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), který vrací jedno nebo více rozhraní [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Rozhraní [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) vrátí rozhraní [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) a [Funkce GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) vrátí [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) sjednocení obsahující ho kód nebo kontext dat.

 Pokud DE nemůže svázat zarážku, odešle do ladicího balíčku jedno rozhraní události [IDebugBreakPointEventEvent2.](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) Ladicí balíček načte typ chyby (chyba nebo upozornění) a informační zprávu voláním [geterrorbreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), následovaný [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) a [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Vrátí [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) strukturu, která obsahuje typ chyby a zprávu.

 Pokud DE zpracovává zarážku, ale nelze ji svázat, vrátí chybu typu `BPET_TYPE_ERROR`. Ladicí balíček reaguje zobrazením chybového dialogového okna a rozhraní IDE umístí glyf vykřičníku do glyfu zarážky vlevo od řádku zdrojového kódu.

 Pokud DE zpracovává zarážku, nelze ji svázat, ale některé jiné DE může svázat, vrátí upozornění. IDE odpoví umístěním otázky glyfu uvnitř glyfu zarážky nalevo od řádku zdrojového kódu.

## <a name="see-also"></a>Viz také
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
