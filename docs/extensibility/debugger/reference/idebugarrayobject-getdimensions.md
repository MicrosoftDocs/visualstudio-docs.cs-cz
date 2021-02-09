---
title: 'IDebugArrayObject:: GetDimensions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c0c71032fc8f5c75522f6b1f9e0d8cb1308f63f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870191"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Získá rozměry pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
pro Počet dimenzí, které mají být načteny.

`dwDimensions`\
[in, out] Pole, které je vyplněno velikostmi každé dimenze. `dwCount` Určuje maximální velikost `dwDimensions` pole.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Multidimenzionální pole může mít různé velikosti pro každou dimenzi. Například vzhledem k trojrozměrnému poli `myarray[3][2][6]` by tato metoda vrátila 3, 2 a 6 v `dwDimensions` parametru v tomto pořadí.

## <a name="see-also"></a>Viz také
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
