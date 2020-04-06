---
title: IDebugMessageEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727357"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Toto rozhraní používá ladicí modul (DE) k odeslání zprávy do sady Visual Studio, která vyžaduje odpověď od uživatele.

## <a name="syntax"></a>Syntaxe

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 De implementuje toto rozhraní k odeslání zprávy do sady Visual Studio, která vyžaduje odpověď uživatele. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

 Implementace tohoto rozhraní musí komunikovat Visual Studio volání [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) de. Například to lze provést se zprávou zaúčtované do vlákna zpracování zpráv DE nebo objekt implementující toto rozhraní může obsahovat odkaz na DE a volat zpět na DE s odpovědí předána do `IDebugMessageEvent2::SetResponse`.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události zobrazit zprávu pro uživatele, který vyžaduje odpověď. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm, když je připojen k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugMessageEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Získá zprávu, která má být zobrazena.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Nastaví odpověď, pokud existuje, z okna se zprávou.|

## <a name="remarks"></a>Poznámky
 DE bude používat toto rozhraní, pokud vyžaduje konkrétní odpověď od uživatele pro konkrétní zprávu. Například pokud DE získá zprávu "Přístup byl odepřen" po pokusu o vzdálené připojení k programu, `IDebugMessageEvent2` DE odešle tuto `MB_RETRYCANCEL`konkrétní zprávu do sady Visual Studio v události se stylem okna se zprávou . To umožňuje uživateli opakovat nebo zrušit operaci připojení.

 DE určuje, jak má být tato zpráva zpracována podle konvencí funkce `MessageBox` Win32 (podrobnosti naleznete v tématu [AfxMessageBox).](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

 Pomocí rozhraní [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) odesílejte zprávy do sady Visual Studio, které nevyžadují odpověď od uživatele.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
