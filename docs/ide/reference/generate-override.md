---
title: Vygenerovat přepsání metody
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 075c7dc49ffba1d67bbb5b62d313f50b5d09e956
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668436"
---
# <a name="generate-an-override-in-visual-studio"></a>Vygenerování přepsání v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje ihned vygenerovat kód pro jakoukoliv metodu, která může být přepsána ze základní třídy.

**Když:** Chcete přepsat metodu základní třídy a automaticky vygenerovat podpis.

**Proč:** Podpis metody můžete napsat sami, ale tato funkce bude podpis generovat automaticky.

## <a name="how-to"></a>Postupy

1. Do Visual Basic zadejte C# `override` nebo `Overrides` následovaný mezerou, kam chcete vložit metodu override.

   - C#:

      ![Přepsat IntelliSenseC#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Přepsat IntelliSense VB](media/override-intellisense-vb.png)

2. Vyberte metodu, kterou chcete přepsat ze základní třídy.

   > [!TIP]
   > - Použití ikony vlastnosti ![Ikona vlastnosti](media/override-property-cs.png) zobrazení nebo skrytí vlastností v seznamu.
   > - Použijte ikonu metody ![Ikona metody](media/override-method-cs.png) pro zobrazení nebo skrytí metod v seznamu.

   Vybraná metoda nebo vlastnost je přidána do třídy jako přepsání připravené k implementaci.

   - C#:

       ![Výsledek přepsáníC#](media/override-result-cs.png)

   - Visual Basic:

       ![Výsledek potlačení VB](media/override-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)