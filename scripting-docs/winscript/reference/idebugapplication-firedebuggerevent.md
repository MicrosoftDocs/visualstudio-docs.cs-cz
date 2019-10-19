---
title: 'IDebugApplication –:: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575001"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Aktivuje obecnou událost pro `IApplicationDebugger` rozhraní ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 pro Identifikátor GUID objektu.  
  
 `punk`  
 pro Objekt události, který bude předána ladicímu programu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Metoda není aktuálně implementována.|  
  
## <a name="remarks"></a>Poznámky  
 Sémantika identifikátoru GUID a `IUnknown` jsou definovány pro aplikace/ladicí program.  
  
 Tato metoda umožňuje vlastní rozšíření modelu ladicího programu. v tuto chvíli není naimplementovaná.  
  
 Tato metoda způsobí, že `IApplicationDebugger::onDebuggerEvent` být volána.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IDebugApplication –](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)