---
title: 'Krok 7: Přidání součástí dialogového okna do formuláře'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9697bf6cf84c2a74daac2017b4f63d52a7019b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579276"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7: Přidání součástí dialogu do formuláře

Chcete-li aplikaci povolit otevírání souborů obrázků a výběr <xref:System.Windows.Forms.OpenFileDialog> barvy pozadí, přidejte v tomto kroku do formuláře komponentu a komponentu. <xref:System.Windows.Forms.ColorDialog>

Komponenta je v některých ohledech jako ovládací prvek. Panel **nástrojů** slouží k přidání součásti do formuláře a nastavení jejích vlastností pomocí okna **Vlastnosti.** Na rozdíl od ovládacího prvku však přidání komponenty do formuláře nepřidá viditelnou položku, kterou uživatel uvidí ve formuláři. Místo toho poskytuje určité chování, které můžete aktivovat s kódem. Jedná se o součást, která otevře dialogové okno **Otevřít soubor.**

## <a name="to-add-dialog-components-to-your-form"></a>Přidání součástí dialogu do formuláře

1. Zvolte **Návrháře formulářů systému Windows** (**Form1.cs [Design]**) a potom otevřete skupinu **Dialogy** v **panelu nástrojů**.

    > [!NOTE]
    > Skupina **Dialogy** v **panelu nástrojů** obsahuje komponenty, které pro vás otevírají mnoho užitečných dialogových oken, která lze použít k otevírání a ukládání souborů, procházení složek a výběru písem a barev. V tomto projektu se používají dvě součásti dialogu: OpenFileDialog a ColorDialog.

1. Chcete-li do formuláře přidat součást nazvanou **openFileDialog1,** poklepejte na **položku OpenFileDialog**. Chcete-li do formuláře přidat součást nazvanou **colorDialog1,** poklepejte v **panelu nástrojů**na **položku ColorDialog** . (Tento použijete v dalším kroku kurzu.) V dolní části **Návrháře formulářů systému Windows** (pod formulářem **Prohlížeč obrázků)** byste měli vidět oblast, která obsahuje ikonu pro každou ze dvou součástí dialogového okna, kterou jste přidali, jak je znázorněno na následujícím obrázku.

     ![Komponenty dialogu](../ide/media/express_dialogsadded.png)<br>***Komponenty*** *dialogu*

1. Zvolte ikonu **openFileDialog1** v oblasti v dolní části **Návrháře formulářů systému Windows**. Nastavte dvě vlastnosti:

    - Nastavte vlastnost **Filter** na následující (můžete ji zkopírovat a vložit):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Nastavení vlastnosti **Title** na následující: **Výběr souboru obrázku**

         Nastavení vlastností **Filtr** určuje typy typů souborů, které se zobrazí v dialogovém okně Vybrat soubor **obrázku.**

    > [!TIP]
    > Chcete-li zobrazit příklad dialogového okna **Otevřít soubor** v jiné aplikaci, otevřete **Poznámkový blok** nebo **malování**a na řádku nabídek zvolte **Otevřít soubor** > **.** Všimněte si, jak je vedle názvu souboru rozevírací seznam, který umožňuje zvolit typ souboru. <br/><br/>Právě jste použili vlastnost **Filter** v komponentě **OpenFileDialog** k nastavení, která je ve vaší aplikaci. Všimněte si také, jak title **a** **filter** vlastnosti jsou tučně v okně **Vlastnosti.** IDE to dělá, aby vám ukázal všechny vlastnosti, které byly změněny z jejich výchozí hodnoty.

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít k dalšímu kroku kurzu, **[přečtěte si krok 8: Napište kód pro obslužnou rutinu události tlačítka zobrazit obrázek](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si číslo 6: Pojmenujte ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
