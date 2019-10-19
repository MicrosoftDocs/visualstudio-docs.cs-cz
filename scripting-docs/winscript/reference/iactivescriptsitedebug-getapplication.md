---
title: 'Iactivescriptsitedebug –:: getapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2ad81e3b6b1707f5a23271cf0abe3832266c07f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570117"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
 @No__t_1 [rozhraní iactivescriptsitedebug –](../../winscript/reference/iactivescriptsitedebug-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)