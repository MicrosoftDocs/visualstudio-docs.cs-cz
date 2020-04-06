---
title: IDebugEngine2::CauseBreak | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62be3ce13ecbc3180cf2bbcce26b04f3d79edb1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731165"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Požaduje, aby všechny programy, které jsou laděny tímto ladicím strojem (DE), aby se zastavilo provádění při příštím pokusu o spuštění jednoho z jejich vláken.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je asynchronní: Událost [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) je odeslána při dalším pokusu programu o spuštění po volání této metody.

## <a name="see-also"></a>Viz také
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
