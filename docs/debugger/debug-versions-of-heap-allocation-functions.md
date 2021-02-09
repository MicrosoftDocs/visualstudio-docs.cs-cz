---
title: Ladění verzí funkcí přidělení haldy | Microsoft Docs
description: Použijte ladicí verze funkcí přidělení haldy v knihovně run-time jazyka C. Tyto funkce mají stejné názvy jako verze vydání s _dbg připojena.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eedf9259f7bc62f32ca563d863a7fb686b8f6f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873116"
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