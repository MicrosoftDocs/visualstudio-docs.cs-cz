---
title: IActiveScriptSiteDebug32::GetApplication | Microsoft Docs
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
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793620"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Vrátí objekt ladění aplikace přidružené k této lokalitě skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 [out] Ukazatel na objekt ladění aplikace přidružené k lokalitě skriptu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Hostitel nepodporuje přímo ladění.|  
  
## <a name="remarks"></a>Poznámky  
 `GetApplication` Metoda poskytuje způsob, jak inteligentního hostitele pro daný aplikační objekt, ke kterému patří každý skript zadejte. Skriptovací stroje mají pokusit o volat tuto metodu za účelem získání jeho obsahující aplikaci a uchýlit k `IProcessDebugManager::GetDefaultApplication` Pokud se to nezdaří.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptSiteDebug32 rozhraní](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)