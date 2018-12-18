---
title: IActiveScript::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791997"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Provede klonování aktuální skriptovacího stroje (minus všechny aktuální stav provádění), vrácení načíst skriptovací stroj, který má žádná lokalita v aktuální vlákno. Vlastnosti tohoto nového skriptovacího stroje se bude shodovat s vlastnostmi, které by bylo původní skriptovacího stroje v Pokud byly přešla do inicializovaný stav.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppscript`  
 [out] Adresy proměnné, která přijímá ukazatel na [IActiveScript –](../../winscript/reference/iactivescript.md) rozhraní klonovaný skriptovací stroje. Hostitel musí vytvořit lokality a volání [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) metodu nového skriptovacího stroje předtím, než bude inicializovaný stav a tedy použitelné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_NOTIMPL`|Tato metoda není podporována.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
  
## <a name="remarks"></a>Poznámky  
 `IActiveScript::Clone` Je metoda optimalizace `IPersist*::Save`, `CoCreateInstance`, a `IPersist*::Load`, takže stav nového skriptovacího stroje musí být stejná jako v případě, že stav původní skriptovací stroje byly uložit a načtena do nového skriptovacího stroje. Pojmenované položky jsou duplicitní v rámci klonovaný skriptovací stroje, ale ukazatele určitý objekt pro každou položku jsou zapomenete a jsou získány s [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metoda. To umožňuje identické objektový model s vlákno vstupní body (apartment model) má být použit.  
  
 Tato metoda se používá pro vícevláknové serveru hostitele, které můžete spustit více instancí stejného skriptu. Skriptovací stroj může vrátit `E_NOTIMPL`, v takovém případě hostitele dosažení stejného výsledku duplikováním trvalý stav a vytvoření nové instance skriptovací stroje s `IPersist*` rozhraní.  
  
 Tuto metodu lze volat z vlákna není základní bez výsledkem není základní popisku na objekty hostitele nebo na [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)