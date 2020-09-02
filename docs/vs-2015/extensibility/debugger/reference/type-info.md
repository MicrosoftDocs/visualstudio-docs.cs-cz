---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837084"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato struktura určuje různé druhy informací o typu pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 dwKind  
 Hodnota z výčtu [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) , která určuje, jakým způsobem se má sjednocení vysvětlit.  
  
 Type. typeMeta  
 [Pouze C++] Obsahuje strukturu [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) , pokud `dwKind` je `TYPE_KIND_METADATA` .  
  
 Type. typePdb  
 [Pouze C++] Obsahuje strukturu [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) , pokud `dwKind` je `TYPE_KIND_PDB` .  
  
 Type. typeBuilt  
 [Pouze C++] Obsahuje strukturu [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) , pokud `dwKind` je `TYPE_KIND_BUILT` .  
  
 typ. Nepoužito  
 Nepoužité odsazení  
  
 typ  
 Název sjednocení  
  
 unionmember  
 [Pouze C#] Zařaďte ho do příslušného typu struktury na základě `dwKind` .  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předána metodě [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) , kde je vyplněna. Způsob interpretace obsahu struktury je založen na `dwKind` poli.  
  
> [!NOTE]
> [Pouze C++] Je-li `dwKind` rovno `TYPE_KIND_BUILT` , je nutné uvolnit základní objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) při zničení `TYPE_INFO` struktury. To se provádí voláním metody `typeInfo.type.typeBuilt.pUnderlyingField->Release()` .  
  
 [Pouze C#] Následující tabulka ukazuje, jak interpretovat `unionmember` člena pro každý typ typu. Příklad ukazuje, jak je provedeno pro jeden druh typu.  
  
|`dwKind`|`unionmember` interpretováno jako|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak interpretovat `unionmember` člena `TYPE_INFO` struktury v jazyce C#. Tento příklad ukazuje, jak interpretovat pouze jeden typ ( `TYPE_KIND_METADATA` ), ale ostatní jsou interpretovány přesně stejným způsobem.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
