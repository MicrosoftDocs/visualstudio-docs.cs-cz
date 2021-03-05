---
description: Toto rozhraní používá modul ladění (DE) k odeslání zprávy do aplikace Visual Studio, která vyžaduje odpověď od uživatele.
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c84bf93a50ce9a5e530ebb7143d7b1c69f50360
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172270"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Toto rozhraní používá modul ladění (DE) k odeslání zprávy do aplikace Visual Studio, která vyžaduje odpověď od uživatele.

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní k odeslání zprávy do aplikace Visual Studio, která vyžaduje reakci uživatele. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

 Implementace tohoto rozhraní musí komunikovat se [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) voláním sady Visual Studio do de. To lze provést například pomocí zprávy zveřejněné ve vlákně zpracování zprávy DE nebo objekt implementující toto rozhraní může obsahovat odkaz na DE a volání zpět do DE s předanou odpovědí `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a pošle tento objekt události, aby zobrazil zprávu uživateli, který vyžaduje odpověď. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugMessageEvent2` .

|Metoda|Popis|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Získá zprávu, která se má zobrazit.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|V okně se zprávou nastaví odpověď (pokud existuje).|

## <a name="remarks"></a>Poznámky
 DE použije toto rozhraní, pokud vyžaduje konkrétní odpověď od uživatele pro konkrétní zprávu. Například pokud DE Získá zprávu "přístup byl odepřen" poté, co se pokusí vzdáleně připojit k programu, vrátí tato konkrétní zpráva do sady Visual Studio v `IDebugMessageEvent2` události se stylem okna se zprávou `MB_RETRYCANCEL` . To uživateli umožňuje opakovat nebo zrušit operaci připojení.

 DE určuje, jak bude tato zpráva zpracována podle konvencí funkce Win32 `MessageBox` (podrobnosti viz [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) ).

 Použijte rozhraní [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) k posílání zpráv do sady Visual Studio, které nevyžadují odpověď od uživatele.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
