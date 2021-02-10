---
title: Vygenerovat přepsání metody
description: Naučte se ihned vygenerovat kód pro jakoukoliv metodu, která může být přepsána ze základní třídy.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3640fe29a18ba1ec89ab2806810165a0ec509167
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968057"
---
# <a name="generate-an-override-in-visual-studio"></a>Vygenerování přepsání v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje ihned vygenerovat kód pro jakoukoliv metodu, která může být přepsána ze základní třídy.

**Když:** Chcete přepsat metodu základní třídy a automaticky vygenerovat podpis.

**Proč:** Podpis metody můžete napsat sami, ale tato funkce bude podpis generovat automaticky.

## <a name="how-to"></a>Postupy

1. Zadejte `override` v jazyce C# nebo `Overrides` v Visual Basic, za nímž následuje mezera, kam chcete vložit metodu přepsání.

   - C#:

      ![Přepsat IntelliSense C #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Přepsat IntelliSense VB](media/override-intellisense-vb.png)

2. Vyberte metodu, kterou chcete přepsat ze základní třídy.

   > [!TIP]
   > - Použití ikony vlastnosti ![Ikona vlastnosti](media/override-property-cs.png) zobrazení nebo skrytí vlastností v seznamu.
   > - Použijte ikonu metody ![Ikona metody](media/override-method-cs.png) pro zobrazení nebo skrytí metod v seznamu.

   Vybraná metoda nebo vlastnost je přidána do třídy jako přepsání připravené k implementaci.

   - C#:

       ![Přepsat výsledek C #](media/override-result-cs.png)

   - Visual Basic:

       ![Výsledek potlačení VB](media/override-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
