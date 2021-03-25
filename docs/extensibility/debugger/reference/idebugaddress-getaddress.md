---
description: Vrátí strukturu popisující objekt a jeho umístění v rámci jeho oboru nebo kontejneru.
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094393"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Vrátí strukturu popisující objekt a jeho umístění v rámci jeho oboru nebo kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[in, out] Struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , která je touto metodou vyplněna.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Do této metody je předána struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , která je následně vyplní příslušnými informacemi. Způsob interpretace těchto informací závisí na typu vrácených informací a samotné obslužné rutině symbolů. Další podrobnosti najdete v tématu [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>Viz také
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
