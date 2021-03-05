---
description: Načte zadaný počet bajtů z objektu.
title: 'IEEDataStorage:: GetData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f28533ad07bc7626f1576ef4422d6d20725b9450
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227304"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Načte zadaný počet bajtů z objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parametry
`dataSize`\
pro Počet bajtů, které mají být načteny ( `data` pole musí obsahovat alespoň tento počet bajtů).

`sizeGotten`\
mimo Vrátí počet bajtů, které byly skutečně načteny.

`data`\
[in, out] Pole, které se má vyplnit požadovanými daty

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Doporučené použití této metody je načtení všech datových bajtů do místního pole, protože neexistuje žádný způsob, jak přeskočit bajty v procesu načítání. V tomto případě `dataSize` by měl být parametr hodnotou vrácenou metodou [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .

## <a name="see-also"></a>Viz také
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize –](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
