---
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 911556cb615e373d620b496fb31e5d6093b7cc37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869931"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Tato metoda načte rozšířené informace o poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parametry
`guidExtendedInfo`\
pro Vybere informace, které mají být vráceny. Platné hodnoty jsou:

|Hodnota|Popis|
|-----------|-----------------|
|`guidConstantValue`|Hodnota jako posloupnost bajtů.|
|`guidConstantType`|Typ jako podpis typu.|

`prgBuffer`\
mimo Vrátí rozšířené informace.

`pdwLen`\
[in, out] Vrátí velikost rozšířených informací v bajtech.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V současné době tato metoda vrátí pouze typ nebo hodnotu konstanty. Volající musí uvolnit vyrovnávací paměť vrácenou `prgBuffer` voláním `CoTaskMemFree` funkce com (C++) nebo <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Viz také
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
