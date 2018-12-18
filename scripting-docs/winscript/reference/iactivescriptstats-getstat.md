---
title: IActiveScriptStats::GetStat | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793716"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Vrací jednu ze statistiky standardní skripty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stid`  
 [v] Určuje, které statistiky vrátit. Hodnota musí být:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Vrátí počet příkazy provést, protože spuštění skriptu nebo statistiky byly obnoveny.|  
  
 `pluHi`  
 [out] Vysoká 32bitová verze 64bitová verze celé číslo bez znaménka představující této statistiky.  
  
 `pluLo`  
 [out] Nízkou 32bitová verze 64bitová verze celé číslo bez znaménka představující této statistiky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty patří, ale nejsou omezeny pouze na hodnoty v následující tabulce.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací jednu ze statistiky standardní skripty.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Iactivescriptstats – rozhraní](../../winscript/reference/iactivescriptstats-interface.md)