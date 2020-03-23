---
title: Generovat přepsání metody
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569241"
---
# <a name="generate-an-override-in-visual-studio"></a>Generovat přepsání v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě generovat kód pro libovolnou metodu, která může být přepsána ze základní třídy.

**Kdy:** Chcete přepsat metodu základní třídy a automaticky vygenerovat podpis.

**Proč:** Podpis metody můžete napsat sami, ale tato funkce bude automaticky generovat podpis.

## <a name="how-to"></a>Postupy

1. Zadejte `override` c# `Overrides` nebo v jazyce Visual Basic, následovaný mezerou, kde chcete vložit metodu přepsání.

   - C#:

      ![Přepsat technologie IntelliSense C #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Přepsat technologie IntelliSense VB](media/override-intellisense-vb.png)

2. Vyberte metodu, kterou chcete přepsat ze základní třídy.

   > [!TIP]
   > - Použití ikony vlastnosti ![Ikona vlastnosti](media/override-property-cs.png) zobrazíte nebo skryjete vlastnosti v seznamu.
   > - Použití ikony metody ![Ikona metody](media/override-method-cs.png) zobrazíte nebo skryjete metody v seznamu.

   Vybraná metoda nebo vlastnost je přidána do třídy jako přepsání, připravené k implementaci.

   - C#:

       ![Přepsat výsledek C #](media/override-result-cs.png)

   - Visual Basic:

       ![Přepsat výsledek VB](media/override-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
