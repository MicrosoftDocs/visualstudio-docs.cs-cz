---
title: BP_RESOLUTION_LOCATION | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737820"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Určuje strukturu umístění rozlišení zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Členové
`bpType`\
Hodnota z [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) výčtu, který určuje, `bpResLocation` jak `unionmemberX` interpretovat unie nebo členy.

`bpResLocation.bpresCode`\
[Pouze C++] Obsahuje [strukturu](../../../extensibility/debugger/reference/bp-resolution-code.md) BP_RESOLUTION_CODE `bpType`  =  `BPT_CODE`if .

`bpResLocation.bpresData`\
[Pouze C++] Obsahuje [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) strukturu `bpType`  =  `BPT_DATA`if .

`bpResLocation.unused`\
[Pouze C++] Zástupný symbol.

`unionmember1`\
[Pouze C#] Viz Poznámky k interpretaci.

`unionmember2`\
[Pouze C#] Viz Poznámky k interpretaci.

`unionmember3`\
[Pouze C#] Viz Poznámky k interpretaci.

`unionmember4`\
[Pouze C#] Viz Poznámky k interpretaci.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) a [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktur.

 [Pouze C#] Členy `unionmemberX` jsou interpretovány podle následující tabulky. Podívejte se do levého sloupce pro hodnotu `bpType` pak napříč určit, co každý `unionmemberX` člen představuje a zařazovat `unionmemberX` odpovídajícím způsobem. Viz Příklad způsob, jak interpretovat tuto strukturu v C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(datový výraz)|`string`(název funkce)|`string`(název obrázku)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Příklad
Tento příklad ukazuje, `BP_RESOLUTION_LOCATION` jak interpretovat strukturu v C#.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
