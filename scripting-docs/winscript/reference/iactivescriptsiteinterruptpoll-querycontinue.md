---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793677"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Umožňuje hostitele k určení, že by měl skript ukončen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Volání úspěšné a hostitele umožňuje skript, který chcete-li pokračovat v práci.|  
|`S_FALSE`|Volání úspěšné a hostitele požadavků, které skript ukončen.|  
  
## <a name="remarks"></a>Poznámky  
 Hostované skript by měl ukončení, pokud vrátí hodnotu, která `QueryContinue` je metoda `S_OK`. Vrácená hodnota `S_FALSE` označuje, že hostitel výslovně požaduje, aby skript ukončen.  
  
 Hostitel s více vlákny mohou používat `IActiveScript::InterruptScriptThread` metoda ukončit skript.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsiteinterruptpoll – rozhraní](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)