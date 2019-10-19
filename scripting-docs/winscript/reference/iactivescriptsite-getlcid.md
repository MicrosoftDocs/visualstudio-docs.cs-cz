---
title: 'IActiveScriptSite:: getlcid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570737"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Načte identifikátor národního prostředí přidružený k uživatelskému rozhraní hostitele. Skriptovací stroj používá identifikátor k zajištění toho, aby řetězce chyb a jiné prvky uživatelského rozhraní generované modulem byly zobrazeny v příslušném jazyce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `plcid`  
 mimo Adresa proměnné, která přijímá identifikátor národního prostředí pro prvky uživatelského rozhraní zobrazené skriptovacím modulem.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_NOTIMPL`|Tato metoda není implementována. Použijte národní prostředí definované systémem.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato metoda vrátí `E_NOTIMPL`, měl by být použit identifikátor národního prostředí definovaný systémem.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)