---
title: Symboly a značky symbolů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67fbe790eaded11806f1ca1fbfcaaeee38a36116
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732194"
---
# <a name="symbols-and-symbol-tags"></a>Symboly a značky symbolů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Informace o ladění o zkompilovaný program je uloženo v souboru databáze (PDB) programu jako symboly, které jsou přístupné pomocí rozhraní API sady SDK pro přístup k rozhraní ladění (DIA). Mají všechny symboly [idiasymbol::get_symtag –](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) a [idiasymbol::get_symindexid –](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) vlastnost. `symTag` Vlastnost označuje druh symbolu podle definice [symtagenum – výčet](../../debugger/debug-interface-access/symtagenum.md) výčtu. `symIndexId` Je vlastnost `DWORD` hodnotu, která obsahuje jedinečný identifikátor pro každou instanci symbolu.  
  
 Symboly také mít vlastnosti, které můžete zadat další informace o symbolu, jakož i odkazy na jiné symboly nejčastěji [idiasymbol::get_lexicalparent –](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) nebo [idiasymbol::get_classparent –](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Když odešlete dotaz na vlastnost, která obsahuje odkaz, odkaz se vrátí jako [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objektu. Tyto vlastnosti jsou vždy spárovaná s jinou vlastnost se stejným názvem, ale příponami "ID", například [idiasymbol::get_lexicalparentid –](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) a [idiasymbol::get_classparentid –](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabulky v [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md), [lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), a [hierarchie typů symbolů tříd](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) popisují vlastnosti pro každý z různých typů z symboly. Důležité informace o nebo odkazy na jiné symboly, může mít tyto vlastnosti. Vzhledem k tomu, `*Id` jednoduše číselného pořadí identifikátory jejich související vlastnosti jsou vlastnosti, jsou vynechány z další diskuse. Označujeme je pouze v případě potřeby pro parametr vyjasnění.  
  
 Při pokusu o přístup k vlastnosti, pokud nedojde k žádné chybě a symbol vlastnost má přiřazenou hodnotu, je vlastnost "get" vrátí metoda `S_OK`. Vrácená hodnota `S_FALSE` znamená, že vlastnost není platná pro aktuální symbol.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)  
 Popisuje různé druhy umístění, které může mít symbol.  
  
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Popisuje typy symbolů, které tvoří lexikální hierarchie, jako jsou soubory, moduly a funkce.  
  
 [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Popisuje typy symbolů, které odpovídají různé jazykové prvky, jako je tříd, polí a funkce návratové typy.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k rozhraní ladění SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)



