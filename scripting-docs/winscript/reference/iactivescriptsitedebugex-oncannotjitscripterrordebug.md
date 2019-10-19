---
title: 'Iactivescriptsitedebugex –:: OnCanNotJITScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572179"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informuje hostitele o chybě za běhu skriptu, když správce ladění procesu nenalezne ladicí program skriptu přesně v čase.  
  
 Chcete-li implementovat ladicí program na hostitele, měli byste zpracovat [iactivescriptsitedebug –:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Na základě akce uživatele může hostitel buď připojit ladicí program a vrátit se, nebo vrátit začátek ladicího programu v parametru OnScriptErrorDebug `pfEnterDebugger`. Toto rozhraní byste měli taky implementovat, aby se zobrazilo oznámení o chybě za běhu i v případě, že neexistují externí ladicí programy, které by bylo možné interpretovat pomocí Správce ladění procesů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 pro Došlo k chybě za běhu.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 mimo Určuje, zda má být volána možnost [iactivescriptsitedebug –:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) , pokud se uživatel rozhodne pokračovat bez ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní byste měli taky implementovat, aby se zobrazilo oznámení.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSiteDebugEx – rozhraní](../../winscript/reference/iactivescriptsitedebugex-interface.md)