---
title: 'Krok 8: Přidání metody k ověření, jestli hráč vyhrál'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed7a2796f08e85441c174e882c00fa406cb2379
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289659"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Přidání metody k ověření, jestli hráč vyhrál
Vytvořili jste zábavnou hru, která však potřebuje ještě něco. Hra by měla skončit, když je přehrávač WINS, takže potřebujete přidat metodu `CheckForWinner()` pro ověření, zda hráč zvítězil.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Přidání metody k ověření, zda hráč zvítězil

1. Do dolní části kódu přidejte metodu `CheckForWinner()` pod obslužnou rutinou události `timer1_Tick()`, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>@no__t – ovládací prvek jazyka pro Docs. Microsoft. com @ no__t-1     

     Metoda používá k procházení každého popisku v <xref:System.Windows.Forms.TableLayoutPanel> C# další @no__t smyčka v jazyce Visual nebo ve smyčce `For Each` v Visual Basic. Používá operátor rovnosti (`==` v jazyce Visual C# a `=` v Visual Basic) ke kontrole barvy ikony jednotlivých popisků a k ověření, zda odpovídá pozadí. Pokud se barvy shodují, zůstane ikona skryta a hráč nespároval všechny zbývající ikony. V takovém případě program používá příkaz `return` k přeskočení zbytku metody. Pokud smyčka projde všemi štítky bez provedení příkazu `return`, znamená to, že všechny ikony ve formuláři byly spárovány. Program zobrazí MessageBox, aby congratulate přehrávač při výhrě, a potom zavolá metodu `Close()` formuláře pro ukončení hry.

2. Dále požádejte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> popisku, který volá novou metodu `CheckForWinner()`. Ujistěte se, že váš program kontroluje vítěze ihned po tom, co zobrazí druhou ikonu, kterou hráč vybere. Vyhledejte řádek, kde jste nastavili barvu druhé zvolené ikony, a potom zavolejte metodu `CheckForWinner()` hned po tom, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Program uložte a spusťte jej. Zahrajte si hru a spárujte všechny ikony. Když nahrajete, program zobrazí congratulatory **MessageBox** (jak je znázorněno na následujícím obrázku) a pak pole zavře.

     @no__t – 0Matching hry s MessageBox @ no__t-1<br/>
**Porovnávací hra** s **MessageBox**

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si téma [Step 9: Vyzkoušejte jiné funkce @ no__t-0.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si článek [Step 7: Zachovat páry viditelné @ no__t-0.
