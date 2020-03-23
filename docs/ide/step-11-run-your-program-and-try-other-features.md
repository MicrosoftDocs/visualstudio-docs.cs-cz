---
title: 'Krok 11: Spuštění aplikace prohlížeče obrázků a vyzkoušení dalších funkcí'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579903"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Krok 11: Spuštění aplikace prohlížeče obrázků a vyzkoušení dalších funkcí

Aplikace prohlížeče obrázků je hotová a připravená ke spuštění. Aplikaci můžete spustit a nastavit barvu <xref:System.Windows.Forms.PictureBox>pozadí aplikace . Chcete-li se dozvědět více, zkuste aplikaci vylepšit změnou barvy formuláře, přizpůsobením tlačítek a zaškrtávacího políčka a změnou vlastností formuláře.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Jak spustit aplikaci a nastavit barvu pozadí

1. Zvolte **F5**nebo na řádku nabídek zvolte **Ladění** > **ladění startování**.

1. Před otevřením obrázku zvolte **tlačítko Nastavit barvu pozadí.** Otevře se dialogové okno **Barva.**

     ![Dialogové okno Barva](../ide/media/express_colordialog.png)<br/>
***Color*** *Dialogové okno* Barva

1. Zvolte barvu, kterou chcete nastavit barvu pozadí PictureBoxu. Podívejte se `backgroundButton_Click()` pozorně na `BackgroundButton_Click()`(nebo) metoda pochopit, jak to funguje.

    > [!NOTE]
    > Obrázek z Internetu můžete načíst vložením jeho adresy URL do dialogového okna **Otevřít soubor.** Pokuste se najít obrázek s průhledným pozadím, aby se barva pozadí zosazena.

1. Zvolte tlačítko **Vymazat obrázek,** abyste se ujistili, že se vymaže. Potom aplikaci ukončete výběrem tlačítka **Zavřít.**

## <a name="try-other-features"></a>Vyzkoušení dalších funkcí

* Změňte barvu formuláře a tlačítek pomocí vlastnosti **BackColor.**

* Přizpůsobte si tlačítka a zaškrtávací políčko pomocí **vlastností Písmo** a **Barva ForeColor.**

* Změňte vlastnosti **FormBorderStyle** a **ControlBox** formuláře.

* Použijte vlastnosti **AcceptButton** a **CancelButton** formuláře, aby byla tlačítka automaticky vybrána, když uživatel zvolí klávesu **Enter** nebo **Esc.** Otevřete aplikaci dialogové okno **Otevřít soubor,** když uživatel zvolí **Enter** a zavře ho, když uživatel zvolí **Esc**.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md)

Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 10: Napsat kód pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Viz také

* [Další výukové programy pro C#](/visualstudio/get-started/csharp/)
* [Další výukové programy jazyka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Kurz pro C++](/cpp/get-started/tutorial-console-cpp)
