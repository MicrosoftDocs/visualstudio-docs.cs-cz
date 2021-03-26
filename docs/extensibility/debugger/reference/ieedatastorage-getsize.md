---
description: Vrátí počet bajtů obsažených v tomto objektu.
title: 'IEEDataStorage:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 632d2adeaca976d0bb3fdfbe1b88571e337e02dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083528"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Vrátí počet bajtů obsažených v tomto objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parametry
`size`\
mimo Počet bajtů obsažených v tomto objektu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 K načtení skutečných datových bajtů použijte metodu [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) .

## <a name="see-also"></a>Viz také
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [Získat data](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
