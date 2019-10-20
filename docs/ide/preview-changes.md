---
title: Náhled změn kódu
ms.date: 12/16/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: 485a127faa8228ce5ef17a6208e9cc4e7e50e1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666800"
---
# <a name="preview-changes-window"></a>Okno Náhled změn

Při použití různých *rychlých akcí* nebo nástrojů *refaktoringu* v aplikaci Visual Studio je často možné zobrazit náhled změn, které budou provedeny v projektu, a teprve potom je přijmout. V okně **Náhled změn** je tam, kde je to hotové.  Zde je například okno **Náhled změn** , které ukazuje, co se změní během refaktoru přejmenování v C# projektu:

![Náhled změn](media/previewchanges.png)

Horní polovina okna zobrazuje konkrétní řádky, které budou změněny, přičemž každý má zaškrtávací políčko. Zaškrtnutím nebo zrušením zaškrtnutí jednotlivých políček můžete v případě, že chcete selektivně použít refaktoring pouze na určité řádky.

V dolní polovině okna se zobrazuje formátovaný kód z projektu, který bude změněn, přičemž byly zvýrazněny ovlivněné oblasti. Výběrem konkrétního řádku v horní polovině okna se zvýrazní odpovídající řádek v dolní polovině. To vám umožní rychle přeskočit na příslušný řádek a zobrazit okolní kód.

Po zkontrolování změn klikněte na tlačítko **použít** a potvrďte tyto změny, nebo klikněte na tlačítko **Storno** , aby bylo možné některé z nich nechat.

## <a name="see-also"></a>Viz také:

- [Refaktoring v aplikaci Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Rychlé akce](../ide/quick-actions.md)
