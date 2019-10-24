---
title: C++Výčty v Návrhář tříd
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a514d5eb4b7f79e2fd193c79de670b6dd9c14cb5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747996"
---
# <a name="c-enumerations-in-class-designer"></a>C++výčty v Návrhář tříd

**Návrhář tříd** podporuje C++ `enum` a vymezené `enum class` typy. Následuje příklad:

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

Tvar C++ výčtu v diagramu třídy vypadá a funguje jako obrazec struktury, s tím rozdílem, že popisek čte **výčet** nebo **třídu enum**, je růžový namísto modré a má barevné ohraničení na levém a horním okraji. Obrazce výčtu i obrazce struktury mají čtvercové rohy.

Další informace o použití typu `enum` naleznete v tématu [výčty](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Viz také:

- [Práce s C++ kódem](working-with-visual-cpp-code.md)
- [Výčty](/cpp/cpp/enumerations-cpp)