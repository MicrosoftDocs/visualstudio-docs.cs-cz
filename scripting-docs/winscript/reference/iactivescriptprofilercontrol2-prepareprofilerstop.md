---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793431"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Jestli chcete zastavit profilování na všechny příslušné skriptovacích strojů upozorní profileru. Pomocí této metody můžete získat zásobníku dokončení volání, pokud [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] běží při zastavení profilování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Profilace se nepodařilo spustit.|  
|`S_FALSE`|Profilace byla zastavena, když skript nebyl spuštěn.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povoleno.|  
  
## <a name="remarks"></a>Poznámky  
 Volání metody `IActiveScriptProfilerControl2::PrepareProfilerStop` zajistí, že se odesílají události pro funkce v zásobníku volání. Tato metoda je volána před provedením zastavit profilování v jakéhokoli skriptovací stroje, který je na kartě aktuální. Metodu lze volat pro všechny skriptovacího stroje.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Iactivescriptprofilercontrol2 – rozhraní](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)