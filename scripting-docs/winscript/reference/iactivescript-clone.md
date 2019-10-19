---
title: 'IActiveScript:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575802"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Naklonuje aktuální skriptovací stroj (mínus aktuální stav spuštění) a vrátí načtený skriptovací stroj, který nemá v aktuálním vlákně žádný web. Vlastnosti tohoto nového skriptovacího modulu budou stejné jako vlastnosti, které by původní skriptovací stroj měl v případě, že byl přepnut zpátky do inicializovaného stavu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppscript`  
 mimo Adresa proměnné, která přijímá ukazatel na rozhraní [IActiveScript](../../winscript/reference/iactivescript.md) naklonovaného skriptovacího modulu. Hostitel musí vytvořit lokalitu a volat metodu [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) v novém skriptovacím stroji předtím, než bude v inicializovaném stavu, a proto lze použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_NOTIMPL`|Tato metoda není podporována.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `IActiveScript::Clone` je optimalizace `IPersist*::Save`, `CoCreateInstance` a `IPersist*::Load`, takže stav nového skriptovacího stroje by měl být stejný, jako kdyby byl uložen do nového skriptovacího stroje a byl načten do nového skriptovacího stroje. Pojmenované položky jsou duplikovány v naklonovaném skriptovacím modulu, ale konkrétní ukazatele objektu pro každou položku jsou zapomenuté a jsou získány pomocí metody [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . To umožňuje použít identický objektový model s vstupními body pro vlákno (model Apartment).  
  
 Tato metoda se používá pro hostitele serverů s více vlákny, které mohou spouštět více instancí stejného skriptu. Skriptovací stroj může vracet `E_NOTIMPL`. v takovém případě může hostitel dosáhnout stejného výsledku tak, že duplikuje trvalý stav a vytvoří novou instanci skriptovacího stroje s rozhraním `IPersist*`.  
  
 Tuto metodu lze volat z nezákladních vláken, aniž by došlo k nezákladnímu popisku pro hostování objektů nebo rozhraní [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)