---
title: IDebugAddress::GetAddress | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736607"
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
[dovnitř, ven] DEBUG_ADDRESS [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury, která je vyplněna touto metodou.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 DEBUG_ADDRESS [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktura je předána této metodě, která ji pak vyplní příslušnými informacemi. Způsob interpretace těchto informací závisí na druhu vrácených informací a samotné obslužné rutině symbolu. Další podrobnosti najdete [DEBUG_ADDRESS.](../../../extensibility/debugger/reference/debug-address.md)

## <a name="see-also"></a>Viz také
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
