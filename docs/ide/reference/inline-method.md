---
title: Vložená metoda
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
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402261"
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

    ![Nastavit abstraktní třídu](media/inline-method-remove-declaration.png)

   Vyberte možnost **Vložit a zachovat `<QualifiedMethodName>`** , abyste zachovali deklaraci původní metody: 

    ![Nastavit abstraktní třídu](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
