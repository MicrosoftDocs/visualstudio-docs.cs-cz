---
description: Tato metoda obnoví výčet adres na první prvek.
title: 'IEnumDebugAddresses:: resetovat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 385e650e908947288eafa6f3f2812db45f9721a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083138"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Tato metoda obnoví výčet na první prvek.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po volání této metody bude další volání funkce [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) vracet první prvek výčtu.

## <a name="see-also"></a>Viz také
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
