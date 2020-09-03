---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad4b6a06a2a145daa85d780f4d23dfac9bebf7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205102"
---
# <a name="pdb_type"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato struktura určuje informace o typu pole pořízených ze symbolu PDB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 ulAppDomainID  
 ID aplikace, ze které byl symbol dodán Slouží k jednoznačné identifikaci instance aplikace.  
  
 guidModule  
 Identifikátor GUID modulu, který obsahuje toto pole.  
  
 symid  
 ID symbolu, který odpovídá tomuto poli.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura se zobrazí jako součást sjednocení ve struktuře [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , pokud `dwKind` `TYPE_INFO` je pole struktury nastaveno na `TYPE_KIND_PDB` hodnotu (hodnota z výčtu [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
