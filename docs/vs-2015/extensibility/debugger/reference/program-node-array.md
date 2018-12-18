---
title: PROGRAM_NODE_ARRAY | Dokumentace Microsoftu
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
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b04e784db657567d1b6d88c1d3a1d7f882d663a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779213"
---
# <a name="programnodearray"></a>PROGRAM_NODE_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obsahuje pole objektů, které popisují programy, které vás zajímají.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagPROGRAM_NODE_ARRAY {  
   DWORD                dwCount;  
   IDebugProgramNode2** Members;  
} PROGRAM_NODE_ARRAY;  
```  
  
```csharp  
public struct tagPROGRAM_NODE_ARRAY {  
   public uint                 dwCount;  
   public IDebugProgramNode2[] Members;  
}  
```  
  
## <a name="members"></a>Členové  
 dwCount  
 Počet objektů v `Members` pole.  
  
 Členové  
 Pole [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) popisující programy požadované objekty.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je součástí [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struktury, což zase je vyplněna voláním [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

