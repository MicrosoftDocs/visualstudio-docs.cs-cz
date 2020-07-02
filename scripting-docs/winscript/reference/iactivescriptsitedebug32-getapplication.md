---
title: 'IActiveScriptSiteDebug32:: getapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835625"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Vrátí objekt aplikace ladění přidružený k tomuto webu skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 mimo Ukazatel na objekt ladění aplikace přidružený k webu skriptu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí `HRESULT` . Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Hostitel přímo nepodporuje ladění.|  
  
## <a name="remarks"></a>Poznámky  
 `GetApplication`Metoda poskytuje způsob, jak může inteligentní hostitel definovat objekt aplikace, ke kterému každý skript patří. Skriptovací stroje by se měly pokusit zavolat tuto metodu a získat tak jejich obsahující aplikaci a využít tak, `IProcessDebugManager::GetDefaultApplication` že se nezdaří.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)