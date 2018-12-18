---
title: TYPE_INFO | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 628d6e5ae2e13ea117cb3fd50aca3ba2150ac59f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755446"
---
# <a name="typeinfo"></a>TYPE_INFO
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
 Hodnota z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) výčet, který určuje, jak interpretovat sjednocení.  
  
 type.typeMeta  
 [Jenom C++] Obsahuje [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) strukturu Pokud `dwKind` je `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [Jenom C++] Obsahuje [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) strukturu Pokud `dwKind` je `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [Jenom C++] Obsahuje [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) strukturu Pokud `dwKind` je `TYPE_KIND_BUILT`.  
  
 Type.unused  
 Nepoužité odsazení.  
  
 – typ  
 Název sjednocení.  
  
 unionmember  
 [C# pouze] Zařazování tuto hodnotu na typ odpovídající struktury na základě `dwKind`.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předán [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody, kde je vyplněna. Jak interpretovat obsah struktury je založen na `dwKind` pole.  
  
> [!NOTE]
>  [Jenom C++] Pokud `dwKind` rovná `TYPE_KIND_BUILT`, pak je nutné uvolnit základní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objektu při ničení `TYPE_INFO` struktury. To se provádí voláním `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [C# pouze] Následující tabulka ukazuje, jak interpretovat `unionmember` člen pro každý druh typu. Příklad ukazuje, jak to lze provést jednoho druhu typu.  
  
|`dwKind`|`unionmember` interpretováno jako|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak interpretovat `unionmember` člena `TYPE_INFO` struktura v jazyce C#. Tento příklad ukazuje interpretace pouze jeden typ (`TYPE_KIND_METADATA`) ale ostatní jsou interpretovány stejným způsobem.  
  
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
 Záhlaví: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)

