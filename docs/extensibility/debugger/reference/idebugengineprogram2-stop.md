---
description: Zastaví všechna vlákna spuštěná v tomto programu.
title: 'IDebugEngineProgram2:: stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3867e4e3f119e69734495d5c545d53348755af3a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153453"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Zastaví všechna vlákna spuštěná v tomto programu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána, když je tento program laděn v prostředí s více programy. Je-li přijata událost zastavení z nějakého jiného programu, je tato metoda volána v tomto programu. Implementace této metody by měla být asynchronní; To znamená, že před vrácením této metody musí být nutné zastavit všechna vlákna. Implementace této metody může být jednoduchá jako volání metody [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) v tomto programu.

 Implementátor by měl při zastavení programu odeslat [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) .

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
