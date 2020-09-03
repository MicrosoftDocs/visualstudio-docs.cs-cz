---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f37fb773a07291a883f5cb65e4cb4ac840a87a14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198777"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jak interpretovat typ objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 TYPE_KIND_METADATA  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) sjednocení by se mělo interpretovat jako [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktura.  
  
 TYPE_KIND_PDB  
 `TYPE_INFO`Sjednocení by se mělo interpretovat jako struktura [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO`Sjednocení by se mělo interpretovat jako struktura [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) .  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty tohoto výčtu se zobrazí v `dwKind` poli struktury [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) a slouží k určení, jak interpretovat `type` člena sjednocení. `TYPE_INFO`Struktura je vrácena voláním metody [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
