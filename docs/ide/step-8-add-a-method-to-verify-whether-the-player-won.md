---
title: 'Krok 8: Přidání metody k ověření, jestli hráč vyhrál'
description: Naučte se, jak přidat metodu k určení, jestli hráč zvítězil.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c49a5d05e5bf1bb381bdc34d9fef60819e2790b1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214132"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Přidání metody k ověření, jestli hráč vyhrál
Vytvořili jste zábavnou hru, která však potřebuje ještě něco. Hra by měla skončit, když je přehrávač WINS, takže potřebujete přidat `CheckForWinner()` metodu pro ověření, zda hráč zvítězil.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Přidání metody k ověření, zda hráč zvítězil

1. Přidejte `CheckForWinner()` metodu do dolní části kódu pod `timer1_Tick()` obslužnou rutinou události, jak je znázorněno v následujícím kódu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment kódu jazyka C# nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     Metoda používá jinou `foreach` smyčku v jazyce C# nebo `For Each` loop v Visual Basic k tomu, aby procházel každý popisek v <xref:System.Windows.Forms.TableLayoutPanel> . Používá operátor rovnosti ( `==` v jazyce C# a `=` v Visual Basic) ke kontrole barvy ikony jednotlivých popisků a k ověření, zda odpovídá pozadí. Pokud se barvy shodují, zůstane ikona skryta a hráč nespároval všechny zbývající ikony. V takovém případě program používá `return` příkaz k přeskočení zbytku metody. Pokud smyčka projde všemi štítky bez provedení `return` příkazu, znamená to, že všechny ikony ve formuláři byly spárovány. Program zobrazí MessageBox, aby congratulate přehrávač při výhrě, a potom zavolá `Close()` metodu formuláře pro ukončení hry.

2. Dále má <xref:System.Windows.Forms.Control.Click> obslužná rutina události popisku zavolat novou `CheckForWinner()` metodu. Ujistěte se, že váš program kontroluje vítěze ihned po tom, co zobrazí druhou ikonu, kterou hráč vybere. Vyhledejte řádek, kde jste nastavili barvu druhé zvolené ikony, a potom zavolejte `CheckForWinner()` metodu hned po tom, jak je znázorněno v následujícím kódu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. Program uložte a spusťte jej. Zahrajte si hru a spárujte všechny ikony. Když nahrajete, program zobrazí congratulatory **MessageBox** (jak je znázorněno na následujícím snímku obrazovky) a pak okno zavře.

     ![Porovnávací hra s ovládacím prvkem MessageBox](../ide/media/express_tut4step8.png)<br/>
***Porovnávací hra** _ _With * ***MessageBox***

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek krok 9: Vyzkoušejte si další funkce](../ide/step-9-try-other-features.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md).
