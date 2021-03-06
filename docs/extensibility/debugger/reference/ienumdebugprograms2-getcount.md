---
description: Vrátí počet prvků výčtu programů.
title: 'IEnumDebugPrograms2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::GetCount
helpviewer_keywords:
- IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0d6fb47478a75e9636f7da3f4097c01e7bd378b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224366"
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
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
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
