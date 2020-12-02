---
title: 'Krok 7: přidejte do svého formuláře komponenty dialogových oken'
description: Naučte se, jak přidat <xref:System.Windows.Forms.OpenFileDialog> komponentu dialogového okna a <xref:System.Windows.Forms.ColorDialog> komponentu dialogového okna do formuláře.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 37cbd2ca1f0207eaf2a41f6a08248bcedcfbe5bb
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479469"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7: Přidání komponent dialogových oken do formuláře

Chcete-li aplikaci povolit, aby otevírala soubory obrázků a zvolila barvu pozadí, v tomto kroku přidáte <xref:System.Windows.Forms.OpenFileDialog> komponentu a <xref:System.Windows.Forms.ColorDialog> komponentu do formuláře.

Komponenta je jako ovládací prvek v některých způsobech. Pomocí **panelu nástrojů** přidáte komponentu do formuláře a nastavíte její vlastnosti pomocí okna **vlastnosti** . Ale na rozdíl od ovládacího prvku, přidání komponenty do formuláře nepřidá viditelnou položku, kterou může uživatel zobrazit ve formuláři. Místo toho poskytuje určité chování, které lze aktivovat pomocí kódu. Je to komponenta, která otevře dialogové okno **otevřít soubor** .

## <a name="to-add-dialog-components-to-your-form"></a>Přidání součástí dialogového okna do formuláře

1. Zvolte **Návrhář formulářů** (**Form1.cs [Design]**) a pak otevřete skupinu **dialogy** v sadě **nástrojů**.

    > [!NOTE]
    > Skupina **dialogová okna** v **sadě nástrojů** obsahuje komponenty, které otevřou spoustu užitečných dialogových oken, které lze použít pro otevírání a ukládání souborů, procházení složek a výběr písma a barev. V tomto projektu použijete dvě komponenty dialogového okna: OpenFileDialog a ColorDialog.

1. Chcete-li přidat komponentu s názvem **OpenFileDialog1** do formuláře, dvakrát klikněte na položku **OpenFileDialog**. Chcete-li do formuláře přidat komponentu s názvem **colorDialog1** , dvakrát klikněte na položku **ColorDialog** v sadě **nástrojů**. (Použijete ho v dalším kroku kurzu.) Měla by se zobrazit oblast v dolní části **Návrhář formulářů** (pod formulářem **prohlížeče obrázků** ), která má ikonu pro každou ze dvou součástí dialogových oken, které jste přidali, jak je znázorněno na následujícím obrázku.

     ![Komponenty dialogového okna](../ide/media/express_dialogsadded.png)<br>**_Dialog_* _ _components *

1. V oblasti v dolní části **Návrhář formulářů** vyberte ikonu **OpenFileDialog1** . Nastavte dvě vlastnosti:

    - Nastavte vlastnost **Filter** na následující (můžete ji zkopírovat a vložit):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Vlastnost **title** nastavte na následující: **Vyberte soubor s obrázkem** .

         Nastavení vlastnosti **filtru** určují typy souborů, které se zobrazí v dialogovém okně vyberte soubor **obrázku** .

    > [!TIP]
    > Pokud chcete zobrazit příklad dialogového okna **otevřít soubor** v jiné aplikaci, otevřete **Poznámkový blok** nebo **Malování** a na panelu nabídek vyberte **soubor**  >  **otevřít**. Všimněte si, jak je rozevírací seznam vedle názvu souboru, který umožňuje zvolit typ souboru. <br/><br/>Právě jste v komponentě **OpenFileDialog** použili vlastnost **Filter** a nastavili jste ji v aplikaci. Všimněte si také, jak jsou vlastnosti **nadpisu** a **filtru** tučné v okně **vlastnosti** . Integrované vývojové prostředí (IDE) umožňuje zobrazit všechny vlastnosti, které byly změněny z jejich výchozích hodnot.

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si **[Krok 8: napište kód pro zobrazení obslužné rutiny události tlačítka Zobrazit obrázek](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**.

* Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
