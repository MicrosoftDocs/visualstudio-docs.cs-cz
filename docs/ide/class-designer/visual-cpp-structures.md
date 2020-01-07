---
title: C++Struktury v Návrhář tříd
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590681"
---
# <a name="c-structures-in-class-designer"></a>C++struktury v Návrhář tříd

**Návrhář tříd** podporuje C++ struktury, které jsou deklarovány pomocí klíčového slova `struct`. Tady je příklad:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Další informace o použití typu `struct` naleznete v tématu [struct](/cpp/cpp/struct-cpp).

Obrazec C++ struktury v diagramu tříd vypadá a funguje jako obrazec třídy, s tím rozdílem, že popisek čte **strukturu** a má čtvercové rohy namísto zaoblených rohů.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struktura|

## <a name="see-also"></a>Viz také:

- [Práce s C++ kódem](working-with-visual-cpp-code.md)
- [Třídy a struktury](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
