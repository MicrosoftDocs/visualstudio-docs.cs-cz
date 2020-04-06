---
title: BP_LOCATION | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737926"
---
# <a name="bp_location"></a>BP_LOCATION
Určuje typ struktury použité k popisu umístění zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Členové
`bpLocationType`\
Hodnota z [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) výčtu slouží `bpLocation` k interpretaci unie nebo `unionmemberX` členy.

`bpLocation`.`bplocCodeFileLine`\
[Pouze C++] Obsahuje [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) strukturu `bpLocationType`  =  `BPLT_CODE_FILE_LINE`if .

`bpLocation.bplocCodeFuncOffset`\
[Pouze C++] Obsahuje [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) strukturu `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`if .

`bpLocation.bplocCodeContext`\
[Pouze C++] Obsahuje [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) strukturu `bpLocationType`  =  `BPLT_CODE_CONTEXT`if .

`bpLocation.bplocCodeString`\
[Pouze C++] Obsahuje [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) strukturu `bpLocationType`  =  `BPLT_CODE_STRING`if .

`bpLocation.bplocCodeAddress`\
[Pouze C++] Obsahuje [strukturu](../../../extensibility/debugger/reference/bp-location-code-address.md) BP_LOCATION_CODE_ADDRESS `bpLocationType`  =  `BPLT_CODE_ADDRESS`if .

`bpLocation.bplocDataString`\
[Pouze C++] Obsahuje [strukturu](../../../extensibility/debugger/reference/bp-location-data-string.md) BP_LOCATION_DATA_STRING `bpLocationType`  =  `BPLT_DATA_STRING`if .

`bpLocation.bplocResolution`\
[Pouze C++] Obsahuje [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) strukturu `bpLocationType`  =  `BPLT_RESOLUTION`if .

`unionmember1`\
[Pouze C#] Viz Poznámky k interpretaci.

`unionmember2`\
[Pouze C#] Viz Poznámky k interpretaci.

`unionmember3`\
[Pouze C#] Viz Poznámky k interpretaci.

`unionmember4`\
[Pouze C#] Viz Poznámky k interpretaci.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktur.

 [Pouze C#] Členy `unionmemberX` jsou interpretovány podle následující tabulky. Podívejte se do levého sloupce pro hodnotu `bpLocationType` a `unionmemberX` pak se podívejte `unionmemberX` přes ostatní sloupce k určení, co každý člen představuje a zařazuje odpovídajícím způsobem. Viz příklad pro způsob, jak interpretovat část této struktury v C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(kontext)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(kontext)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(kontext)|`string`(podmíněný výraz)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(kontext)|`string`(adresa URL modulu)|`string`(název funkce)|`string`(adresa)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(kontext)|`string`(datový výraz)|`uint`(počet prvků)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Příklad
Tento příklad ukazuje, `BP_LOCATION` jak interpretovat strukturu `BPLT_DATA_STRING` v C# pro typ. Tento konkrétní typ ukazuje, `unionmemberX` jak interpretovat všechny čtyři členy ve všech možných formátech (objekt, řetězec a číslo).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
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
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
