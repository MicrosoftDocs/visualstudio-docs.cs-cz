---
title: 'IDebugApplication –:: HandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574965"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Způsobí, že aktuální vlákno zablokuje a pošle oznámení o zarážce do rozhraní IDE ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `br`  
 pro Důvod pro přerušení  
  
 `pbra`  
 mimo Akce, která se má provést, když ladicí program obnoví aplikaci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Jazykový modul volá tuto metodu v kontextu vlákna, které narazí na zarážku. Tato metoda zablokuje aktuální vlákno a pošle oznámení o zarážce do IDE ladicího programu. Když ladicí program obnoví aplikaci, parametr `pbra` určuje, jakou akci chcete provést.  
  
> [!NOTE]
> Modul jazyka může být volán vláknem k provádění úloh, jako je například zobrazení výčtu rámců zásobníku nebo vyhodnocování výrazů během zarážky.  
  
 Tato metoda způsobí, že `IApplicationDebugger::onHandleBreakPoint` být volána.  
  
## <a name="see-also"></a>Viz také:  
   [rozhraní IDebugApplication –](../../winscript/reference/idebugapplication-interface.md)  
 [Iapplicationdebugger –:: onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
   [výčtu breakreason –](../../winscript/reference/breakreason-enumeration.md)  
 [BREAKRESUMEACTION – výčet](../../winscript/reference/breakresumeaction-enumeration.md)