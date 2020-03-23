---
title: Náhled změn kódu
ms.date: 12/16/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: f45b186153b4cc046d35fd941f6a80e108476fc0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585766"
---
# <a name="preview-changes-window"></a>Okno Náhled změn

Při použití různých *rychlých akcí* nebo *refaktoringu* nástroje v sadě Visual Studio, je často možné zobrazit náhled změny, které budou provedeny v projektu před jejich přijetím. Okno **Změny náhledu** je místo, kde se to provádí.  Například zde je **náhled změny** okno zobrazující, co se změní během refactor přejmenování v projektu C#:

![Náhled změn](media/previewchanges.png)

V horní polovině okna se zobrazí konkrétní řádky, které budou změněny, každý se zaškrtávacím políčkem. Můžete zaškrtnout nebo zrušit zaškrtnutí každého políčka, pokud chcete selektivně použít refaktoring pouze na určité řádky.

V dolní polovině okna se zobrazí formátovaný kód z projektu, který bude změněn se zvýrazněnými postiženými oblastmi. Výběrem konkrétního řádku v horní polovině okna zvýrazníte odpovídající řádek v dolní polovině. To vám umožní rychle přeskočit na příslušný řádek a zobrazit okolní kód.

Po kontrole změn klikněte na tlačítko **Použít,** abyste tyto změny potvrdí, nebo kliknutím na tlačítko **Storno** ponechte věci tak, jak byly.

## <a name="see-also"></a>Viz také

- [Refaktoring v sadě Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Rychlé akce](../ide/quick-actions.md)
