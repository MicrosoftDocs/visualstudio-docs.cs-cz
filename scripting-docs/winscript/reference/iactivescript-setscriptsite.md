---
title: IActiveScript::SetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793263"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informuje o skriptovací stroje systému [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) rozhraní lokality od hostitele. Volat tuto metodu před všemi ostatními [IActiveScript –](../../winscript/reference/iactivescript.md) metody rozhraní se používá.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pScriptSite`  
 [v] Adresa webu hostitele zadaný skript má být přidružena k této instanci skriptovacího stroje. Webu musí být jedinečně přiřazeny k této instanci skriptovací stroj; nemohou být sdíleny s další skriptovací stroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_FAIL`|Došlo k neurčené chybě; Skriptovací stroj se nepodařilo dokončit inicializace webu.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například lokality již byl nastaven).|  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)