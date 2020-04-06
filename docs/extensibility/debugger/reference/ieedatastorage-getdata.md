---
title: IEEDataStorage::GetData | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718207"
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
[v] Počet bajtů načíst `data` (pole musí obsahovat alespoň tento počet bajtů).

`sizeGotten`\
[out] Vrátí počet skutečně načtených bajtů.

`data`\
[dovnitř, ven] Pole, které má být vyplněno požadovanými daty.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Doporučené použití této metody je načíst všechna data bajtů do místního pole, protože neexistuje žádný způsob, jak přeskočit bajty v procesu načítání. V tomto případě `dataSize` by parametr měl být hodnota vrácená [metodou GetSize.](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

## <a name="see-also"></a>Viz také
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
