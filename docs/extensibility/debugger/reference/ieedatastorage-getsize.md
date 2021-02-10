---
title: 'IEEDataStorage:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a18ae08500bd457f6e9ab316514836a30538a42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965509"
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
