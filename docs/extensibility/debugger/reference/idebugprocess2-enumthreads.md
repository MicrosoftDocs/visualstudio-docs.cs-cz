---
description: Načte seznam všech vláken spuštěných v procesu.
title: 'IDebugProcess2:: EnumThreads – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c502504b3a31f3e4689db34f907f9596b214877
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071607"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Načte seznam všech vláken spuštěných v procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
mimo Vrátí objekt [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) , který obsahuje seznam všech vláken ve všech programech v procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vytvoří výčet vláken spuštěných v každém programu a jejich kombinaci do zobrazení procesu vláken. Jedno vlákno může běžet v několika programech. Tato metoda vytvoří výčet pouze jednou vláknem.

 Tato metoda prezentuje seznam vláken procesu bez duplicitních hodnot. V opačném případě pro zobrazení výčtu vláken spuštěných v určitém programu použijte metodu [EnumThreads –](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
