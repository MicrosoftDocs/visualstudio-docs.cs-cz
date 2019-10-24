---
title: Ladění verzí funkcí přidělení haldy | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0fde776e9f2bd48aca92c7ba6d7f1fe1e23f01a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738376"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Ladění verzí funkcí přidělení haldy
Knihovna run-time jazyka C obsahuje speciální ladicí verze funkcí přidělení haldy. Tyto funkce mají stejné názvy jako verze pro vydání, ke kterým se připojí _dbg. Toto téma popisuje rozdíly mezi vydáním verze funkce CRT a _dbg verze pomocí `malloc` a `_malloc_dbg` jako příklady.

 Pokud je definována [_DEBUG](/cpp/c-runtime-library/debug) , CRT [mapuje všechna volání](/cpp/c-runtime-library/reference/malloc) [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Proto nemusíte přepisovat kód pomocí `_malloc_dbg` místo `malloc` pro příjem výhod při ladění.

 Je však vhodné volat `_malloc_dbg` explicitně. Volání `_malloc_dbg` explicitně přináší některé přidané výhody:

- Sledování přidělení typu `_CLIENT_BLOCK`.

- Ukládá se zdrojový soubor a číslo řádku, kde došlo k žádosti o přidělení.

  Pokud nechcete převést volání `malloc` na `_malloc_dbg`, můžete získat informace o zdrojovém souboru definováním [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), což způsobí, že preprocesoru přímo namapuje všechna volání do `malloc` na `_malloc_dbg` nemusíte spoléhat na obálku kolem  `malloc`.

  Chcete-li sledovat samostatné typy přidělení v klientských blocích, je nutné volat `_malloc_dbg` přímo a nastavit parametr `blockType` na `_CLIENT_BLOCK`.

  Není-li _DEBUG definováno, volání `malloc` nejsou narušena, volání `_malloc_dbg` jsou přeložena na `malloc`, definice [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) je ignorována a informace o zdrojovém souboru týkající se žádosti o přidělení nejsou k dispozici. Vzhledem k tomu, že `malloc` nemá parametr typu bloku, jsou požadavky na typy `_CLIENT_BLOCK` považovány za standardní přidělení.

## <a name="see-also"></a>Viz také:

- [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)