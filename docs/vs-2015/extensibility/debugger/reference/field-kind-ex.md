---
title: FIELD_KIND_EX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c56d41dcc7ebbdb8565ff265c88e33aef095abc6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729239"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří výčet další typy polí, která [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objekt může obsahovat. Tento výčet rozšiřuje [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```csharp  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## <a name="members"></a>Členové  
 FIELD_KIND_EX_NONE  
 Pole neobsahuje rozšířeného typu.  
  
 FIELD_TYPE_EX_METHODVAR  
 Pole obsahuje proměnnou metody.  
  
 FIELD_TYPE_EX_CLASSVAR  
 Pole obsahuje proměnné třídy.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)

