---
title: Iactivescriptprofilercontrol2 –::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571440"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Upozorní profileru, že se chystáte profilování u všech příslušných skriptovacích strojů. Pomocí této metody můžete získat kompletní zásobník volání, pokud se při zastavení profilování spustí [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Profilování nebylo možné spustit.|  
|`S_FALSE`|Profilace byla zastavena, pokud nebyl spuštěn skript.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilace není povolená.|  
  
## <a name="remarks"></a>Poznámky  
 Volání `IActiveScriptProfilerControl2::PrepareProfilerStop` zajistí odeslání událostí pro funkce v zásobníku volání. Tato metoda musí být volána před zastavením profilování na jakémkoli skriptovacím stroji, který je na aktuální kartě. Metodu lze volat pro libovolný skriptovací modul.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 – rozhraní](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)