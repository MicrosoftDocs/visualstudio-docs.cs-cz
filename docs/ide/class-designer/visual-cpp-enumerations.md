---
title: Výčty jazyka C++ v Návrháři tříd
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee56850c05e4b06ea4325ec238e56e99b38978d0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114196"
---
# <a name="c-enumerations-in-class-designer"></a>Výčty jazyka C++ v Návrháři tříd

**Návrhář tříd** podporuje `enum` typy Jazyka `enum class` C++ a scoped. Tady je příklad:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Obrazec výčtu jazyka C++ v diagramu třídy vypadá a funguje jako obrazec struktury s tím rozdílem, že popisek čte **třídu Výčtu** nebo **Výčtu**, je růžový místo modrý a má barevné ohraničení vlevo a horní okraj. Obrazce výčtu i obrazce struktury mají čtvercové rohy.

Další informace o `enum` použití typu naleznete v tématu [Výčet](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Viz také

- [Práce s kódem jazyka C++](working-with-visual-cpp-code.md)
- [Výčty](/cpp/cpp/enumerations-cpp)
