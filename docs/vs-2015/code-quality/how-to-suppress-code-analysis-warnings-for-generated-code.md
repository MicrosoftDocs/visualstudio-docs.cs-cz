---
title: 'Postupy: potlačení upozornění analýzy kódu pro generovaný kód | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646266"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Postupy: Potlačení upozornění Analýzy kódu pro vygenerovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kompilátory spravovaného kódu často generují kód, který je přidán do projektu pro usnadnění rychlého vývoje kódu. Kromě toho vývojáři často používají nástroje třetích stran, které vám pomůžou rychle vyvíjet aplikace. Tyto nástroje také generují kód, který je přidán do projektu.

 Je možné, že budete chtít zobrazit porušení pravidel, která analýza kódu zjistí v generovaném kódu. Nebudete je však chtít zobrazit, pokud nemůžete zobrazit a udržovat kód, který obsahuje porušení.

 Zaškrtávací políčko **Potlačit výsledky z vygenerovaného kódu** na stránce vlastností analýza kódu projektu umožňuje vybrat, zda chcete zobrazit upozornění analýzy kódu z kódu generovaného nástrojem třetí strany.

> [!NOTE]
> Tato možnost potlačí chyby a upozornění analýzy kódu z generovaného kódu, pokud se chyby a upozornění zobrazují ve formulářích a šablonách. Zdrojový kód formuláře nebo šablony můžete zobrazit a spravovat.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Potlačení upozornění pro generovaný kód v projektu

1. Klikněte pravým tlačítkem na projekt v Průzkumník řešení a pak klikněte na **vlastnosti**.

2. Klikněte na **Analýza kódu**.

3. Zaškrtněte políčko **Potlačit výsledky z generovaného kódu** .
