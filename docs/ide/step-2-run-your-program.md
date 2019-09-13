---
title: 'Krok 2: Spuštění aplikace pro prohlížeč obrázků'
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6c7e90f8113f5fa03da907db5dbb8f374a564e7
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887916"
---
# <a name="step-2-run-your-picture-viewer-app"></a>Krok 2: Spuštění aplikace pro prohlížeč obrázků

Když vytváříte projekt aplikace model Windows Forms, ve skutečnosti vytvoříte program, který běží. V tomto kurzu aplikace pro prohlížení obrázků nepracuje mnohem ještě&mdash;daleko, i když to bude. Prozatím zobrazí prázdné okno, které zobrazuje **Form1** v záhlaví.

Tady je postup, jak aplikaci spustit. 

1. Vyberte jednu z následujících metod:

    - Klikněte na klávesu **F5** .

    - Na panelu nabídek vyberte **ladit** > **Spustit ladění**.

    - Na panelu nástrojů klikněte na tlačítko **Spustit ladění** , které se zobrazí takto:

      ![Spustit ladění – tlačítko panelu nástrojů](../ide/media/express_icondebug.png)<br>
      ***Spustit ladění*** *tlačítko panelu nástrojů*

1. Visual Studio spustí vaši aplikaci a zobrazí se okno s názvem **Form1** . Na následujícím snímku obrazovky vidíte aplikaci, kterou jste právě sestavili. Aplikace je spuštěná a později do ní přidáte.

     ![Spuštěná aplikace model Windows Forms](../ide/media/express_firstrun.png)<br>
***Aplikace model Windows Forms***, *spuštěné*

1. Vraťte se do integrovaného vývojového prostředí (IDE) sady Visual Studio a podívejte se na nový panel nástrojů. Další tlačítka se zobrazí na panelu nástrojů při spuštění aplikace. Tato tlačítka umožňují provádět akce, jako je zastavení a spuštění vaší aplikace, a umožňují vám sledovat případné chyby, které může mít. V tomto příkladu ho používáme ke spuštění a zastavení aplikace.

     ![Panel nástrojů ladění](../ide/media/express_debugtoolbar.png)<br>
***Ladění*** *panel nástrojů*

1. K zastavení vaší aplikace použijte jednu z následujících metod:

    - Na panelu nástrojů klikněte na tlačítko **Zastavit ladění** .

    - Na řádku nabídek klikněte na položku **ladit** > **Zastavit ladění**.

    - Použijte klávesnici a stiskněte **SHIFT**+**F5**.

    - Klikněte na tlačítko **X** v horním rohu okna **Form1** .

    > [!NOTE]
    > Když aplikaci spouštíte zevnitř rozhraní IDE, nazývá se to ladění, protože to obvykle provedete tak, že v aplikaci vyhledáte a opravíte chyby (chyby). I když je tato aplikace malá a ve skutečnosti ještě nic nedělá, je to stále skutečný program. Stejný postup můžete použít ke spuštění a ladění dalších programů. Další informace o ladění naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Další postup

* Pokud chcete přejít na další krok kurzu,  **[přejděte na krok 3: Nastavte vlastnosti](../ide/step-3-set-your-form-properties.md)** formuláře.

* Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si téma krok 1: Vytvořte projekt](../ide/step-1-create-a-windows-forms-application-project.md)aplikace model Windows Forms.

## <a name="see-also"></a>Viz také:

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: Vytvořit porovnávací hru](tutorial-3-create-a-matching-game.md)
