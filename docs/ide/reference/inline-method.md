---
title: Vložená metoda
description: Naučte se, jak pomocí nabídky rychlé akce a Refaktoring v aplikaci Visual Studio Refaktorovat deklarace vložené do vložených metod a zadat zřetelnou syntaxi.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761417"
---
# <a name="inline-method"></a>Vložená metoda

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Refaktoring vložené metody. 

**Když:** Chcete nahradit použití statické, instance a metody rozšíření v rámci jednoho těla příkazu s možností odebrání původní deklarace metody.

**Proč:**  Tento refaktoring nabídne zřetelnější syntaxi.

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na použití metody.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vyberte jednu z následujících možností: 
    
   Vyberte možnost **Vložit `<QualifiedMethodName>`** , abyste odebrali deklaraci vložené metody: 

    ![Screeenshot z nabídky rychlé akce a Refaktoring v aplikaci Visual Studio s vybranou možnost převést vloženou CreateWidget () a zobrazenou změnu kódu jazyka C#.](media/inline-method-remove-declaration.png)

   Vyberte možnost **Vložit a zachovat `<QualifiedMethodName>`** , abyste zachovali deklaraci původní metody: 

    ![Screeenshot z nabídky rychlé akce a Refaktoring v aplikaci Visual Studio s vybranou možnost převést "vložené a zachovat" CreateWidget () "a zobrazí se změny kódu jazyka C#.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
