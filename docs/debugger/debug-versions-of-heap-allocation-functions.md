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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738376"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Ladění verzí funkcí přidělení haldy
Knihovna run-time jazyka C obsahuje speciální ladicí verze funkcí přidělení haldy. Tyto funkce mají stejné názvy jako verze pro vydání s _dbg připojené k nim. Toto téma popisuje rozdíly mezi vydáním verze funkce CRT a verzí _dbg, a to pomocí `malloc` `_malloc_dbg` příkladů a jako příklady.

 Pokud je definována [_DEBUG](/cpp/c-runtime-library/debug) , CRT namapuje všechna [volání](/cpp/c-runtime-library/reference/malloc) nevlastního rozhraní na [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Proto nemusíte přepisovat kód pomocí `_malloc_dbg` místo `malloc` pro příjem výhod při ladění.

 Je však vhodné volat `_malloc_dbg` explicitně. `_malloc_dbg`Explicitní volání má některé přidané výhody:

- Sledování `_CLIENT_BLOCK` Přidělení typu.

- Ukládá se zdrojový soubor a číslo řádku, kde došlo k žádosti o přidělení.

  Pokud nechcete převádět `malloc` volání na `_malloc_dbg` , můžete získat informace o zdrojovém souboru definováním [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), což způsobí, že preprocesoru přímo namapuje všechna volání na `malloc` `_malloc_dbg` místo nespoléhání na obálku `malloc` .

  Chcete-li sledovat samostatné typy přidělení v klientských blocích, je nutné zavolat `_malloc_dbg` přímo a nastavit `blockType` parametr na `_CLIENT_BLOCK` .

  Není-li _DEBUG definováno, volání nejsou `malloc` narušena, volání `_malloc_dbg` jsou přeložena na `malloc` , definice [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) je ignorována a informace o zdrojovém souboru týkající se žádosti o přidělení nejsou poskytovány. Vzhledem k tomu, že nemá `malloc` parametr typu bloku, jsou požadavky na `_CLIENT_BLOCK` typy zpracovány jako standardní přidělení.

## <a name="see-also"></a>Viz také

- [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)