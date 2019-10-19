---
title: 'Iremotedebugapplication –:: ResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577463"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Pokračuje v aplikaci, která je aktuálně v zarážce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prptFocus`  
 pro V případě režimů krokování je vlákno ovlivněné režimem krokování.  
  
 `bra`  
 pro Akce, která se má provést při obnovení aplikace  
  
 `era`  
 pro Akce, která má být provedena v případě, že aplikace byla zastavena z důvodu chyby.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda pokračuje v aplikaci, která je aktuálně v zarážce.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iremotedebugapplication –](../../winscript/reference/iremotedebugapplication-interface.md)  
 @No__t_1 [výčtu breakresumeaction –](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION – výčet](../../winscript/reference/errorresumeaction-enumeration.md)