---
title: Zarážky vazeb | Microsoft Docs
description: Zjistěte, jak rozhraní IDE formuluje požadavek na zarážku a vyzve relaci ladění, aby vytvořila zarážku, když uživatel nastaví zarážku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 606c1f4cb5559722028b78ef4ef21c41c0ba5556
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914709"
---
# <a name="bind-breakpoints"></a>Vázání zarážek
Pokud uživatel nastaví zarážku, třeba stisknutím klávesy **F9**, rozhraní IDE formuluje požadavek a vyzve relaci ladění, aby vytvořila zarážku.

## <a name="set-a-breakpoint"></a>Nastavení zarážky
 Nastavení zarážky je proces se dvěma kroky, protože kód nebo data ovlivněná zarážkou nemusí být zatím k dispozici. Nejprve musí být zarážka popsána a poté, jak bude kód nebo data k dispozici, musí být vázány na tento kód nebo data, a to následujícím způsobem:

1. Zarážka je požadována z příslušných ladicích modulů (DEs) a pak je zarážka svázána s kódem nebo daty, jakmile budou k dispozici.

2. Požadavek na zarážku se pošle do ladicí relace, která ho pošle do všech relevantních DEs. Jakýkoli DE, který se rozhodne zpracovat zarážku, vytvoří odpovídající nevyřízenou zarážku.

3. Ladicí relace shromažďuje nevyřízené zarážky a odesílá je zpět do ladicího balíčku (součást ladění sady Visual Studio).

4. Ladicí balíček vyzve relaci ladění, aby navázala nevyřízenou zarážku na kód nebo data. Ladicí relace odesílá tento požadavek do všech relevantních DEs.

5. Pokud DE může svázat zarážku, pošle událost spojenou se zarážkou zpět do ladicí relace. Pokud ne, odešle místo toho událost chyby zarážky.

## <a name="pending-breakpoints"></a>Nedokončené zarážky
 Nevyřízená zarážka se může navazovat na více umístění kódu. Například řádek zdrojového kódu pro šablonu jazyka C++ se může přivážet ke každé sekvenci kódu generované ze šablony. Relace ladění může použít událost spojenou s zarážkou k vytvoření výčtu kontextů kódu vázaných na zarážku v době odeslání události. Další kontexty kódu mohou být vázány později, takže příkaz DE smí odeslat více událostí vázaných na zarážku pro každou žádost o vazbu. DE by ale měl odeslat jenom jednu chybovou událost zarážky na požadavek vazby.

## <a name="implementation"></a>Implementace
 Programově balíček ladění volá Správce ladění relace (SDM) a poskytuje mu rozhraní [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , které zabalí strukturu [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) , což popisuje, kterou zarážku má být nastavena. I když zarážky mohou mít mnoho formulářů, jejich konečné vyhodnocení na kód nebo kontext dat.

 Model SDM předá toto volání ke všem relevantním DE voláním metody [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) . Pokud se DE zvolí pro zpracování zarážky, vytvoří a vrátí rozhraní [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) . SDM shromáždí tato rozhraní a předá je zpět do ladicího balíčku jako jediné `IDebugPendingBreakpoint2` rozhraní.

 Zatím nejsou vygenerované žádné události.

 Ladicí balíček se pak pokusí vytvořit vazby na nevyřízenou zarážku na kód nebo data voláním metody [BIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), která je implementována pomocí příkazu de.

 Pokud je zarážka svázána, příkaz DE pošle rozhraní události [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) do balíčku pro ladění. Ladicí balíček používá toto rozhraní k zobrazení výčtu všech kontextů kódu (nebo jednoho kontextu dat) svázaného se zarážkou voláním [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), která vrací jedno nebo více [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) rozhraní. Rozhraní [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) vrací rozhraní [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) a [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) vrací sjednocení [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) obsahující kód nebo kontext dat.

 Pokud DE není schopen navazovat zarážku, pošle jediné rozhraní události [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do balíčku pro ladění. Ladicí balíček načte typ chyby (chyba nebo varování) a informační zprávu voláním [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), za nímž následuje [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) a [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Vrátí [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) strukturu, která obsahuje typ a zprávu o chybě.

 Pokud DE zpracuje zarážku, ale nemůže ji vytvořit, vrátí chybu typu `BPET_TYPE_ERROR` . Ladicí balíček reaguje zobrazením chybového dialogového okna a IDE umístí do glyfu zarážky symbol vykřičníku nalevo od řádku zdrojového kódu.

 Pokud DE zpracuje zarážku, nemůže ji vytvořit, ale jiné metody DE ji mohou vytvořit, vrátí upozornění. Rozhraní IDE odpoví umístěním glyfu otázky uvnitř glyfu zarážky nalevo od řádku zdrojového kódu.

## <a name="see-also"></a>Viz také
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
