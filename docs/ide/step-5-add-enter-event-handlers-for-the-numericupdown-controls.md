---
title: 'Krok 5: Přidat obslužné rutiny událostí Enter pro ovládací prvky NumericUpDown'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9566e5bb8bd5be3c1a44ff79690fb1f8107b40f9
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079468"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5: Přidání obslužných rutin událostí Enter pro ovládací prvky NumericUpDown

V páté části tohoto kurzu přidáte <xref:System.Windows.Forms.Control.Enter> obslužné rutiny událostí, aby bylo možné zadat odpovědi na otázky kvízu, které jsou poněkud jednodušší. Tento kód vybere a vymaže aktuální hodnotu v každém <xref:System.Windows.Forms.NumericUpDown> ovládacím prvku, jakmile ho si ten vybere a začne zadat jinou hodnotu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování.
> - Přehled tohoto kurzu najdete v [kurzu 2: Vytvoření časovaného matematického](../ide/tutorial-2-create-a-timed-math-quiz.md)kvízu
> - Chcete-li stáhnout dokončenou verzi kódu, přečtěte si [ukázku kurzu dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-verify-the-default-behavior"></a>Ověření výchozího chování

1. Spusťte program a spusťte kvíz.

     V ovládacím prvku **NumericUpDown** pro problém sčítání se kurzor bliká vedle **0** (nula).

2. Zadejte **3**a Všimněte si, že ovládací prvek zobrazuje **30**.

3. Zadejte **5**a Všimněte si, že **350** se zobrazí, ale po druhém se změní na **100** .

     Než vyřešíte tento problém, zamyslete se nad tím, co se děje. Zvažte, proč **0** nezmizí, když jste zadali **3** a proč **350** změněno na **100** , ale ne okamžitě.

     Toto chování se může zdát liché, ale dává smysl na základě logiky kódu. Když kliknete na tlačítko **Start** , vlastnost **Enabled** je nastavena na **hodnotu false**a tlačítko se zobrazí jako neaktivní a není k dispozici. Program změní aktuální výběr (fokus) na ovládací prvek, který má další nejnižší hodnotu TabIndex, což je ovládací prvek NumericUpDown pro daný problém sčítání. Když použijete klávesu **TAB** k přechodu do ovládacího prvku NumericUpDown, kurzor je automaticky umístěn na začátku ovládacího prvku, což je důvod, proč se čísla, která zadáte, zobrazí na levé straně a ne na pravé straně. Když zadáte číslo, které je vyšší než hodnota vlastnosti **vlastnosti MaximumValue** , která je nastavená na 100, číslo, které zadáte, se nahradí hodnotou této vlastnosti.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Přidání obslužné rutiny události Enter pro ovládací prvek NumericUpDown

1. Zvolte první ovládací prvek **NumericUpDown** (s názvem "Sum") ve formuláři a potom v dialogovém okně **vlastnosti** zvolte ikonu **události** na panelu nástrojů.

   ![Tlačítko události na panelu nástrojů vlastnosti](media/control-properties-events.png)

   Karta **události** v dialogovém okně **vlastnosti** zobrazí všechny události, na které můžete reagovat (popisovač) pro položku, kterou zvolíte ve formuláři. Vzhledem k tomu, že jste zvolili ovládací prvek NumericUpDown, vztahují se na něj všechny uvedené události.

2. Zvolte událost **ENTER** , zadejte `answer_Enter`a potom stiskněte klávesu **ENTER** .

   ![Zadejte název metody obslužné rutiny události.](media/enter-event.png)

   Právě jste přidali obslužnou rutinu události Enter pro součtový ovládací prvek NumericUpDown a pojmenovali jste obslužnou rutinu **answer_Enter**.

3. V metodě pro obslužnou rutinu události **answer_Enter** přidejte následující kód:

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Tento kód může vypadat složitě, ale můžete ho pochopit, pokud se podíváte na krok za krokem. Nejprve se podívejte na horní část metody: `object sender` v C# nebo `sender As System.Object` v Visual Basic. Tento parametr odkazuje na objekt, jehož událost se vyvolává, což se označuje jako odesilatel. V tomto případě je objekt odesílatel ovládacího prvku NumericUpDown. Takže v prvním řádku metody určíte, že odesílatel není pouze obecný objekt, ale konkrétně ovládací prvek NumericUpDown. (Každý ovládací prvek NumericUpDown je objekt, ale ne každý objekt je ovládací prvek NumericUpDown.) Ovládací prvek NumericUpDown má v této metodě název **answerBox** , protože bude použit pro všechny ovládací prvky NumericUpDown ve formuláři, nikoli pouze pro součet ovládacího prvku NumericUpDown. Vzhledem k tomu, že v této metodě deklarujete proměnnou answerBox, její obor se vztahuje pouze na tuto metodu. Jinými slovy proměnné lze použít pouze v rámci této metody.

     Další řádek ověří, zda answerBox byl úspěšně převeden (přetypování) z objektu na ovládací prvek NumericUpDown. Pokud převod nebyl úspěšný, proměnná by měla hodnotu `null` (C#) nebo `Nothing` (Visual Basic). Třetí řádek získá délku odpovědi, která se zobrazí v ovládacím prvku NumericUpDown, a čtvrtá čára vybere aktuální hodnotu v ovládacím prvku na základě této délky. Teď, když si autor kvízu zvolí ovládací prvek, Visual Studio aktivuje tuto událost, což způsobí, že se vybere aktuální odpověď. Jakmile si autor kvízu začne zadávat jinou odpověď, předchozí odpověď je vymazána a nahrazena novou odpovědí.

4. V **Návrhář formulářů**vyberte rozdílový ovládací prvek **NumericUpDown** .

5. Na stránce **události** v dialogovém okně **vlastnosti** se posuňte dolů k události **ENTER** , klikněte na šipku rozevíracího seznamu na konci řádku a zvolte `answer_Enter` obslužnou rutinu události, kterou jste právě přidali.

6. Opakujte předchozí krok pro produkt a podíl ovládacího prvku NumericUpDown.

7. Uložte program a spusťte jej.

     Když vyberete ovládací prvek **NumericUpDown** , stávající hodnota se automaticky vybere a po zahájení zadávání jiné hodnoty se vymaže.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si  **[krok 6: Přidejte problém](../ide/step-6-add-a-subtraction-problem.md)** odčítání.

- Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 4: Přidejte metodu](../ide/step-4-add-the-checktheanswer-parens-method.md)metodu CheckTheAnswer ().
