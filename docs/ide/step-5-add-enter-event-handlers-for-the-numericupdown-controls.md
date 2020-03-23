---
title: 'Krok 5: Přidání obslužných rutin událostí Enter pro ovládací prvky NumericUpDown'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17fb9ba8e82739ddb0a420f52b6f7f945a6454b8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579828"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5: Přidání obslužných rutin událostí Enter pro ovládací prvky NumericUpDown

V páté části tohoto kurzu přidáte <xref:System.Windows.Forms.Control.Enter> obslužné rutiny událostí, aby bylo zadávání odpovědí na problémy s kvízy o něco jednodušší. Tento kód vybere a vymaže aktuální hodnotu v každém <xref:System.Windows.Forms.NumericUpDown> ovládacím prvku, jakmile si ho příjemce kvízu vybere a začne zadávat jinou hodnotu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Ověření výchozího chování

1. Spusťte program a spusťte kvíz.

     V **ovládacím prvku NumericUpDown** pro problém s přidáním kurzor bliká vedle **0** (nula).

2. Zadejte **3**a všimněte si, že ovládací prvek zobrazuje **30**.

3. Zadejte **hodnotu 5**a všimněte si, že se zobrazí **350,** ale po sekundě se změní na **100.**

     Než tento problém vyřešíte, zamyslete se nad tím, co se děje. Zvažte, proč **0** nezmizela, když jste zadali **3** a proč **350** změnil na **100,** ale ne okamžitě.

     Toto chování se může zdát divné, ale dává smysl vzhledem k logice kódu. Když zvolíte tlačítko **Start,** jeho **Vlastnost Povoleno** je nastavena na **False**a tlačítko se zobrazí šedě a není k dispozici. Program změní aktuální výběr (fokus) na ovládací prvek, který má další nejnižší TabIndex hodnotu, což je NumericUpDown ovládací prvek pro přidání problém. Při použití **klávesy Tab** přejít na ovládací prvek NumericUpDown, kurzor je automaticky umístěn na začátku ovládacího prvku, což je důvod, proč čísla, která zadáte se zobrazí z levé strany a ne na pravé straně. Zadáte-li číslo, které je vyšší než hodnota **vlastnosti MaximumValue,** která je nastavena na hodnotu 100, zadané číslo bude nahrazeno hodnotou této vlastnosti.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Přidání obslužné rutiny události Enter pro ovládací prvek NumericUpDown

1. Zvolte první ovládací prvek **NumericUpDown** (s názvem "sum") ve formuláři a pak v dialogovém okně **Vlastnosti** zvolte ikonu **Události** na panelu nástrojů.

   ![Tlačítko Události v pruhu nástrojů vlastností](media/control-properties-events.png)

   Karta **Události** v dialogovém okně **Vlastnosti** zobrazuje všechny události, na které můžete reagovat (zpracovat) pro položku, kterou zvolíte ve formuláři. Vzhledem k tomu, že jste zvolili numericupdown ovládací prvek, všechny uvedené události se k němu vyhovují.

2. Zvolte **Enter** událost, zadejte `answer_Enter`a stiskněte klávesu **Enter.**

   ![Zadejte název metody obslužné rutiny události.](media/enter-event.png)

   Právě jste přidali obslužnou rutinu události Enter pro ovládací prvek SumUpDown a obslužnou rutinu jste pojmenovali **answer_Enter**.

3. V metodě pro obslužnou rutinu události **answer_Enter** přidejte následující kód:

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Tento kód může vypadat složitě, ale můžete pochopit, pokud se na něj podíváte krok za krokem. Nejprve se podívejte na začátek `object sender` metody: `sender As System.Object` v jazyce C# nebo v jazyce Visual Basic. Tento parametr odkazuje na objekt, jehož událost je spouštění, který je známý jako odesílatel. V tomto případě je objektodesílatelem ovládací prvek NumericUpDown. Takže v prvním řádku metody určíte, že odesílatel není pouze libovolný obecný objekt, ale konkrétně ovládací prvek NumericUpDown. (Každý ovládací prvek NumericUpDown je objekt, ale ne každý objekt je ovládací prvek NumericUpDown.) Ovládací prvek NumericUpDown má v této metodě název **answerBox,** protože bude použit pro všechny ovládací prvky NumericUpDown ve formuláři, nikoli pouze pro ovládací prvek SumUpDown. Vzhledem k tomu, že deklarujete proměnnou answerBox v této metodě, její obor se vztahuje pouze na tuto metodu. Jinými slovy, proměnnou lze použít pouze v rámci této metody.

     Další řádek ověří, zda answerBox byl úspěšně převeden (přetypován) z objektu na ovládací prvek NumericUpDown. Pokud byl převod neúspěšný, proměnná by `null` měla hodnotu `Nothing` (C#) nebo (Visual Basic). Třetí řádek získá délku odpovědi, která se zobrazí v ovládacím prvku NumericUpDown a čtvrtý řádek vybere aktuální hodnotu v ovládacím prvku na základě této délky. Nyní, když příjemce kvízu vybere ovládací prvek, Visual Studio spustí tuto událost, která způsobí, že aktuální odpověď, která má být vybrána. Jakmile příjemce kvízu začne zadávat jinou odpověď, předchozí odpověď je vymazána a nahrazena novou odpovědí.

4. V **Návrháři formulářů systému Windows**zvolte ovládací prvek **NumericUpDown.**

5. Na stránce **Události** v dialogovém okně **Vlastnosti** přejděte dolů na událost **Enter,** zvolte šipku `answer_Enter` rozevíracího seznamu na konci řádku a pak zvolte obslužnou rutinu události, kterou jste právě přidali.

6. Opakujte předchozí krok pro ovládací prvky produktu a kvocientu NumericUpDown.

7. Uložte program a spusťte jej.

     Když zvolíte ovládací prvek **NumericUpDown,** existující hodnota se automaticky vybere a po zahájení zadání jiné hodnoty se ponese zaškrtnutí.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud jde o další krok kurzu, **[přečtěte si číslo 6: Přidání problému s odčítáním](../ide/step-6-add-a-subtraction-problem.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si postup 4: Přidání metody CheckTheAnswer().](../ide/step-4-add-the-checktheanswer-parens-method.md)
