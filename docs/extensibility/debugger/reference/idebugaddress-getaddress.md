---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df4eb1278a0fe436899c1da989c4c63cfa98cac3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853009"
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
