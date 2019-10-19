---
title: 'IActiveScriptSiteDebug32:: getapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572196"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32:: getapplication
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
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Hostitel přímo nepodporuje ladění.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetApplication` poskytuje inteligentnímu hostiteli způsob, jakým má definovat objekt aplikace, ke kterému každý skript patří. Skriptovací stroje by se měly pokusit zavolat tuto metodu a získat tak jejich obsahující aplikaci a využít `IProcessDebugManager::GetDefaultApplication`, pokud se to nepovede.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)