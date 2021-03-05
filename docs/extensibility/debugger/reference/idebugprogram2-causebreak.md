---
description: Požaduje, aby program zastavil provádění při příštím pokusu o spuštění některého z jeho vláken.
title: 'IDebugProgram2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef10a714b6e65b40edb83cb0547ae1a28720d328
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166031"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Požaduje, aby program zastavil provádění při příštím pokusu o spuštění některého z jeho vláken.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Událost [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) se pošle, když se program příště pokusí spustit kód po volání této metody.

 Tato metoda je asynchronní v tom, že metoda vrátí hodnotu okamžitě, aniž by musela čekat na zastavení programu.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
