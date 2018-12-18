---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793605"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Umožňuje určit, jak se budou zpracovávat chyby spuštění inteligentního hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [v] Chyba při spuštění, který došlo k chybě  
  
 `pfEnterDebugger`  
 [out] Příznak, která určuje, zda mají být předány ladicí program na provádět ladění JIT k chybě.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Příznak označující, zda má být volána `IActiveScriptSite::OnScriptError` když se uživatel rozhodne pro pokračování bez ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty patří, ale nejsou omezeny pouze na hodnotu v následující tabulce.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu můžete určit, jak se budou zpracovávat chyby spuštění použít inteligentního hostitele.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsitedebug – rozhraní](../../winscript/reference/iactivescriptsitedebug-interface.md)