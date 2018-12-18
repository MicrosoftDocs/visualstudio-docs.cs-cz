---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793515"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Volá se při každém profilace zastavení na skriptovací stroj informovat objekt profileru. Tímto způsobem objekt profileru můžete volat jeho čištění rutiny, v případě potřeby. Tato metoda je volána také skriptovací stroj, když se vypíná skriptovací stroje, nebo když volání [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) selže.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hrReason`  
 [v] Z důvodu ukončení aplikace. Pokud se vypíná skriptovací stroje, `S_OK` je předán. Pokud volání [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) vrátí selhání HRESULT, je předaná hodnota HRESULT. Jinak, tato hodnota je načtena z [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota tato metoda je ignorován v skriptovacího stroje.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptprofilercallback – rozhraní](../../winscript/reference/iactivescriptprofilercallback-interface.md)