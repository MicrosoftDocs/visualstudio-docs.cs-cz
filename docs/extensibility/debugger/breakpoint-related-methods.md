---
title: Metody související s zarážkem | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739207"
---
# <a name="breakpoint-related-methods"></a>Metody související s zarážkem
Ladicí modul (DE) musí podporovat nastavení zarážek. Ladění sady Visual Studio podporuje následující typy zarážek:

- Bound

     Požadováno prostřednictvím hlavního nastavení a úspěšně vázáno na zadané umístění kódu

- Čekající na vyřízení

     Požadováno prostřednictvím hlavního použití, ale ještě není vázáno na skutečné pokyny

## <a name="discussion"></a>Diskuse
 Například čekající zarážka nastane, když pokyny ještě nejsou načteny. Při načtení kódu čekající zarážky se pokusí svázat s kódem v předepsaném umístění, to znamená vložit pokyny přerušení v kódu. Události jsou odesílány do správce ladění relace (SDM) k označení úspěšné vazby nebo upozornit, že došlo k chybám vazby.

 Čekající zarážka také spravuje vlastní interní seznam odpovídajícívázané zarážky. Jedna čekající zarážka může způsobit vložení mnoha zarážek v kódu. Visual Studio ladění uhlavního zobrazení stromu čekající zarážky a jejich odpovídající vázané zarážky.

 Vytvoření a použití čekajících zarážek vyžadují implementaci [metody IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) a následujících metod rozhraní [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Metoda|Popis|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Určuje, zda se zadaná čekající zarážka může svázat s umístěním kódu.|
|[Vytvořit vazbu](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Sváže zadanou čekající zarážku s jedním nebo více umístěními kódu.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Získá stav čekající zarážky.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Získá požadavek na zarážky slouží k vytvoření čekající zarážka.|
|[Povolení](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Přepíná povolený stav čekající zarážky.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Vyjmenovává všechny zarážky vázané z čekající zarážky.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Vyjmenovává všechny chybové zarážky, které jsou výsledkem čekající zarážky.|
|[Odstranit](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Odstraní čekající zarážku a všechny zarážky z ní vázané.|

 Chcete-li vytvořit výčet vázaných zarážek a zarážek chyb, je nutné implementovat všechny metody [IEnum DebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) a [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Čekající zarážky, které se vážou k umístění kódu vyžadují implementaci následujících metod [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Metoda|Popis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Získá čekající zarážka, která obsahuje zarážku.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Získá stav vázané zarážky.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Získá rozlišení zarážky, která popisuje zarážku.|
|[Povolení](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Povolí nebo zakáže zarážku.|
|[Odstranit](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Odstraní vázanou zarážku.|

 Informace o řešení a požadavku vyžadují implementaci následujících metod [IDebugBreakpointResolution2.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Metoda|Popis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky reprezentované rozlišení.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Získá informace o rozlišení zarážky, která popisuje zarážku.|

 Řešení chyb, ke kterým může dojít během vazby, vyžaduje implementaci následujících metod [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Metoda|Popis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Získá čekající zarážka, která obsahuje zarážky chyby.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Získá rozlišení chyby zarážky, která popisuje zarážky chyby.|

 Řešení chyb, ke kterým může dojít během vazby, vyžaduje také následující metody [IDebugErrorBreakpointresolutionResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Metoda|Popis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Získá informace o řešení zarážky.|

 Zobrazení zdrojového kódu na zarážky vyžaduje implementaci metod [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) a/nebo metody [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
