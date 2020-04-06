---
title: IEnumDebugThreads2::Obnovit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f90a0d130d69a0c710c89bb346ad9756ac54289
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715111"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
Obnoví výčet na první prvek.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po volání této metody další volání [Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) metoda vrátí první prvek výčtu.

## <a name="see-also"></a>Viz také
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
