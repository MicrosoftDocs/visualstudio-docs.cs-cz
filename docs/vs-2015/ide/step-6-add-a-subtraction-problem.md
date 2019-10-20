---
title: 'Krok 6: Přidání problému odčítání | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ec0bdd3ebae52158c5631a880e63ee0f3a455de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671715"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6: Přidejte problém odečtení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V šesté části tohoto kurzu přidáte problém odčítání a naučíte se, jak provádět následující úlohy:

- Uložte hodnoty odčítání.

- Vygenerujte náhodná čísla pro daný problém (a ujistěte se, že odpověď je mezi 0 a 100).

- Aktualizujte metodu, která zkontroluje odpovědi, aby vyhledá i nový problém odčítání.

- Aktualizujte obslužnou rutinu události Tick časovače tak, aby obslužná rutina události vyplnila správnou odpověď, když vyprší čas.

### <a name="to-add-a-subtraction-problem"></a>Přidání problému odčítání

1. Přidejte dvě celočíselné proměnné pro problém odčítání do formuláře mezi celočíselnými proměnnými pro daný problém sčítání a časovač. Kód by měl vypadat takto.

     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]

     Názvy nových celočíselných proměnných –**minuend** a **subtrahend**– nejedná se o programovací pojem. Jedná se o tradiční názvy aritmetické operace pro číslo, které se odečte (subtrahend), a číslo, ze kterého se odečte subtrahend (minuend). Rozdíl je minuend mínus subtrahend. Můžete použít jiné názvy, protože program nevyžaduje konkrétní názvy pro proměnné, ovládací prvky, komponenty nebo metody. Musíte dodržovat pravidla, jako je například nepočáteční názvy začínající číslicemi, ale obecně můžete použít názvy, například x1, X2, X3 a X4. Obecné názvy ale zjednodušují čtení kódu a problémy téměř nemožné sledovat. Aby názvy proměnných byly jedinečné a užitečné, použijte tradiční názvy pro násobení (multiplicand × násobitel = Product) a dělení (dělené ÷ dělitele = podíl) později v tomto kurzu.

     Dále upravíte metodu `StartTheQuiz()`, aby poskytovala náhodné hodnoty pro problém odčítání.

2. Přidejte následující kód za komentář "vyplňování problému při odčítání".

     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]

     Aby nedocházelo k negativním odpovědím na problém odčítání, tento kód používá metodu `Next()` `Random` třídy, která je trochu odlišná od způsobu, jakým je problém sčítání. Když podáte metodu `Next()` dvě hodnoty, vybere náhodné číslo, které je větší nebo rovno první hodnotě a menší než druhá hodnota. Následující kód zvolí náhodné číslo od 1 do 100 a uloží jej do proměnné minuend.

     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]

     Můžete volat metodu `Next()` třídy `Random`, kterou jste pojmenovali "randomizer" dříve v tomto kurzu, a to více způsoby. Metody, které lze volat více než jedním způsobem, jsou označovány jako přetížené a můžete je prozkoumat pomocí technologie IntelliSense. Vyhledejte znovu v popisku okna technologie IntelliSense pro metodu `Next()`.

     ![Popisek okna IntelliSense](../ide/media/express-overloads.png "Express_Overloads") Popisek okna IntelliSense

     Popis zobrazuje **(+ 2 přetížení)** , což znamená, že můžete volat metodu `Next()` dvěma dalšími způsoby. Přetížení obsahují odlišná čísla nebo typy argumentů, aby byly mírně odlišné od sebe. Například metoda může převzít jeden celočíselný argument, zatímco jedno z jeho přetížení může mít celočíselnou hodnotu a řetězec. Můžete zvolit správné přetížení na základě toho, co chcete udělat. Když přidáte kód do metody `StartTheQuiz()`, zobrazí se v okně IntelliSense Další informace hned po zadání `randomizer.Next(`. Pomocí šipek nahoru a dolů můžete cyklicky přepínat, jak ukazuje následující obrázek.

     ![Přetížení pro metodu&#40; &#41; Next v technologii IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload") Overload pro metodu Next () v IntelliSense

     V takovém případě chcete zvolit poslední přetížení, protože můžete zadat minimální a maximální hodnoty.

3. Upravte metodu `CheckTheAnswer()` pro kontrolu správné odpovědi na odčítání.

     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]

     V jazyce C#Visual je `&&` operátorem `logical and`. V Visual Basic je ekvivalentní operátor `AndAlso`. Tyto operátory označují "Pokud součet hodnot addend1 a addend2 se rovná hodnotě součtu NumericUpDown a pokud je minuend mínus subtrahend rovna hodnotě rozdílu NumericUpDown." Metoda `CheckTheAnswer()` vrátí `true` pouze v případě, že odpovědi na problémy sčítání a odčítání jsou správné.

4. Poslední část obslužné rutiny události Tick časovače nahraďte následujícím kódem, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]

5. Uložte a spusťte kód.

     Váš program zahrnuje problém odčítání, jak ukazuje následující obrázek.

     ![Matematický kvíz s problémem odčítání](../ide/media/express-addsubtract.png "Express_AddSubtract") Matematický kvíz s problémem odčítání

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít k dalšímu kroku kurzu, přečtěte si [článek krok 7: Přidání problémů násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md).

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 5: Přidání obslužných rutin událostí Enter pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
