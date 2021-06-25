---
title: Metody Breakpoint-Related | Microsoft Docs
description: Ladění sady Visual Studio podporuje vázané zarážky, které jsou úspěšně svázány s umístěním v kódu a čekají na zarážky, které ještě nejsou vázané.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec218cea05dffc1c558cabdef47895da9ad7ba9c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901497"
---
# <a name="breakpoint-related-methods"></a>Metody související se zarážkami
Ladicí stroj (DE) musí podporovat nastavení zarážek. Ladění sady Visual Studio podporuje následující typy zarážek:

- Bound

     Požadováno prostřednictvím uživatelského rozhraní a úspěšné vázání na zadané umístění kódu

- Čekající

     Požadováno prostřednictvím uživatelského rozhraní, ale ještě není vázané na skutečné pokyny

## <a name="discussion"></a>Diskuse
 Například nevyřízená zarážka nastane, když pokyny ještě nejsou načteny. Při načtení kódu se nevyřízené zarážky pokusí vytvořit vazby na kód v předepsaném umístění, tedy pro vložení instrukcí break do kódu. Události se odesílají do Správce ladění relace (SDM), aby označovaly úspěšné vazby nebo oznámily, že došlo k chybám vazeb.

 Nevyřízená zarážka také spravuje svůj vlastní interní seznam odpovídajících svázaných zarážek. Jedna nevyřízená zarážka může způsobit vložení mnoha zarážek v kódu. Uživatelské rozhraní ladění sady Visual Studio zobrazuje stromové zobrazení nevyřízených zarážek a jejich odpovídajících vázaných zarážek.

 Vytváření a používání nevyřízených zarážek vyžaduje implementaci metody [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) a také následující metody rozhraní [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

|Metoda|Popis|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Určuje, zda zadaná nedokončená zarážka může vytvořit vazby na umístění kódu.|
|[Zapisovat](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Váže určenou nevyřízenou zarážku na jedno nebo více umístění kódu.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Získá stav čeká na zarážce.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Získá požadavek na zarážku, který se používá k vytvoření nedokončené zarážky.|
|[Povolení](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Přepne povolený stav čeká na zarážku.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Vytvoří výčet všech zarážek vázaných z nedokončené zarážky.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Vytvoří výčet všech zarážek s chybami, které jsou výsledkem nedokončené zarážky.|
|[Odstranit](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Odstraní nevyřízenou zarážku a všechny zarážky, které jsou z něho svázané.|

 Chcete-li vytvořit výčet vázaných zarážek a chyb zarážek, je nutné implementovat všechny metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) a [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Nedokončené zarážky, které se vážou na umístění kódu, vyžadují implementaci následujících metod [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

|Metoda|Popis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Získá nevyřízenou zarážku, která obsahuje zarážku.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Získá stav vázané zarážky.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Získá rozlišení zarážky, které popisuje zarážku.|
|[Povolení](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Povoluje nebo zakazuje zarážku.|
|[Odstranit](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Odstraní vázanou zarážku.|

 Informace o řešení a požadavku vyžadují implementaci následujících metod [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

|Metoda|Popis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky reprezentované rozlišením.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Získá informace o rozlišení zarážky, které popisují zarážku.|

 Řešení chyb, ke kterým může dojít během vytváření vazby, vyžaduje implementaci následujících metod [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

|Metoda|Popis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Získá nevyřízenou zarážku obsahující chybovou zarážku.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Získá rozlišení chyby zarážky, které popisuje chybovou zarážku.|

 Řešení chyb, ke kterým může dojít během vytváření vazby, vyžaduje také následující metody [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Metoda|Popis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Získá informace o řešení zarážky.|

 Zobrazení zdrojového kódu na zarážce vyžaduje, abyste implementovali metody [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) a/nebo metody [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
