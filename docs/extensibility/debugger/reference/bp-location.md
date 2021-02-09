---
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15f52f9b71bcb18131e03a7d7fbdd9f56ac4fa6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902123"
---
# <a name="bp_location"></a>BP_LOCATION
Určuje typ struktury sloužící k popisu umístění zarážky.

## <a name="syntax"></a>Syntax

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
Hodnota z výčtu [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) používaná k interpretaci `bpLocation` sjednocení nebo `unionmemberX` členů.

`bpLocation`.`bplocCodeFileLine`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) , pokud `bpLocationType`  =  `BPLT_CODE_FILE_LINE` .

`bpLocation.bplocCodeFuncOffset`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) , pokud `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` .

`bpLocation.bplocCodeContext`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) , pokud `bpLocationType`  =  `BPLT_CODE_CONTEXT` .

`bpLocation.bplocCodeString`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) , pokud `bpLocationType`  =  `BPLT_CODE_STRING` .

`bpLocation.bplocCodeAddress`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) , pokud `bpLocationType`  =  `BPLT_CODE_ADDRESS` .

`bpLocation.bplocDataString`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) , pokud `bpLocationType`  =  `BPLT_DATA_STRING` .

`bpLocation.bplocResolution`\
[Pouze C++] Obsahuje strukturu [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) , pokud `bpLocationType`  =  `BPLT_RESOLUTION` .

`unionmember1`\
[Pouze C#] Viz poznámky, jak interpretovat.

`unionmember2`\
[Pouze C#] Viz poznámky, jak interpretovat.

`unionmember3`\
[Pouze C#] Viz poznámky, jak interpretovat.

`unionmember4`\
[Pouze C#] Viz poznámky, jak interpretovat.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktur.

 [Pouze C#] `unionmemberX` Členy jsou interpretovány podle následující tabulky. Vyhledejte v levém sloupci `bpLocationType` hodnotu a pak Prohlédněte v ostatních sloupcích, abyste určili, co každý `unionmemberX` člen představuje a `unionmemberX` odpovídajícím způsobem zařaďte. Podívejte se na příklad pro způsob, jak interpretovat část této struktury v jazyce C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (kontext)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (kontext)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (kontext)|`string` (podmíněný výraz)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (kontext)|`string` (adresa URL modulu)|`string` (název funkce)|`string` adresáře|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (kontext)|`string` (datový výraz)|`uint` (počet prvků)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak interpretovat `BP_LOCATION` strukturu v jazyce C# pro `BPLT_DATA_STRING` typ. Tento konkrétní typ ukazuje, jak interpretovat všechny čtyři `unionmemberX` členy ve všech možných formátech (objekt, řetězec a číslo).

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
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

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
