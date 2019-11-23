---
title: 'IDebugApplication –:: HandleRuntimeError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574323"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Způsobí, že aktuální vlákno zablokuje a pošle oznámení o chybě do integrovaného vývojového prostředí (IDE) ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 pro Chyba, ke které došlo.  
  
 `pScriptSite`  
 pro Skriptovací lokalita vlákna.  
  
 `pbra`  
 mimo Akce, která se má provést, když ladicí program obnoví aplikaci.  
  
 `perra`  
 mimo Akce, která se má provést, když ladicí program obnoví aplikaci, pokud dojde k chybě.  
  
 `pfCallOnScriptError`  
 mimo Příznak, který je `TRUE`, pokud má modul zavolat metodu `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Jazykový modul volá tuto metodu v kontextu vlákna, které způsobuje chybu za běhu. Tato metoda způsobí, že aktuální vlákno zablokuje a pošle oznámení o chybách k odeslání do rozhraní IDE ladicího programu. Když rozhraní IDE ladicího programu obnoví aplikaci, vrátí tato metoda s akcí, která má být provedena.  
  
> [!NOTE]
> V běhové chybě může být modul jazyka volán vláknem k provádění úkolů, jako je například zobrazení výčtu rámců zásobníku nebo vyhodnocení výrazů.  
  
## <a name="see-also"></a>Viz také:  
   [rozhraní IDebugApplication –](../../winscript/reference/idebugapplication-interface.md)  
   [rozhraní IActiveScriptErrorDebug –](../../winscript/reference/iactivescripterrordebug-interface.md)  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
   [výčtu breakresumeaction –](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION – výčet](../../winscript/reference/errorresumeaction-enumeration.md)