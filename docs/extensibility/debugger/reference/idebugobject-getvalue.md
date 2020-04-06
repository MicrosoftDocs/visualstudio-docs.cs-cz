---
title: IDebugObject::GetValue | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726542"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Získá hodnotu objektu jako po sobě jdoucí řady bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parametry
`pValue`\
[dovnitř, ven] Pole, které je vyplněno po sobě jdoucí řadou bajtů představujících hodnotu objektu.

`nSize`\
[v] Maximální počet bajtů načíst.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Získejte celkový počet bajtů hodnoty, které lze načíst voláním metody [GetSize.](../../../extensibility/debugger/reference/idebugobject-getsize.md)

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
