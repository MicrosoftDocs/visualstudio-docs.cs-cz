---
title: Struktury C++ v Návrhář tříd
description: Přečtěte si, jak Návrhář tříd podporuje struktury C++ deklarované pomocí klíčové slovo struct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca35f9e1c3c1340330ddbbe36ede540fe1e547d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879953"
---
# <a name="c-structures-in-class-designer"></a>Struktury C++ v Návrhář tříd

**Návrhář tříd** podporuje struktury jazyka C++, které jsou deklarovány pomocí klíčového slova `struct` . Tady je příklad:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Další informace o použití tohoto `struct` typu naleznete v tématu [struct](/cpp/cpp/struct-cpp).

Obrazec struktury C++ v diagramu tříd vypadá a funguje jako obrazec třídy, s tím rozdílem, že popisek čte **strukturu** a má čtvercové rohy namísto zaoblených rohů.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struktura|

## <a name="see-also"></a>Viz také

- [Práce s kódem C++](working-with-visual-cpp-code.md)
- [Třídy a struktury](/cpp/cpp/classes-and-structs-cpp)
- [nemají](/cpp/cpp/struct-cpp)
