---
title: IDebugProcess2::EnumThreads | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724066"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Načte seznam všech vláken spuštěných v procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Vrátí objekt [IEnumDebugThreads2,](../../../extensibility/debugger/reference/ienumdebugthreads2.md) který obsahuje seznam všech vláken ve všech programech v procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vytvoří výčet podprocesů spuštěných v každém programu a pak je zkombinuje do zobrazení procesu podprocesů. Jedno vlákno může být spuštěno ve více programech. tato metoda vyjmenovává toto vlákno pouze jednou.

 Tato metoda představuje seznam vláken procesu bez duplikátů. V opačném případě výčet podprocesů spuštěných v určitém programu použijte metodu [EnumThreads.](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
