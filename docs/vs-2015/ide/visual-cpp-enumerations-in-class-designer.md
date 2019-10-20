---
title: Vizuální C++ výčty v Návrhář tříd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651669"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Výčty jazyka Visual C++ v návrháři tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář tříd podporuje C++ `enum` a vymezené `enum class` typy. Následuje příklad:

```
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

 Další informace o použití typu `enum` naleznete v tématu [výčty](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).

## <a name="see-also"></a>Viz také
 Práce s [výčty](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) [Visual C++ Code (návrhář tříd)](../ide/working-with-visual-cpp-code-class-designer.md)
