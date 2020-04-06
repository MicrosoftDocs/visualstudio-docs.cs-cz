---
title: IDebugCanStopEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734507"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Toto rozhraní se používá k dotazu správce ladění relace (SDM), zda se má zastavit v aktuálním umístění kódu.

## <a name="syntax"></a>Syntaxe

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní pro podporu krokování zdrojového kódu. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto `IDebugEvent2` rozhraní (SDM používá [QueryInterface](/cpp/atl/queryinterface) pro přístup k rozhraní).

 Implementace tohoto rozhraní musí komunikovat volání SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) do ladicí modul. Například to lze provést se zprávou zaúčtované do vlákna zpracování zpráv ladicího stroje nebo objekt implementující toto rozhraní může obsahovat `IDebugCanStopEvent2::CanStop`odkaz na ladicí modul a volat zpět do ladicího modulu s příznakem předaným do .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE můžete odeslat tuto metodu pokaždé, když DE je požádán, aby pokračovat v provádění a DE je krokování kódu. Tato událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zajišťované sdm, když je připojena k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugCanStopEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Získá důvod pro tuto událost.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Určuje, zda má laděný program zastavit v umístění této události (a odeslat událost, která popisuje důvod zastavení) nebo pokračovat v provádění.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Získá kontext dokumentu, který popisuje umístění této události.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Získá kontext kódu, který popisuje umístění této události.|

## <a name="remarks"></a>Poznámky
 DE odešle toto rozhraní, pokud uživatel kroky do funkce a DE najde žádné informace o ladění existuje nebo ladicí informace existuje, ale DE neví, pokud zdrojový kód lze zobrazit pro toto umístění.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
