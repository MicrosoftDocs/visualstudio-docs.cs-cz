---
title: 'Krok 8: Přidejte metodu k ověření, zda hráč vyhrál'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34b4e8085c3ff3de8037827769331eac83325ff8
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748007"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Přidejte metodu k ověření, zda hráč vyhrál
Vytvořili jste zábavnou hru, která však potřebuje ještě něco. Hra by měla skončit při přehrávač služby wins, proto je nutné přidat `CheckForWinner()` metodu k ověření, zda hráč vyhrál.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Přidání metody k ověření, zda hráč zvítězil

1.  Přidat `CheckForWinner()` metoda do dolní části kódu, níže `timer1_Tick()` obslužné rutiny události, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     Metoda používá další `foreach` smyčky v jazyce Visual C# nebo `For Each` v jazyce Visual Basic projít každý popisek v <xref:System.Windows.Forms.TableLayoutPanel>. Používá operátor rovnosti (`==` v jazyce Visual C# a `=` v jazyce Visual Basic) ke kontrole barvy ikony každý popisek k ověření, zda odpovídá na pozadí. Pokud se barvy shodují, zůstane ikona skryta a hráč nespároval všechny zbývající ikony. V takovém případě se používá program `return` příkaz tak, aby přeskočil zbytek metodu. Pokud získá prostřednictvím všechny popisky smyčky bez spuštění `return` příkaz, který znamená všechny ikony na formuláři byly odpovídá. Program zobrazí MessageBox k Blahopřání player v hodnocený a pak zavolá formuláře `Close()` metoda k ukončení hry.

2.  V dalším kroku mít jmenovky <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zavolat novou `CheckForWinner()` metoda. Ujistěte se, že váš program kontroluje vítěze ihned po tom, co zobrazí druhou ikonu, kterou hráč vybere. Vyhledejte řádek, kde nastavíte barvy druhý zvolené ikony a pak zavolají `CheckForWinner()` metoda hned po tomto, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3.  Program uložte a spusťte jej. Zahrajte si hru a spárujte všechny ikony. Když získáte, program zobrazí gratulací **MessageBox** (jak ukazuje následující obrázek) a poté uzavře pole.

     ![Odpovídající hru s MessageBox](../ide/media/express_tut4step8.png)
**odpovídající herní** s **MessageBox**

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 9: Vyzkoušejte jiné funkce](../ide/step-9-try-other-features.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 7: uchovejte páry viditelné](../ide/step-7-keep-pairs-visible.md).
