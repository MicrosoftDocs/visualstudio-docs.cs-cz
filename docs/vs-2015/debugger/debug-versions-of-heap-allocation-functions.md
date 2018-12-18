---
title: Ladění verzí funkcí přidělení haldy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7a649d8afd3ae7bf7d6d9abff98734ac96e05cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802091"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Ladění verzí funkcí přidělení haldy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Knihovny run-time C obsahuje speciální ladění verzí funkcí přidělení haldy. Tyto funkce mají stejné názvy jako vydání verze s _dbg připojí k nim. Toto téma popisuje rozdíly mezi verzi funkce CRT a verze _dbg pomocí `malloc` a `_malloc_dbg` jako příklady.  
  
 Když [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) je definován, CRT mapuje všechny [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) volání [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Proto není potřeba revize kódu pomocí `_malloc_dbg` místo `malloc` získat výhody při ladění.  
  
 Můžete chtít volat `_malloc_dbg` explicitně, ale. Volání `_malloc_dbg` explicitně má některé další výhody:  
  
- Sledování `_CLIENT_BLOCK` zadejte přidělení.  
  
- Ukládání zdrojový soubor a číslo řádku kde došlo k požadavek na přidělení.  
  
  Pokud nechcete převést vaše `malloc` volání `_malloc_dbg`, můžete získat informace o zdrojovém souboru tak, že definujete [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), což způsobí, že preprocesor přímá mapování všech volání `malloc` k `_malloc_dbg` aniž byste museli spoléhat na obálku kolem `malloc`.  
  
  Pokud chcete sledovat samostatné typy přidělení v blocích klienta, musí volat `_malloc_dbg` přímo a nastavte `blockType` parametr `_CLIENT_BLOCK`.  
  
  Když není definovaný _DEBUG, volání `malloc` nejsou narušen, volání `_malloc_dbg` , jsou vyhodnoceny na `malloc`, definice [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) bude ignorována a zdroje týkající se informací o souboru požadavek na přidělení není k dispozici. Protože `malloc` nemá parametr typu blok, žádosti o `_CLIENT_BLOCK` typy se považují za standardní přidělení.  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)



