---
title: Inicializace | Microsoft Docs
description: Použijte metodu init () pro VsgDbg k přípravě komponenty v aplikaci diagnostiky grafiky k protokolování informací o grafice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 094f4f3c64570a0af5396e903541c70a919cc0d3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996185"
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
 `vsgLogGetter` Odkazovaná entita – například funkce, ukazatel na funkci, výraz lambda nebo objekt funkce, který přijímá jako parametry délku vyrovnávací paměti složené z `wchar_t` a ukazatel na tuto vyrovnávací paměť a vrátí `void` . Při vyvolání určuje volanou entitu název souboru, který se použije k zaznamenání informací o grafice a před vrácením zapíše do zadané vyrovnávací paměti.

## <a name="remarks"></a>Poznámky
 `Init`Funkce je volána automaticky, pokud `VsgDbg` je instance třídy vytvořena zadáním `bDefaultInit` parametru jeho konstruktoru, `true` v opačném případě `Init` musí být explicitně volána před tím, než bude možné aktivně zachytit a zaznamenat informace o grafice.

 Můžete dokončit a zavřít aktivní soubor protokolu grafiky voláním `UnInit` a pak zachytit a zaznamenat více grafických informací do nového souboru protokolu grafiky voláním metody `Init` . Tuto akci můžete opakovat tolikrát, kolikrát chcete vytvořit několik nezávislých souborů protokolu grafiky pomocí stejné `VsgDbg` instance.

## <a name="see-also"></a>Viz také
- [UnInit](init.md)