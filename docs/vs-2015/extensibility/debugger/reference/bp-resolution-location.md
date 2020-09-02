---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ea6539f2ed790dda5cc4c9de126aa226f4b2686
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153296"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje strukturu umístění rozlišení zarážky.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Členové  
 `bpType`  
 Hodnota z výčtu [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) , která určuje, jak se mají interpretovat `bpResLocation` sjednocení nebo `unionmemberX` členy.  
  
 `bpResLocation.bpresCode`  
 [Pouze C++] Obsahuje strukturu [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) , pokud `bpType`  =  `BPT_CODE` .  
  
 `bpResLocation.bpresData`  
 [Pouze C++] Obsahuje strukturu [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) , pokud `bpType`  =  `BPT_DATA` .  
  
 `bpResLocation.unused`  
 [Pouze C++] Zástupný symbol.  
  
 `unionmember1`  
 [Pouze C#] Viz poznámky, jak interpretovat.  
  
 `unionmember2`  
 [Pouze C#] Viz poznámky, jak interpretovat.  
  
 `unionmember3`  
 [Pouze C#] Viz poznámky, jak interpretovat.  
  
 `unionmember4`  
 [Pouze C#] Viz poznámky, jak interpretovat.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je členem [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) a [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktur.  
  
 [Pouze C#] `unionmemberX` Členy jsou interpretovány podle následující tabulky. Vyhledejte levý sloupec pro `bpType` hodnotu a pak napříč a určete, co každý `unionmemberX` člen představuje a zařaďte `unionmemberX` odpovídajícím způsobem zařadit. Podívejte se na příklad pro způsob interpretace této struktury v jazyce C#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (datový výraz)|`string` (název funkce)|`string` (název obrázku)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak interpretovat `BP_RESOLUTION_LOCATION` strukturu v jazyce C#.  
  
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
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
