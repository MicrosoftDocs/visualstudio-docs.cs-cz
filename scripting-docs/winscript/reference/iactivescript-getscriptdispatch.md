---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575751"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Načte rozhraní `IDispatch` pro metody a vlastnosti přidružené k aktuálně běžícímu skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrItemName`  
 pro Adresa vyrovnávací paměti obsahující název položky, pro kterou volající potřebuje přidružený objekt dispatch. Pokud je tento parametr `NULL`, objekt Dispatch obsahuje jako členy všechny globální metody a vlastnosti definované skriptem. Prostřednictvím rozhraní `IDispatch` a přidruženého rozhraní `ITypeInfo` může hostitel vyvolat metody skriptu nebo zobrazit a upravit proměnné skriptu.  
  
 `ppdisp`  
 mimo Adresa proměnné, která přijímá ukazatel na objekt přidružený k globálním metodám a vlastnostem skriptu. Pokud skriptovací stroj takový objekt nepodporuje, `NULL` se vrátí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
|`S_FALSE`|Skriptovací stroj nepodporuje objekt Dispatch; parametr `ppdisp` je nastaven na hodnotu NULL.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že metody a vlastnosti lze přidat voláním rozhraní [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , může rozhraní `IDispatch` vrácené touto metodou dynamicky podporovat nové metody a vlastnosti. Podobně by metoda `IDispatch::GetTypeInfo` měla vracet nové jedinečné rozhraní `ITypeInfo`, když jsou přidány metody a vlastnosti. Upozorňujeme však, že tyto jazykové moduly nesmí měnit rozhraní `IDispatch` způsobem, který je nekompatibilní s jakýmkoli předchozím vráceným rozhraním `ITypeInfo`. Což implikuje například, že by se identifikátory SPID nikdy znovu nepoužily.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)