---
title: 'Iactivescriptprofilercallback –:: Shutdown | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571655"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Volá se, aby se informoval objekt profileru, když se profilování zastaví na skriptovacím stroji. Tímto způsobem může objekt profileru volat své rutiny pro čištění v případě potřeby. Tato metoda je také volána skriptovacím modulem, když se vypíná skriptovací stroj nebo když volání [iactivescriptprofilercallback –:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) neproběhne úspěšně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hrReason`  
 pro Důvod vypnutí. Pokud se skriptovací modul vypíná, `S_OK` se předává. Pokud volání metody [iactivescriptprofilercallback –:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) vrátí chybu HRESULT, je předána hodnota HRESULT. V opačném případě se tato hodnota načte z [IActiveScriptProfilerControl:: StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Skriptovací stroj ignoruje vrácenou hodnotu této metody.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerCallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)