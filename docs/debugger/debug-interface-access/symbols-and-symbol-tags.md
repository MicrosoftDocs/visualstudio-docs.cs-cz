---
title: Symboly a značky symbolů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738522"
---
# <a name="symbols-and-symbol-tags"></a>Symboly a značky symbolů
Ladicí informace o kompilovaném programu jsou uloženy v souboru databáze programu (PDB) jako symboly, které jsou přístupné pomocí rozhraní API sady SDK přístup k rozhraní ladění (DIA). Všechny symboly mají vlastnost [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) a [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . Vlastnost `symTag` určuje druh symbolu definovaný výčtem [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) . Vlastnost `symIndexId` je `DWORD` hodnota, která obsahuje jedinečný identifikátor pro všechny instance symbolu.

 Symboly také mají vlastnosti, které mohou zadat další informace o symbolu a také odkazy na jiné symboly, nejčastěji [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) nebo [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Při dotazování na vlastnost, která obsahuje odkaz, je odkaz vrácen jako objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Tyto vlastnosti jsou vždycky spárovány s jinou vlastností se stejným názvem, ale mají příponu "ID", například [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) a [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabulky v [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md), [lexikální hierarchii typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)a [hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) mají přehled o vlastnostech pro každý z různých druhů symbolů. Tyto vlastnosti mohou mít relevantní informace o jiných symbolech nebo odkazy na ně. Vzhledem k tomu, že vlastnosti `*Id` jsou jednoduše numerické řadové identifikátory jejich souvisejících vlastností, jsou vynechány z dalších diskusí. Jsou odkazovány pouze tam, kde je to nutné pro objasnění parametru.

 Pokud při pokusu o přístup k vlastnosti dojde k žádné chybě a k vlastnosti symbolu byla přiřazena hodnota, vrátí metoda get `S_OK`. Návratová hodnota `S_FALSE` značí, že vlastnost není platná pro aktuální symbol.

## <a name="in-this-section"></a>V tomto oddílu

[Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)

Popisuje různé druhy umístění, které může mít symbol.

[Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Popisuje typy symbolů, které tvoří lexikální hierarchie, jako jsou soubory, moduly a funkce.

[Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Popisuje typy symbolů, které odpovídají různým prvkům jazyka, jako jsou třídy, pole a návratové typy funkcí.

## <a name="see-also"></a>Viz také:

- [Přístup k rozhraní ladění SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)