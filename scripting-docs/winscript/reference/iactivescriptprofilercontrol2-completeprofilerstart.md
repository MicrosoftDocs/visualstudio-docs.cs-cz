---
title: 'Iactivescriptprofilercontrol2 –:: CompleteProfilerStart | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571552"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Upozorňuje profileru, že jste spustili profilaci pro všechny příslušné skriptovací moduly. Pomocí této metody můžete získat kompletní zásobník volání, pokud při spuštění profilace spustíte [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Profilaci nelze spustit.|  
|`S_FALSE`|Profilace byla spuštěna, když nebyl spuštěn skript.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povolená. Nebylo nastaveno žádné zpětné volání.|  
|`E_OUTOFMEMORY`|Zásobník volání nelze získat z důvodu stavu mimo paměť.|  
  
## <a name="remarks"></a>Poznámky  
 Volání `IActiveScriptProfilerControl2::CompleteProfilerStart` zajišťuje odeslání událostí pro funkce, které jsou již v zásobníku volání. Tuto metodu je třeba volat po zahájení profilace na jakémkoli skriptovacím stroji, který je na aktuální kartě. Metodu lze volat pro libovolný skriptovací modul.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 – rozhraní](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)