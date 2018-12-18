---
title: IDebugDefaultPort2::GetPortNotify | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb21f020f6a470b9fded56939987f0a03333206
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872732"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Tato metoda načte [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) rozhraní pro tento port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppPortNotify`  
 [out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Za normálních okolností `QueryInterface` metoda je volána při implementaci objektu [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) rozhraní získat [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) rozhraní. Nicméně existují okolnosti, ve kterých požadované rozhraní je implementováno na jiný objekt. Tato metoda skrývá situace a vrátí `IDebugPortNotify2` rozhraní z objektu nejvhodnější.  
  
## <a name="see-also"></a>Viz také  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)