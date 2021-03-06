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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88675bb7593a901805cc156bbb36a2f49d69ec29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852554"
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
