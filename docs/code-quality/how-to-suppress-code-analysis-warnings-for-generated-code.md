---
title: Potlačit porušení analýzy kódu pro generovaný kód
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39daa50254f2d1b69514d4065e582154e9ceb6b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649394"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Postupy: potlačení upozornění analýzy kódu pro generovaný kód

Generovaný kód zahrnuje kód, který je přidán do projektu pomocí kompilátorů spravovaného kódu nebo nástrojů třetích stran. Je možné, že budete chtít zobrazit porušení pravidel, která analýza kódu zjistí v generovaném kódu. Vzhledem k tomu, že nemůžete zobrazit a udržovat kód, který obsahuje porušení, možná je nechcete zobrazit.

Zaškrtávací políčko **Potlačit výsledky z vygenerovaného kódu** na stránce vlastností analýza kódu projektu umožňuje vybrat, zda se má zobrazit upozornění analýzy kódu z kódu generovaného nástrojem třetí strany.

> [!NOTE]
> Tato možnost potlačí chyby a upozornění analýzy kódu z generovaného kódu, pokud se chyby a upozornění zobrazují ve formulářích a šablonách. Zdrojový kód formuláře nebo šablony můžete zobrazit a spravovat.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Potlačení upozornění pro generovaný kód v projektu

1. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a pak klikněte na **vlastnosti**.

2. Klikněte na kartu **Analýza kódu** .

3. Zaškrtněte políčko **Potlačit výsledky z generovaného kódu** .

> [!NOTE]
> Upozornění můžete potlačit jenom z analýz starší verze. V současné době nemůžete potlačit upozornění analýzy kódu z [analyzátorů](roslyn-analyzers-overview.md).
