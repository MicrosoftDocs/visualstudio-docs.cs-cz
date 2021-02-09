---
title: 'IEnumDebugErrorBreakpoints2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::GetCount
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::GetCount
ms.assetid: 56f7bb70-d55b-471c-8c65-09a9e7f4938e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ff426a16a9dec71f809202a9ba0a70e9f2c4965
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897003"
---
# <a name="ienumdebugerrorbreakpoints2getcount"></a>IEnumDebugErrorBreakpoints2::GetCount
Vrátí počet prvků ve výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametry
`pcelt`\
mimo Vrátí počet prvků ve výčtu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda není součástí vlastního rozhraní výčtu modelu COM, které určuje, že `Next` `Clone` `Skip` `Reset` je nutné implementovat pouze metody,, a.

## <a name="see-also"></a>Viz také
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
