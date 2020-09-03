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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585766"
---
# <a name="preview-changes-window"></a>Okno Náhled změn

Při použití různých *rychlých akcí* nebo nástrojů *refaktoringu* v aplikaci Visual Studio je často možné zobrazit náhled změn, které budou provedeny v projektu, a teprve potom je přijmout. V okně **Náhled změn** je tam, kde je to hotové.  Zde je například okno **Náhled změn** zobrazující, co bude změněno během refaktoru přejmenování v projektu jazyka C#:

![Náhled změn](media/previewchanges.png)

Horní polovina okna zobrazuje konkrétní řádky, které budou změněny, přičemž každý má zaškrtávací políčko. Zaškrtnutím nebo zrušením zaškrtnutí jednotlivých políček můžete v případě, že chcete selektivně použít refaktoring pouze na určité řádky.

V dolní polovině okna se zobrazuje formátovaný kód z projektu, který bude změněn, přičemž byly zvýrazněny ovlivněné oblasti. Výběrem konkrétního řádku v horní polovině okna se zvýrazní odpovídající řádek v dolní polovině. To vám umožní rychle přeskočit na příslušný řádek a zobrazit okolní kód.

Po zkontrolování změn klikněte na tlačítko **použít** a potvrďte tyto změny, nebo klikněte na tlačítko **Storno** , aby bylo možné některé z nich nechat.

## <a name="see-also"></a>Viz také

- [Refaktoring v sadě Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Rychlé akce](../ide/quick-actions.md)
