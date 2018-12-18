---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793416"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Jestli jste spustili profilace na všechny příslušné skriptovacích strojů upozorní profileru. Pomocí této metody můžete získat zásobníku dokončení volání, pokud [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] běží při spuštění profilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Profilace nelze spustit.|  
|`S_FALSE`|Profilace byla spuštěna při skript nebyl spuštěn.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povoleno. Bez zpětného volání již byla nastavena.|  
|`E_OUTOFMEMORY`|Zásobník volání nelze získat z důvodu podmínku nedostatku paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Volání metody `IActiveScriptProfilerControl2::CompleteProfilerStart` zajistí, že se odesílají události pro funkce již v zásobníku volání. Tato metoda má být volána po profilace spouští na jakéhokoli skriptovací stroje, který je na kartě aktuální. Metodu lze volat pro všechny skriptovacího stroje.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Iactivescriptprofilercontrol2 – rozhraní](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)