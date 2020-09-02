---
title: Lexikální hierarchie typů symbolů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70b83046c41b13cb51324eb63e81b26a118a81f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815726"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikální hierarchie typů symbolů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V následující tabulce jsou uvedeny typy symbolů v lexikální hierarchii.  
  
## <a name="symbol-types"></a>Typy symbolů  
  
|Typ symbolu|Popis|  
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
 [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Symboly a značky symbolů](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
