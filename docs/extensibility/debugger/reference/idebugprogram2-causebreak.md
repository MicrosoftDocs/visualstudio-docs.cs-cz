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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64ad2a22a06cc18595aabb37e3c244c7ea0c0be1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076157"
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
