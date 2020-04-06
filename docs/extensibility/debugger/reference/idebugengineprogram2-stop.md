---
title: IDebugEngineProgram2::Stop | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730479"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Zastaví všechna vlákna spuštěná v tomto programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána, když je tento program odladěn v prostředí s více programy. Při přijetí události zastavení z jiného programu je tato metoda volána v tomto programu. Implementace této metody by měla být asynchronní; to znamená, že ne všechna vlákna by měla být požadována k zastavení před vrácením této metody. Implementace této metody může být stejně jednoduché jako volání [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) metoda v tomto programu.

 Implementátoři by měli odeslat [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) při zastavení programu.

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
