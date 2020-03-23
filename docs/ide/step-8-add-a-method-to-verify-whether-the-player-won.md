---
title: 'Krok 8: Přidejte metodu k ověření, zda hráč vyhrál'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881fa0d90390a059bea28cb19584381f814396d3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579761"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Přidejte metodu k ověření, zda hráč vyhrál
Vytvořili jste zábavnou hru, která však potřebuje ještě něco. Hra by měla skončit, když hráč vyhraje, `CheckForWinner()` takže je třeba přidat metodu k ověření, zda hráč vyhrál.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Přidání metody k ověření, zda hráč zvítězil

1. Přidejte `CheckForWinner()` metodu do dolní části `timer1_Tick()` kódu pod obslužnou rutinu události, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky zobrazíte fragment kódu jazyka C# nebo fragment kódu jazyka Visual Basic.<br><br>![Ovládání programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     Metoda používá `foreach` jinou smyčku v jazyce C# `For Each` nebo <xref:System.Windows.Forms.TableLayoutPanel>smyčky v jazyce Visual Basic projít každý popisek v . Používá operátor rovnosti`==` ( v `=` jazyce C# a v jazyce Visual Basic) ke kontrole barvy ikony každého popisku a ověření, zda odpovídá pozadí. Pokud se barvy shodují, zůstane ikona skryta a hráč nespároval všechny zbývající ikony. V takovém případě program `return` používá příkaz přeskočit zbytek metody. Pokud smyčka prochází všechny popisky bez `return` spuštění příkazu, znamená to, že všechny ikony ve formuláři byly spárovány. Program ukazuje MessageBox poblahopřát hráči na výhru, a `Close()` pak volá formulář metoda ukončit hru.

2. Dále mají obslužná <xref:System.Windows.Forms.Control.Click> rutina `CheckForWinner()` události popisku volání nové metody. Ujistěte se, že váš program kontroluje vítěze ihned po tom, co zobrazí druhou ikonu, kterou hráč vybere. Vyhledejte řádek, kde nastavíte barvu druhé vybrané ikony, a poté zavolejte metodu `CheckForWinner()` hned poté, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Program uložte a spusťte jej. Zahrajte si hru a spárujte všechny ikony. Když vyhrajete, program zobrazí gratulační **MessageBox** (jak je znázorněno na následujícím snímku obrazovky) a pak zavře pole.

     ![Porovnávací hra s ovládacím prvkem MessageBox](../ide/media/express_tut4step8.png)<br/>
***Odpovídající hra*** *s* ***MessageBox***

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 9: Vyzkoušejte další funkce](../ide/step-9-try-other-features.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 7: Zachovat viditelné dvojice](../ide/step-7-keep-pairs-visible.md).
