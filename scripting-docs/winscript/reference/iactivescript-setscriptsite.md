---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575333"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informuje skriptovací stroj lokality rozhraní [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) poskytované hostitelem. Tuto metodu volejte před použitím jakékoli jiné metody rozhraní [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pScriptSite`  
 pro Adresa hostitelského skriptovacího serveru, který má být přidružen k této instanci skriptovacího modulu. Lokalita musí být jednoznačně přiřazena této instanci skriptovacího stroje; nedá se sdílet s jinými skriptovacími moduly.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_FAIL`|Došlo k neurčené chybě. skriptovacímu stroji se nepovedlo dokončit inicializaci lokality.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například web již byl nastaven).|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)