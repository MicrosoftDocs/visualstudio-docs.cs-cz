---
title: 'Iapplicationdebugger –:: onDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577866"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Zpracovává vlastní událost aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 pro Identifikátor rozhraní pro objekt.  
  
 `punk`  
 pro Objekt události, který implementuje rozhraní definované `riid`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Metoda není aktuálně implementována.|  
  
## <a name="remarks"></a>Poznámky  
 Sémantika `IUnknown` je definována výhradně pro aplikace/ladicí program.  
  
 Tato metoda umožňuje vlastní rozšíření modelu ladicího programu. v tuto chvíli není naimplementovaná.  
  
 Tato metoda je volána, když je volána `IDebugApplication::FireDebuggerEvent`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iapplicationdebugger –](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)