---
title: Lexikální hierarchie typů symbolů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d1c9284637be43ab30d35d3e0cb4aea937c0a224
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853252"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikální hierarchie typů symbolů
V následující tabulce jsou uvedeny typy symbolů v lexikální hierarchii.

## <a name="symbol-types"></a>Typy symbolů

|Typ symbolu|Description|
|-----------------|-----------------|
|[Poznámka](../../debugger/debug-interface-access/annotation.md)|Určuje umístění s poznámkami v kódu programu.|
|[Blok](../../debugger/debug-interface-access/block.md)|Určuje vnořené obory ve funkcích.|
|`Compiland`|Určuje `compiland` odkaz na soubor. exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Určuje kompilantu data, která mohou vyžadovat načtení dalších podrobností kompilantu, a tím zaplatí zatížení za běhu.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Určuje další proměnné prostředí, které jsou významné pro kompilaci kompilantu.|
|[Vlastní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Určuje uživatelsky definovaný symbol.|
|[Data (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Určuje proměnné jako parametry, místní proměnné, globální proměnné a členy třídy.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Určuje globální rozsah dat. odpovídá celému souboru. exe nebo. dll.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Určuje funkci, která má definovaný bod, na kterém je ladění ukončeno.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Určuje funkci, která má definovaný bod, na kterém má být zahájeno ladění.|
|[Funkce (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Určuje funkci.|
|[Popisek (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Určuje umístění v kódu programu.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Určuje externí symbol, který se zobrazí při vytváření spustitelného programu.|
|[Převod](../../debugger/debug-interface-access/thunk.md)|Určuje `thunk` .|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Určuje `namespace` identifikátor.|

> [!NOTE]
> V závislosti na typu symbolu mohou být k dispozici další vlastnosti symbolu. Tyto vlastnosti jsou uvedeny v tématech jednotlivých symbolů.

## <a name="see-also"></a>Viz také
- [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Symboly a značky symbolů](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)