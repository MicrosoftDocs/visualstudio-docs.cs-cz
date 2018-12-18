---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793995"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Způsobí, že aktuální vlákno blokování a odešle oznámení bod přerušení ladicího programu IDE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `br`  
 [v] Důvod pro rozdělení.  
  
 `pbra`  
 [out] Akce se má provést při ladicího programu obnoví aplikace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Modul jazyka volá tuto metodu v kontextu vlákno, které dotkne zarážky. Tato metoda blokuje aktuální vlákno a odešle oznámení zarážek ladicího programu IDE. Když ladicí program obnoví aplikace, `pbra` parametr určuje, jaká opatření se mají provést.  
  
> [!NOTE]
>  Jazyk modul může volat vláken provádění úkolů, například jako zobrazení výčtu zásobníku snímky nebo vyhodnocení výrazů během zarážku.  
  
 Způsobí, že tato metoda `IApplicationDebugger::onHandleBreakPoint` k volání.  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplication – rozhraní](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON – výčet](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION – výčet](../../winscript/reference/breakresumeaction-enumeration.md)