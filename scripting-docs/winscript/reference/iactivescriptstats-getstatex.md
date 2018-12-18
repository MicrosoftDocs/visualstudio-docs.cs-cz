---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793650"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Vrátí statistiku vlastních skriptů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [v] Určuje, které statistiky vrátit. Sémantika statistiky, které odpovídá konkrétní identifikátor GUID je zcela modul definované.  
  
 `pluHi`  
 [out] Vysoká 32bitová verze 64bitová verze celé číslo bez znaménka představující této statistiky.  
  
 `pluLo`  
 [out] Nízkou 32bitová verze 64bitová verze celé číslo bez znaménka představující této statistiky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Metoda není implementována.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje vlastní skriptovací stroj se vraťte do vlastního hostitele smysluplný statistiky.  
  
> [!NOTE]
>  Tato metoda není implementována aktuálně.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Iactivescriptstats – rozhraní](../../winscript/reference/iactivescriptstats-interface.md)