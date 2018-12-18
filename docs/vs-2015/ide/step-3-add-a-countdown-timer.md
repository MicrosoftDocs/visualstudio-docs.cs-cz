---
title: 'Krok 3: Přidejte časovač odpočítávání | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bbbc5e7de56e3ab03976b1933895035913bb7d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228147"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3: Přidejte časovač odpočítávání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve třetí části tohoto kurzu přidáte časovač odpočítávání ke sledování počtu sekund pro dokončení kvízu.  
  
> [!NOTE]
>  Toto téma je součástí série kurzů o základních principech kódování. Přehled kurzu, naleznete v tématu [kurz 2: vytvoření a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-add-a-countdown-timer"></a>Chcete-li přidat časovač odpočítávání  
  
1.  Přidejte celočíselnou proměnnou s názvem **timeLeft**, stejně jako v předchozím postupu. Váš kód by měl vypadat nějak takto.  
  
     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]  
  
     Teď budete potřebovat metodu, která ve skutečnosti vrátí počet sekund, jako je například časovač, což vyvolá událost po dobu, kterou zadáte.  
  
2.  V okně návrhu přesuňte `Timer` ovládacího prvku **součásti** kategorie panelu nástrojů do formuláře.  
  
     Ovládací prvek se zobrazí v šedé oblasti v dolní části okna návrhu.  
  
3.  Ve formuláři, zvolte **timer1** ikonu, která jste právě přidali a nastavte jeho **Interval** vlastnost **1000**.  
  
     Vzhledem k tomu, že hodnota intervalu jsou milisekund, hodnota 1000 způsobí, že událost Tick je vyvolána každou sekundu.  
  
4.  Ve formuláři poklepejte na ovládací prvek časovače, nebo ho vyberte a stiskněte klávesu Enter.  
  
     Zobrazí se editor kódu a metoda obslužné rutiny události Tick, kterou jste právě přidali.  
  
5.  Přidejte následující příkazy do nové metody obslužné rutiny události.  
  
     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]  
  
     Na základě toho, co jste přidali, každou sekundu časovač zkontroluje, jestli se má spustit tak, že určíte, zda **timeLeft** celočíselná proměnná je větší než 0. Pokud se jedná, doba stále trvá. Časovač se nejprve odečte 1 z proměnné timeLeft a poté aktualizuje **Text** vlastnost `timeLabel` ovládacího prvku na kvízu zobrazit, kolik sekund uživateli.  
  
     Jestliže nezbývá žádný čas, časovač se zastaví a změní se text `timeLabel` tak, aby zobrazuje **čas vypršel!** Okno se zprávou oznamuje, že kvíz a odpověď je odhalena – v tomto případě přidáním addend1 a addend2. **Povoleno** vlastnost `startButton` ovládacího prvku nastavená na `true` tak, aby kvízu, mohl spustit další kvíz.  
  
     Právě jste přidali `if else` příkazu, který je, jak můžete programům sdělujete, abyste se mohli rozhodovat. `if else` Příkaz vypadá takto.  
  
    > [!NOTE]
    >  Následující příklad je pouze pro ilustraci – nepřidávejte ho do projektu.  
  
    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  
  
    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  
  
     Prohlédněte si blíže příkaz, který jste přidali v kroku `else` blok k zobrazení odpovědi na úlohu sčítání.  
  
     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]  
  
     Příkaz `addend1 + addend2` sečte hodnoty obou proměnných společně. První část (`sum.Value`) používá **hodnotu** vlastnost `NumericUpDown` ovládací prvek pro zobrazení správné odpovědi. Stejnou vlastnost můžete použít později ke zkontrolování odpovědi kvízu.  
  
     Uživatelé vyplňující kvíz mohou zadávat čísla snadněji pomocí `NumericUpDown` ovládací prvek, který je důvod, proč ho použijete pro odpovědi na matematické úlohy. Všechny možné odpovědi jsou celá čísla od 0 do 100. Ponechte výchozí hodnoty **minimální**, **maximální**, a **počet desetinných míst** , zajistíte, že uživatelům vyplňujícím kvíz nelze zadat desetinná čísla, záporná čísla, nebo čísla, která jsou příliš vysoká. (Pokud jste chtěli povolit uživatelům vyplňujícím kvíz zadání hodnoty 3,141, ale nikoli 3,1415, můžete nastavit **počet desetinných míst** vlastnost na 3.)  
  
6.  Přidejte tři řádky na konec objektu `StartTheQuiz()` metoda, takže kód vypadá následovně.  
  
     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]  
  
     Teď, když spustíte kvíz, **timeLeft** proměnná je nastavená na 30 a **Text** vlastnost `timeLabel` řízení je nastavené na 30 sekund. Pak bude `Start()` metodu `Timer` ovládací prvek spustí odpočítávání. (Kvíz zatím kontrolu odpovědi –, který obsahuje další.)  
  
7.  Uložte program, spusťte ho a klikněte na tlačítko **Start** tlačítko na formuláři.  
  
     Časovač spustí odpočet. Když čas vyprší, kvíz skončí a zobrazí se odpověď. Následující obrázek znázorňuje probíhající kvíz.  
  
     ![Probíhající matematický kvíz](../ide/media/express-addcountdown.png "Express_AddCountdown")  
Probíhající matematický kvíz  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 4: Přidejte metodu CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 2: Vytvořte náhodný problém s přidáním](../ide/step-2-create-a-random-addition-problem.md).



