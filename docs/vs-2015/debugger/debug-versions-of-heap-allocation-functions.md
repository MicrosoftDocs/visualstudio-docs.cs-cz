---
title: Ladění verzí funkcí přidělení haldy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691160"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Ladění verzí funkcí přidělení haldy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Knihovna run-time jazyka C obsahuje speciální ladicí verze funkcí přidělení haldy. Tyto funkce mají stejné názvy jako verze pro vydání s _dbg připojené k nim. Toto téma popisuje rozdíly mezi vydáním verze funkce CRT a verzí _dbg, a to pomocí `malloc` `_malloc_dbg` příkladů a jako příklady.  
  
 Pokud je definována [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) , CRT namapuje všechna [volání](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) nevlastního rozhraní na [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Proto nemusíte přepisovat kód pomocí `_malloc_dbg` místo `malloc` pro příjem výhod při ladění.  
  
 Je však vhodné volat `_malloc_dbg` explicitně. `_malloc_dbg`Explicitní volání má některé přidané výhody:  
  
- Sledování `_CLIENT_BLOCK` Přidělení typu.  
  
- Ukládá se zdrojový soubor a číslo řádku, kde došlo k žádosti o přidělení.  
  
  Pokud nechcete převádět `malloc` volání na `_malloc_dbg` , můžete získat informace o zdrojovém souboru definováním [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), což způsobí, že preprocesoru přímo namapuje všechna volání na `malloc` `_malloc_dbg` místo nespoléhání na obálku `malloc` .  
  
  Chcete-li sledovat samostatné typy přidělení v klientských blocích, je nutné zavolat `_malloc_dbg` přímo a nastavit `blockType` parametr na `_CLIENT_BLOCK` .  
  
  Není-li _DEBUG definováno, volání nejsou `malloc` narušena, volání `_malloc_dbg` jsou přeložena na `malloc` , definice [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) je ignorována a informace o zdrojovém souboru týkající se žádosti o přidělení nejsou poskytovány. Vzhledem k tomu, že nemá `malloc` parametr typu bloku, jsou požadavky na `_CLIENT_BLOCK` typy zpracovány jako standardní přidělení.  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)
