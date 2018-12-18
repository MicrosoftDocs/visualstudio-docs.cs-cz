---
title: IActiveScriptSite::GetLCID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793542"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Načte identifikátor národního prostředí spojené s uživatelským rozhraním hostitele. Skriptovací stroj používá k zajištění, že chyba řetězce a další prvky uživatelského rozhraní generované modulem se objeví v příslušné jazykové identifikátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `plcid`  
 [out] Adresa proměnné, která přijímá identifikátor národního prostředí pro prvky uživatelského rozhraní zobrazuje skriptovacího stroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_NOTIMPL`|Tato metoda není implementována. Použijte národní prostředí definovaná systémem.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato metoda vrátí hodnotu `E_NOTIMPL`, by měl použít identifikátor národního prostředí definovaná systémem.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)