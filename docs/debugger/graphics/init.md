---
title: Init | Microsoft Docs
description: Pomocí metody Init() VsgDbg připravte komponentu diagnostiky grafiky v aplikaci pro protokolování informací grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc6732ed506d1aa7e4ac3e47c629aadae796201d
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232372"
---
# <a name="init"></a>Init
Připraví komponentu diagnostiky grafiky v aplikaci k aktivnímu zaznamenání a zaznamenání informací grafiky do souboru protokolu grafiky.

## <a name="syntax"></a>Syntaxe

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametry
 `vsgLogGetter` Volatelná entita – například funkce, ukazatel funkce, lambda nebo objekt funkce – která přebírá jako parametry délku vyrovnávací paměti složené z a ukazatel na tuto vyrovnávací paměť `wchar_t` a vrací `void` . Při vyvolání entita volatelná určuje název souboru, který se použije k zaznamenání informací grafiky, a před vrácením je zapíše do zadané vyrovnávací paměti.

## <a name="remarks"></a>Poznámky
 Funkce je volána automaticky při vytvoření instance třídy zadáním parametru jejího konstruktoru jako . V opačném případě musí být volána explicitně před aktivním zachycením a záznamem informací `Init` `VsgDbg` `bDefaultInit` `true` `Init` grafiky.

 Aktivní soubor protokolu grafiky můžete dokončit a zavřít zavoláním funkce a pak můžete do nového souboru protokolu grafiky zaznamenat a zaznamenat další informace grafiky tím, že `UnInit` ho `Init` zavoláte znovu. Můžete to opakovat tolikrát, kolikrát chcete vytvořit několik nezávislých souborů protokolu grafiky pomocí stejné `VsgDbg` instance.

## <a name="see-also"></a>Viz také
- [UnInit](init.md)