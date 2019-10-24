---
title: C++Struktury v Návrhář tříd
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 65fb4738b3124daf48b501c6db416d3803da32ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748908"
---
# <a name="c-structures-in-class-designer"></a>C++struktury v Návrhář tříd

**Návrhář tříd** podporuje C++ struktury, které jsou deklarovány pomocí klíčového slova `struct`. Následuje příklad:

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