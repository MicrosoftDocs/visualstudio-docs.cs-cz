---
title: IDebugThread2::GetName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718770"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Získá název vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
[out] Vrátí název vlákna.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Načtený název je vždy název, který lze zobrazit a tento název popisuje vlákno. Název vlákna může být odvozen z architektury za běhu, která podporuje pojmenovaná vlákna, nebo může být název odvozený z ladicího stroje. Případně název vlákna lze nastavit voláním Metody [SetThreadName.](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
