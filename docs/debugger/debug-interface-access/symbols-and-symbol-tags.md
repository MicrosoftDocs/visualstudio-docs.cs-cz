---
title: Symboly a značky symbolů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f4cb4b6ed35e880e1cb26980420f4e951ffc16
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471217"
---
# <a name="symbols-and-symbol-tags"></a>Symboly a značky symbolů
Informace o ladění o kompilované programu je uložené v souboru databáze (.pdb) program jako symboly, které jsou dostupné, pomocí rozhraní API sady SDK ladění rozhraní přístup (DIA). Mají všechny symboly [idiasymbol::get_symtag –](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) a [idiasymbol::get_symindexid –](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) vlastnost. `symTag` Vlastnost určuje typ symbolu podle definice [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md) výčtu. `symIndexId` Vlastnost je `DWORD` hodnotu, která obsahuje jedinečný identifikátor pro všechny instance symbolu.  
  
 Symboly mít také vlastnosti, které můžete zadat další informace o symbol, jakož i odkazy na symboly dalších nejčastěji [idiasymbol::get_lexicalparent –](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) nebo [idiasymbol::get_classparent –](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Když dotazujete vlastnost, která obsahuje odkaz, odkaz se vrátí jako [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objektu. Tyto vlastnosti jsou vždy spárovaný s jinou vlastnost se stejným názvem, ale vyznačeno s "Id", například [idiasymbol::get_lexicalparentid –](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) a [idiasymbol::get_classparentid –](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabulky v [umístění symbolu](../../debugger/debug-interface-access/symbol-locations.md), [lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), a [Symbol typy tříd hierarchie](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) popisují vlastnosti pro každou z různých druhů z symboly. Důležité informace o nebo odkazy na další symboly, může mít tyto vlastnosti. Protože `*Id` vlastnosti jsou jednoduše číselného pořadí identifikátory jejich souvisejících vlastností, byly vynechány z další diskusí. Budou se označují pouze tehdy, pokud potřebné informace parametr.  
  
 Při pokusu o přístup k vlastnosti, pokud nedojde k žádné chybě a vlastnost symbol má přiřazenou hodnotu vlastnosti "get", metoda vrátí `S_OK`. Vrácená hodnota `S_FALSE` označuje, že vlastnost není platná pro aktuální symbol.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)  
 Popisuje různé druhy umístění, které může mít symbol.  
  
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Popisuje typy symbolu, které tvoří lexikální hierarchie, jako jsou soubory, moduly a funkce.  
  
 [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Popisuje typy symbolu, které odpovídají prvkům jiným jazykem, jako je tříd, pole a funkce návratové typy.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k rozhraní ladění SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)