---
title: Struktury jazyka Visual C++ v návrháři tříd
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 79b4adcfbcacc8cf342b5fc4183ae4fe27431b09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864767"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ v Návrháři tříd

**Návrhář tříd** podporuje struktury, C++, které jsou deklarovány pomocí klíčového slova `struct`. Tady je příklad:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Další informace o používání `struct` zadejte naleznete v tématu [struktura](/cpp/cpp/struct-cpp).

Tvar struktury C++ v diagramu třídy vypadá a funguje jako tvar třídy, s tím rozdílem, že načte popisek **struktura** a má hranaté rohy místo zaoblené rohy.

|Element kódu|Zobrazení návrháře tříd|
|------------------| - |
|`struct StructureName {};`|**%{Structurename/**<br /><br /> Struktura|

## <a name="see-also"></a>Viz také:

- [Práce s kódem jazyka Visual C++](working-with-visual-cpp-code.md)
- [Třídy a struktury](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)