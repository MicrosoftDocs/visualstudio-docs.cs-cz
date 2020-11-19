---
title: Výčty C++ v Návrhář tříd
description: Přečtěte si, jak Návrhář tříd podporuje výčty výčtového typu C++ a vymezené třídy výčtu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b12d270884ca9877d6c1c80780a9ae96324f3af4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903452"
---
# <a name="c-enumerations-in-class-designer"></a>Výčty C++ v Návrhář tříd

**Návrhář tříd** podporuje C++ `enum` a oborové `enum class` typy. Tady je příklad:

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

Tvar výčtu C++ v diagramu tříd vypadá a funguje jako obrazec struktury, s tím rozdílem, že popisek čte **výčet** nebo **třídu enum**, je růžový namísto modrý a má barevné ohraničení na levém a horním okraji. Obrazce výčtu i obrazce struktury mají čtvercové rohy.

Další informace o použití tohoto `enum` typu naleznete v tématu [výčty](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Viz také

- [Práce s kódem C++](working-with-visual-cpp-code.md)
- [Výčty](/cpp/cpp/enumerations-cpp)
