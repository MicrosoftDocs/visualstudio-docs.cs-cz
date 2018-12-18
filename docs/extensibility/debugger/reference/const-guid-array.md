---
title: CONST_GUID_ARRAY | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b66713fa5929fc1397a5302732399c07c3f5a726
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885912"
---
# <a name="constguidarray"></a>CONST_GUID_ARRAY
Struktura, která obsahuje seznam `GUID`s.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```csharp  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## <a name="members"></a>Členové  
 dwCount  
 Počet `GUID`ve `Members` pole.  
  
 Členové  
 Pole `GUID`s.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je předán [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metoda a vrátí [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) a [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) metody.  
  
 Vlastníka instance této struktury je zodpovědná za uvolnění přidělení paměti.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)