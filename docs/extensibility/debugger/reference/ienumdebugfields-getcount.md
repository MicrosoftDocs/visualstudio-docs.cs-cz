---
description: Tato metoda vrací počet prvků ve výčtu polí.
title: 'IEnumDebugFields:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dbce3c9f990e28b63ca3b600e89d12736021dbf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226641"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Tato metoda vrací počet prvků ve výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
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
 Tato metoda není součástí vlastního rozhraní výčtu modelu COM, které určuje, že je nutné implementovat pouze další, klonování, přeskočení a resetování.

## <a name="see-also"></a>Viz také
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
