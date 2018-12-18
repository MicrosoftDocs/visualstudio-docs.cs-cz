---
title: IDebugProcessEx2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fa10fb5ebe2f9a78d44997c29ae51bc02e2c842
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934935"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Toto rozhraní umožňuje relace ladění správci upozornění procesu, který je k připojení nebo odpojení od procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Dodavatel port. Tento vlastní port implementuje toto rozhraní na stejný objekt jako [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) rozhraní za účelem:  
  
- Podpora sledování relací, které jsou připojené k procesu  
  
- Podpora automatické připojení napříč více ladicími stroji  
  
  Pokud zvolí dodavatele port. Tento vlastní port toto rozhraní implementovat.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
  
-   Volání SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugProcess2` rozhraní k získání tohoto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugProcessEx2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje o procesu relace je nyní ladění procesu.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje o procesu relace je již ladění procesu.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Přidá uzly programů seznam ladicí stroj.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je privátní mezi SDM a procesu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)