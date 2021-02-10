---
title: 'IDebugArrayField:: GetNumberOfElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3454624feab268af089a5e82e38c0cce3d23ab03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940303"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Získá počet prvků v poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Parametry
`pdwNumElements`\
mimo Vrátí počet prvků v poli.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vrácená hodnota je celkový počet prvků v poli, bez ohledu na počet rozměrů.

## <a name="see-also"></a>Viz také
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
