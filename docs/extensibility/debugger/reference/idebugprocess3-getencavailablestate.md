---
description: Tato metoda získá aktuální stav operace Upravit a pokračovat.
title: 'IDebugProcess3:: GetENCAvailableState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13ad3bc88ab1e9f10dc87db7d7124adc993b168c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149770"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Tato metoda získá aktuální stav operace Upravit a pokračovat. Vlastní dodavatel portu by měl vždycky vracet `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parametry
`pReason`\
mimo Hodnota z výčtu [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

> [!NOTE]
> Vlastní dodavatel portu by měl vždycky vracet `E_NOTIMPL` .

## <a name="remarks"></a>Poznámky
 Tento stav může mít vliv na [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
