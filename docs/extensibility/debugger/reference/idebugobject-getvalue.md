---
title: 'IDebugObject:: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7534a05879bdae0a885ae0cbe23d072c30132d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846800"
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
[in, out] Pole, které je vyplněno po sobě jdoucí sérii bajtů představujících hodnotu objektu.

`nSize`\
pro Maximální počet bajtů, které mají být načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Získat celkový počet bajtů hodnot, které lze načíst voláním metody [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) .

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
