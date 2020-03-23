---
title: Struktury Jazyka C++ v návrháři tříd
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590681"
---
# <a name="c-structures-in-class-designer"></a>Struktury Jazyka C++ v návrháři tříd

**Class Designer** podporuje c++ struktury, které `struct`jsou deklarovány pomocí klíčového slova . Tady je příklad:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Další informace o `struct` použití typu naleznete v [tématu struct](/cpp/cpp/struct-cpp).

Obrazec struktury jazyka C++ v diagramu třídy vypadá a funguje jako obrazec třídy s tím rozdílem, že popisek čte **Struct** a má čtvercové rohy namísto zaoblených rohů.

|Element kódu|Zobrazení Návrháře tříd|
|------------------| - |
|`struct StructureName {};`|**Název_struktury**<br /><br /> Struktura|

## <a name="see-also"></a>Viz také

- [Práce s kódem jazyka C++](working-with-visual-cpp-code.md)
- [Třídy a struky](/cpp/cpp/classes-and-structs-cpp)
- [Struct](/cpp/cpp/struct-cpp)
