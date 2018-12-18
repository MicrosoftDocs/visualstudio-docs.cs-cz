---
title: 'Krok 5: Přidejte obslužné rutiny událostí Enter pro ovládací prvky NumericUpDown | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a87704f7d836da2309e711f3379df01b01c807c2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294486"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5: Přidejte obslužné rutiny události pro ovládací prvky NumericUpDown
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V páté části tohoto tutoriálu přidáte obslužné rutiny událostí Enter pro trochu usnadnili zadávání odpovědí pro kvíz. Tento kód vybere a vymaže aktuální hodnotu v každém ovládacím prvku NumericUpDown, jakmile kvízu vybere a začne zadávat jinou hodnotu.  
  
> [!NOTE]
>  Toto téma je součástí série kurzů o základních principech kódování. Přehled kurzu, naleznete v tématu [kurz 2: vytvoření a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-verify-the-default-behavior"></a>Ověření výchozího chování  
  
1.  Spusťte program a spusťte kvíz.  
  
     V ovládacím prvku NumericUpDown pro sčítání bliká kurzor vedle **0** (nula).  
  
2.  Zadejte `3`a Všimněte si, že ovládací prvek zobrazuje **30**.  
  
3.  Zadejte `5`a Všimněte si, že **350** se zobrazí, ale změny **100** po druhém.  
  
     Než vyřešíte tento problém, rozmyslete si, co se děje. Zvažte, proč **0** nezmizela poté zadáte `3` a proč **350** změněn na **100** , ale nikoliv okamžitě.  
  
     Toto chování se může zdát neobvyklé, ale dává smysl s ohledem logiku kódu. Při výběru možnosti **Start** tlačítko, jeho **povoleno** je nastavena na **False**, a tlačítko se zobrazí šedě a není k dispozici. Váš program změní aktuální výběr (Přepne fokus) na ovládací prvek s další nejnižší hodnotou TabIndex, což je ovládací prvek NumericUpDown pro úlohu sčítání. Při použití klávesy Tab k přechodu na ovládací prvek NumericUpDown, se automaticky kurzor na začátek ovládacího prvku, což je důvod, proč čísla, která zadáte budou zobrazovat v levé straně a nikoli vpravo. Pokud zadáte číslo vyšší než hodnota **MaximumValue** vlastnost, která je nastavena na hodnotu 100, číslo, které jste zadali je nahrazena hodnotou této vlastnosti.  
  
### <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Chcete-li přidat obslužné rutiny událostí Enter pro ovládací prvek NumericUpDown  
  
1.  Zvolte první ovládací prvek NumericUpDown (s názvem "SUMA") ve formuláři a potom v **vlastnosti** dialogového okna zvolte **události** ikonu na panelu nástrojů.  
  
     **Události** kartu **vlastnosti** dialogové okno zobrazí všechny události, které můžete reagovat (zpracovat) pro položku, kterou zvolíte ve formuláři. Vzhledem k tomu, že jste zvolili ovládací prvek NumericUpDown, přísluší všechny uvedené události k němu.  
  
2.  Zvolte **Enter** události, zadejte `answer_Enter`a potom stiskněte klávesu Enter.  
  
     ![Dialogové okno Vlastnosti](../ide/media/express-answerenter.png "Express_AnswerEnter")  
Dialogové okno Vlastnosti  
  
     Právě jste přidali obslužné rutiny událostí Enter pro součtový ovládací prvek NumericUpDown a pojmenovali jste obslužnou rutinu **answer_Enter**.  
  
3.  V metodě pro **answer_Enter** obslužná rutina události, přidejte následující kód.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial3Step5_6#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#11)]  
  
     Tento kód může vypadat složité, ale lze jej pochopit, když se podíváte na něj krok za krokem. Nejprve se podívejte na horní část metody: `object sender` v jazyce C# nebo `sender As System.Object` v jazyce Visual Basic. Tento parametr odkazuje na objekt, jehož událost je vyvolávána, který je znám jako odesílatel. V takovém případě objekt odesílatel je ovládací prvek NumericUpDown. V prvním řádku metody, tedy zadáte, že odesílatel není pouze obecný objekt, ale specificky ovládací prvek NumericUpDown. (Každý ovládací prvek NumericUpDown je objekt, ale ne každý objekt je ovládací prvek NumericUpDown.) NumericUpDown – ovládací prvek má název **answerBox** v této metodě, protože se použije pro všechny ovládací prvky NumericUpDown ve formuláři, nikoli pouze pro součtový ovládací prvek. Vzhledem k tomu, že deklarujete proměnnou answerBox v této metodě, její obor platí pouze pro tuto metodu. Jinými slovy proměnné lze použít pouze v rámci této metody.  
  
     Další řádek ověří, zda byl answerBox úspěšně převeden (přetypován) z objektu na NumericUpDown ovládací prvek. Pokud převod neúspěšný, proměnné by mít hodnotu `null` (C#) nebo `Nothing` (Visual Basic). Třetí řádek získá délku odpovědi, která se zobrazí v ovládacím prvku NumericUpDown, a čtvrtý řádek vybere aktuální hodnotu v ovládacím prvku v závislosti na této délce. Nyní když kvízu vybere ovládací prvek, sady Visual Studio vyvolá tuto událost, což způsobí, že aktuální odpovědi má být vybrán. Jakmile kvízu začne zadávat různé odpovědi, předchozí odpověď je vymazána a nahrazena novou odpovědí.  
  
4.  V Návrháři Windows Forms vyberte rozdíl ovládacího prvku NumericUpDown.  
  
5.  V **události** stránce **vlastnosti** dialogové okno, posuňte se dolů **Enter** události, klikněte na šipku rozevíracího seznamu na konci řádku a klikněte na tlačítko `answer_Enter`obslužná rutina události, který jste právě přidali.  
  
6.  Opakujte předchozí krok pro násobící a podílové ovládací prvky NumericUpDown.  
  
7.  Uložte program a spusťte jej.  
  
     Když vyberete ovládací prvek NumericUpDown, existující hodnota se vybere automaticky a potom vymazána po spuštění zadat jiné hodnoty.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 6: přidejte problém odečtení](../ide/step-6-add-a-subtraction-problem.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 4: Přidejte metodu CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).



