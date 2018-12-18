---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793656"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informuje o tom, že hostitel o Chyba spuštění skriptu proces ladění Manager nenajde ladicí program pouze v době skriptu.  
  
 K implementaci ladicí program na hostiteli, by měl zpracovat [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Založená na akci uživatele, hostiteli můžete buď připojit ladicí program a vrátí nebo vrátit počáteční v ladicím programu OnScriptErrorDebug `pfEnterDebugger` parametr. Měli byste také implementovat tohoto rozhraní dostávat oznámení o chybě spuštění i v případě, že neexistují žádné externí ladicí programy, které můžete interpretovat pomocí procesu ladění správce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [v] Chyba spuštění, který došlo k chybě.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Jestli se má volat [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) Pokud se uživatel rozhodne pro pokračování bez ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Měli byste také implementovat toto rozhraní získat oznámení.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsitedebugex – rozhraní](../../winscript/reference/iactivescriptsitedebugex-interface.md)