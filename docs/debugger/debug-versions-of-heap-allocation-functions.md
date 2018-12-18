---
title: Ladění verzí funkcí přidělení haldy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12b997b2aeb2b34305eafc2dc478460d9f450677
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941463"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Ladění verzí funkcí přidělení haldy
Knihovny run-time C obsahuje speciální ladění verzí funkcí přidělení haldy. Tyto funkce mají stejné názvy jako vydání verze s _dbg připojí k nim. Toto téma popisuje rozdíly mezi verzi funkce CRT a verze _dbg pomocí `malloc` a `_malloc_dbg` jako příklady.  
  
 Když [_DEBUG](/cpp/c-runtime-library/debug) je definován, CRT mapuje všechny [malloc](/cpp/c-runtime-library/reference/malloc) volání [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Proto není potřeba revize kódu pomocí `_malloc_dbg` místo `malloc` získat výhody při ladění.  
  
 Můžete chtít volat `_malloc_dbg` explicitně, ale. Volání `_malloc_dbg` explicitně má některé další výhody:  
  
- Sledování `_CLIENT_BLOCK` zadejte přidělení.  
  
- Ukládání zdrojový soubor a číslo řádku kde došlo k požadavek na přidělení.  
  
  Pokud nechcete převést vaše `malloc` volání `_malloc_dbg`, můžete získat informace o zdrojovém souboru tak, že definujete [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), což způsobí, že preprocesor přímá mapování všech volání `malloc` k `_malloc_dbg` aniž byste museli spoléhat na obálku kolem `malloc`.  
  
  Pokud chcete sledovat samostatné typy přidělení v blocích klienta, musí volat `_malloc_dbg` přímo a nastavte `blockType` parametr `_CLIENT_BLOCK`.  
  
  Když není definovaný _DEBUG, volání `malloc` nejsou narušen, volání `_malloc_dbg` , jsou vyhodnoceny na `malloc`, definice [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) bude ignorována a zdroje týkající se informací o souboru požadavek na přidělení není k dispozici. Protože `malloc` nemá parametr typu blok, žádosti o `_CLIENT_BLOCK` typy se považují za standardní přidělení.  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)