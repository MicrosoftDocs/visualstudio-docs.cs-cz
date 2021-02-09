---
title: Inicializace | Microsoft Docs
description: Použijte metodu init () pro VsgDbg k přípravě komponenty v aplikaci diagnostiky grafiky k protokolování informací o grafice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17b2490641a85a9a38bdeb2c5cd20038639de6f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891810"
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