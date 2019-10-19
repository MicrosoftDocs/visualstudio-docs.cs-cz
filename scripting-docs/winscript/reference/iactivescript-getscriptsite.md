---
title: 'IActiveScript:: GetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575749"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Načte objekt lokality přidružený ke skriptovacímu stroji Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 pro Identifikátor požadovaného rozhraní  
  
 `ppvSiteObject`  
 mimo Adresa umístění, které přijímá ukazatel rozhraní, do objektu lokality hostitele.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_NOINTERFACE`|Zadané rozhraní není podporováno.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`S_FALSE`|Není nastaven žádný web; parametr `ppvSiteObject` je nastaven na hodnotu `NULL`.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)