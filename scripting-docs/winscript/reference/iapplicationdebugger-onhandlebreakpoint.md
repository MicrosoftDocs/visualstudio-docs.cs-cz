---
title: 'Iapplicationdebugger –:: onHandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577833"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Zpracovává událost zarážky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prpt`  
 pro Vlákno, kde došlo k zarážce.  
  
 `br`  
 pro Důvod pro zarážku.  
  
 `pError`  
 pro Informace o běhové chybě, pokud je hodnota `br` BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když je dosaženo zarážky a je volána `IDebugApplication::HandleBreakPoint`.  
  
 Aplikace zůstane pozastavena, dokud rozhraní IDE ladicího programu nevolá `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iapplicationdebugger –](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication –:: HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)    
 [Iremotedebugapplication –:: ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)    
 [BREAKREASON – výčet](../../winscript/reference/breakreason-enumeration.md)