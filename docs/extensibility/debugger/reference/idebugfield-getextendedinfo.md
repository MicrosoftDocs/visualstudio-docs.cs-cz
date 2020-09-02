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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728875"
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
