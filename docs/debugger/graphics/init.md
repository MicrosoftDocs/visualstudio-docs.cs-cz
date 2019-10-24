---
title: Inicializace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735008"
---
# <a name="init"></a>Init
Připraví komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání grafických informací do souboru protokolu grafiky.

## <a name="syntax"></a>Syntaxe

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametry
 `vsgLogGetter` vyvolatelné entity, jako je funkce, ukazatel na funkci, lambda nebo objekt funkce, které přebírají jako parametry délku vyrovnávací paměti složené z `wchar_t` a ukazatel na tuto vyrovnávací paměť a vrátí `void`. Při vyvolání určuje volanou entitu název souboru, který se použije k zaznamenání informací o grafice a před vrácením zapíše do zadané vyrovnávací paměti.

## <a name="remarks"></a>Poznámky
 Funkce `Init` je volána automaticky, když je vytvořena instance `VsgDbg` třídy zadáním parametru `bDefaultInit` jeho konstruktoru jako `true`; v opačném případě musí být `Init` explicitně volána, aby bylo možné aktivně zachytit a zaznamenat informace grafiky.

 Můžete dokončit a zavřít soubor protokolu aktivní grafiky voláním `UnInit` a potom zachytit a zaznamenat více grafických informací do nového souboru protokolu grafiky voláním `Init` znovu. Tuto akci můžete opakovat tolikrát, kolikrát chcete vytvořit několik nezávislých grafických souborů protokolu pomocí stejné instance `VsgDbg`.

## <a name="see-also"></a>Viz také:
- [UnInit](init.md)