---
title: 'Iactivescriptsiteinterruptpoll –:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572235"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Umožňuje hostiteli určit, že se má skript ukončit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Volání bylo úspěšné a hostitel povoluje, aby skript pokračoval v běhu.|  
|`S_FALSE`|Volání bylo úspěšné a hostitel požaduje ukončení skriptu.|  
  
## <a name="remarks"></a>Poznámky  
 Hostovaný skript by měl skončit, pokud není vrácena návratová hodnota metody `QueryContinue` `S_OK`. Návratová hodnota `S_FALSE` označuje, že hostitel explicitně požaduje ukončení skriptu.  
  
 Hostitel s více vlákny může použít metodu `IActiveScript::InterruptScriptThread` k ukončení skriptu.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptsiteinterruptpoll –](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)