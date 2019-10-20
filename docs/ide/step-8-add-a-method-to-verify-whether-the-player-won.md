---
title: 'Krok 8: Přidejte metodu k ověření, zda hráč zvítězil'
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
ms.openlocfilehash: 0c451b2da08fdb0b38487438a47c6285b0380627
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647457"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Přidejte metodu k ověření, zda hráč zvítězil
Vytvořili jste zábavnou hru, která však potřebuje ještě něco. Hra by měla skončit, když je přehrávač WINS, takže pokud chcete ověřit, zda hráč zvítězil, je třeba přidat metodu `CheckForWinner()`.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Přidání metody k ověření, zda hráč zvítězil

1. Do dolní části kódu přidejte `CheckForWinner()` metodu, která je pod obslužnou rutinou události `timer1_Tick()`, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Programming jazykové řízení pro ](../ide/media/docs-programming-language-control.png) Docs.Microsoft.com     

     Metoda používá jiný `foreach` smyčka v C# nebo `For Each` smyčka v Visual Basic k procházení každého popisku v <xref:System.Windows.Forms.TableLayoutPanel>. Používá operátor rovnosti (`==` v C# a `=` v Visual Basic) ke kontrole barvy ikony jednotlivých popisků a k ověření, zda odpovídá pozadí. Pokud se barvy shodují, zůstane ikona skryta a hráč nespároval všechny zbývající ikony. V takovém případě program používá příkaz `return` k přeskočení zbytku metody. Pokud smyčka projde všemi štítky bez provedení příkazu `return`, znamená to, že všechny ikony ve formuláři byly spárovány. Program zobrazí MessageBox, aby congratulate přehrávač při výhrě, a potom zavolá metodu `Close()` formuláře pro ukončení hry.

2. Dále musí obslužná rutina události <xref:System.Windows.Forms.Control.Click> popisku volat novou metodu `CheckForWinner()`. Ujistěte se, že váš program kontroluje vítěze ihned po tom, co zobrazí druhou ikonu, kterou hráč vybere. Vyhledejte řádek, kde jste nastavili barvu druhé zvolené ikony, a potom zavolejte metodu `CheckForWinner()` hned po tom, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Program uložte a spusťte jej. Zahrajte si hru a spárujte všechny ikony. Když nahrajete, program zobrazí congratulatory **MessageBox** (jak je znázorněno na následujícím snímku obrazovky) a pak okno zavře.

     ![Matching hry pomocí MessageBox ](../ide/media/express_tut4step8.png)<br/>
***Porovnávací hra*** *s* ***MessageBox***

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek krok 9: Vyzkoušejte si další funkce](../ide/step-9-try-other-features.md)** .

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md).
