---
title: 'Iactivescriptsitedebug –:: OnScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572202"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Umožňuje inteligentnímu hostiteli určit, jakým způsobem se mají zpracovávat běhové chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 pro Chyba za běhu, ke které došlo  
  
 `pfEnterDebugger`  
 mimo Příznak označující, zda se má předat chyba ladicímu programu pro ladění JIT  
  
 `pfCallOnScriptErrorWhenContinuing`  
 mimo Příznak označující, zda se má volat `IActiveScriptSite::OnScriptError`, když se uživatel rozhodne pokračovat bez ladění  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují, ale nejsou omezeny na hodnotu v následující tabulce.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Inteligentní hostitel může tuto metodu použít k určení způsobu zpracování chyb za běhu.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSiteDebug – rozhraní](../../winscript/reference/iactivescriptsitedebug-interface.md)