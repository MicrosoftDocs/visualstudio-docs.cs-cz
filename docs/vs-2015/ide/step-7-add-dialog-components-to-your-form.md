---
title: 'Krok 7: přidejte do svého formuláře komponenty dialogových oken | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b58f76dc5137ac0e281f109ee78f3ed43f907400
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646964"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7: Přidejte do svého formuláře komponenty dialogových oken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li programu povolit otevírání souborů obrázků a výběr barvy pozadí, v tomto kroku přidáte komponentu **OpenFileDialog** a komponentu **ColorDialog** do formuláře.

 Komponenta je jako ovládací prvek v některých způsobech. Pomocí panelu nástrojů přidáte komponentu do formuláře a nastavíte její vlastnosti pomocí okna **vlastnosti** . Ale na rozdíl od ovládacího prvku, přidání komponenty do formuláře nepřidá viditelnou položku, kterou může uživatel zobrazit ve formuláři. Místo toho poskytuje určité chování, které lze aktivovat pomocí kódu. Je to komponenta, která otevře dialogové okno **otevřít soubor** .

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu najdete v tématu [kurz 1: vytvoření prohlížeče obrázků v Visual Basic-Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) nebo v [kurzu 1: vytvoření prohlížeče obrázků ve C# formátu-Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio.

### <a name="to-add-dialog-components-to-your-form"></a>Přidání součástí dialogového okna do formuláře

1. Zvolte Návrhář formulářů (Form1.cs [Design] nebo Form1. vb [Design]) a pak otevřete skupinu **dialogy** v sadě nástrojů.

    > [!NOTE]
    > Skupina **dialogová okna** v sadě nástrojů obsahuje komponenty, které otevřou spoustu užitečných dialogových oken, které lze použít pro otevírání a ukládání souborů, procházení složek a výběr písma a barev. V tomto projektu použijete dvě komponenty dialogového okna: **OpenFileDialog** a **ColorDialog**.

2. Chcete-li přidat komponentu s názvem **OpenFileDialog1** do formuláře, dvakrát klikněte na položku **OpenFileDialog**. Chcete-li do formuláře přidat komponentu s názvem **colorDialog1** , dvakrát klikněte na položku **ColorDialog** v sadě nástrojů. (Použijete ho v dalším kroku kurzu.) Měla by se zobrazit oblast v dolní části Návrhář formulářů (pod formulářem prohlížeče obrázků), která má ikonu pro každou ze dvou součástí dialogových oken, které jste přidali, jak je znázorněno na následujícím obrázku.

     ![Komponenty dialogového okna](../ide/media/express-dialogsadded.png "Express_DialogsAdded") Komponenty dialogového okna

3. V oblasti v dolní části Návrhář formulářů vyberte ikonu **OpenFileDialog1** . Nastavte dvě vlastnosti:

    - Nastavte vlastnost **Filter** na následující (můžete ji zkopírovat a vložit):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Vlastnost **title** nastavte na následující: **Vyberte soubor s obrázkem** .

         Nastavení vlastnosti **filtru** určují typy souborů, které se zobrazí v dialogovém okně vyberte soubor **obrázku** .

    > [!NOTE]
    > Chcete-li zobrazit příklad dialogového okna **otevřít soubor** v jiné aplikaci, otevřete Poznámkový blok nebo malování a na panelu nabídek vyberte možnost **soubor**, **otevřít**. Všimněte si, jak jsou v dolní části **soubory typu** rozevírací seznam. Právě jste použili vlastnost **Filter** v komponentě **OpenFileDialog** k nastavení. Všimněte si také, jak jsou vlastnosti **nadpisu** a **filtru** tučné v okně **vlastnosti** . Integrované vývojové prostředí (IDE) umožňuje zobrazit všechny vlastnosti, které byly změněny z jejich výchozích hodnot.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 8: napište kód pro zobrazení obslužné rutiny události tlačítka Zobrazit obrázek](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md).
