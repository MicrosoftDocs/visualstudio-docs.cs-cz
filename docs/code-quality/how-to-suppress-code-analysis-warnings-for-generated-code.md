---
title: Potlačit porušení analýzy kódu pro generovaný kód
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab2ffce28103059414cef8f1b556152485a12ff
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587430"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Postupy: potlačení upozornění analýzy kódu pro generovaný kód

Generovaný kód zahrnuje kód, který je přidán do projektu pomocí kompilátorů spravovaného kódu nebo nástrojů třetích stran. Je možné, že budete chtít zobrazit porušení pravidel, která analýza kódu zjistí v generovaném kódu. Vzhledem k tomu, že nemůžete zobrazit a udržovat kód, který obsahuje porušení, možná je nechcete zobrazit.

Zaškrtávací políčko **Potlačit výsledky z vygenerovaného kódu** na stránce vlastností analýza kódu projektu umožňuje vybrat, zda se má zobrazit upozornění analýzy kódu z kódu generovaného nástrojem třetí strany.

> [!NOTE]
> Tato možnost není potlačit chyby analýzy kódu a upozornění z generovaného kódu při chyby a upozornění se zobrazí ve formulářích a šablony. Zdrojový kód formuláře nebo šablony můžete zobrazit a spravovat.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Potlačení upozornění pro generovaný kód v projektu

1. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a pak klikněte na **vlastnosti**.

2. Klikněte na kartu **Analýza kódu** .

3. Zaškrtněte políčko **Potlačit výsledky z generovaného kódu** .

> [!IMPORTANT]
> Upozornění můžete potlačit jenom z analýz starší verze. Stránka vlastností s nastavením je zastaralá a v budoucí verzi produktu se odebere. V současné době nemůžete potlačit upozornění analýzy kódu z [analyzátorů](roslyn-analyzers-overview.md).
