---
title: IDebugApplication::HandleRuntimeError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793890"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Způsobí, že aktuální vlákno blokování a odešle oznámení chyby ladicího programu IDE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [v] Chyba, k níž došlo.  
  
 `pScriptSite`  
 [v] Lokalita skriptu vlákna.  
  
 `pbra`  
 [out] Akce se má provést při ladicího programu obnoví aplikace.  
  
 `perra`  
 [out] Akce se má provést při ladicího programu pokračuje v aplikaci, pokud dojde k chybě.  
  
 `pfCallOnScriptError`  
 [out] Příznak, který je `TRUE` Pokud modul by měly volat `IActiveScriptSite::OnScriptError` metoda.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Modul jazyka volá tuto metodu v kontextu vláken, která způsobuje chybu běhu. Tato metoda způsobí, že aktuální vlákno blokování a odešle oznámení o chybě pro odeslání do ladicího programu IDE. Když ladicí program IDE obnoví aplikace, tato metoda vrátí s akcí, které mají být provedeny.  
  
> [!NOTE]
>  V průběhu běhu odolnost, může volat modul jazyka vlákno k provedení požadovaných úkolů jako výčet rámce zásobníku nebo vyhodnocení výrazů.  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplication – rozhraní](../../winscript/reference/idebugapplication-interface.md)   
 [Iactivescripterrordebug – rozhraní](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION – výčet](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION – výčet](../../winscript/reference/errorresumeaction-enumeration.md)