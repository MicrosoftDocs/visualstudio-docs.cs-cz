---
title: 'Krok 8: Přidejte metodu k ověření, zda hráč zvítězil | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2481693961dd03815381e9f71ee67cb73464bdf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646931"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Přidejte metodu k ověření, zda hráč vyhrál
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvořili jste zábavnou hru, která však potřebuje ještě něco. Hra by měla skončit, když je přehrávač WINS, takže pokud chcete ověřit, zda hráč zvítězil, je třeba přidat metodu `CheckForWinner()`.

### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Přidání metody k ověření, zda hráč zvítězil

1. Do dolní části kódu přidejte `CheckForWinner()` metodu, která je pod obslužnou rutinou události `timer1_Tick()`, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]

     Metoda používá jinou `foreach` smyčku v jazyce C# Visual nebo `For Each` smyčka v Visual Basic k tomu, aby procházela každým popiskem v kontejneru TableLayoutPanel. Používá operátor rovnosti (`==` v jazyce Visual C# a `=` v Visual Basic) ke kontrole barvy ikony jednotlivých popisků a k ověření, zda odpovídá pozadí. Pokud se barvy shodují, zůstane ikona skryta a hráč nespároval všechny zbývající ikony. V takovém případě program používá příkaz `return` k přeskočení zbytku metody. Pokud smyčka projde všemi štítky bez provedení příkazu `return`, znamená to, že všechny ikony ve formuláři byly spárovány. Program zobrazí MessageBox, aby congratulate přehrávač při výhrě, a potom zavolá metodu `Close()` formuláře pro ukončení hry.

2. Dále má obslužná rutina události Click popisku zavolat novou metodu `CheckForWinner()`. Ujistěte se, že váš program kontroluje vítěze ihned po tom, co zobrazí druhou ikonu, kterou hráč vybere. Vyhledejte řádek, kde jste nastavili barvu druhé zvolené ikony, a potom zavolejte metodu `CheckForWinner()` hned po tom, jak je znázorněno v následujícím kódu.

     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]

3. Program uložte a spusťte jej. Zahrajte si hru a spárujte všechny ikony. Když vyhrajete, program zobrazí prvek MessageBox s blahopřáním (jak je ukázáno na následujícím obrázku) a potom jej zavře.

     ![Porovnávací hra s MessageBox](../ide/media/express-tut4step8.png "Express_Tut4Step8") Porovnávací hra s MessageBox

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 9: Vyzkoušejte si další funkce](../ide/step-9-try-other-features.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 7: zůstat páry viditelné](../ide/step-7-keep-pairs-visible.md).
