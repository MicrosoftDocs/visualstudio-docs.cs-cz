---
title: 'Krok 7: Přidejte do svého formuláře komponenty dialogových oken'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed228c007d41d3c7a0815cb97ea9cd890b3a0c98
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748709"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7: Přidejte do svého formuláře komponenty dialogových oken
Chcete-li povolit program otevřít soubory obrázků a zvolit barvu pozadí v tomto kroku přidáte <xref:System.Windows.Forms.OpenFileDialog> součásti a <xref:System.Windows.Forms.ColorDialog> součásti do svého formuláře.

 Komponenta je jako ovládacího prvku určitým způsobem. Použijete **sada nástrojů** chcete přidejte součást do svého formuláře a nastavte její vlastnosti pomocí **vlastnosti** okno. Ale na rozdíl od řízení, přidání do svého formuláře komponenty nepřidá viditelnou položku, kterou uživatel uvidí na formuláři. Namísto toho poskytuje určitého chování, které můžete aktivovat pomocí kódu. Je součástí, které se otevře **otevření souboru** dialogové okno.

 ![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v části [kurzu 1: vytvoření prohlížeče obrázků v jazyce Visual Basic – Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) nebo [kurzu 1: vytvoření prohlížeče obrázků v jazyce C# - Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tyto videa pomocí starší verze sady Visual Studio, takže drobné rozdíly v některé příkazy a další prvky uživatelského rozhraní. Však koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.

## <a name="to-add-dialog-components-to-your-form"></a>Chcete-li přidat do svého formuláře komponenty dialogových oken

1.  Vyberte **Návrhář formulářů Windows** (**Form1.cs [Design]** nebo **Form1.vb [Design]**) a pak otevřete **v dialogových oknech** v  **Sada nástrojů**.

    > [!NOTE]
    >  **v dialogových oknech** v **sada nástrojů** má komponenty, které otevírají mnoho užitečných dialogových oken, které lze použít pro otevírání a ukládání souborů, procházení složek a výběr písma a barev. V tomto projektu používáte dvě komponenty dialogového okna: OpenFileDialog a ColorDialog.

2.  Chcete-li přidat komponenty s názvem **openFileDialog1** do svého formuláře, dvakrát klikněte na **OpenFileDialog**. Chcete-li přidat komponenty s názvem **colorDialog1** do svého formuláře, dvakrát klikněte na **ColorDialog** v **sada nástrojů**. (Můžete použít v dalším kroku kurzu.) Měli byste vidět oblast v dolní části **Návrhář formulářů Windows** (pod **Prohlížeč obrázků** formuláře), obsahuje ikonu pro jednotlivé součásti dvě dialogové okno, které jste přidali, jak je znázorněno na následujícím obrázku.

     ![Komponenty dialogového okna](../ide/media/express_dialogsadded.png)
**dialogové okno** součásti

3.  Vyberte **openFileDialog1** v oblasti v dolní části ikonu **Návrhář formulářů Windows**. Nastavte dvě vlastnosti:

    -   Nastavte **filtru** vlastnost následující (můžete zkopírovat a vložit ji):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    -   Nastavte **název** vlastnost, která má následující: **vyberte soubor s obrázkem**

         **Filtru** nastavení vlastností zadejte druhy typy souborů, které se zobrazí v **vyberte obrázek** dialogové okno souborů.

    > [!NOTE]
    >  Chcete-li zobrazit příklad **otevřít soubor** dialogové okno v jiné aplikaci, otevřete **Poznámkový blok** nebo **Malování**a na panelu nabídek vyberte **soubor**  >  **Otevřete**. Všimněte si, jak je **soubory typu** rozevíracího seznamu dole. Jste právě použili **filtru** vlastnost **OpenFileDialog** součásti k tomuto nastavení. Všimněte si také, jak **název** a **filtru** jsou vlastnosti tučné v **vlastnosti** okno. Prostředí IDE nemá, tak, aby zobrazovalo všechny vlastnosti, které se liší od výchozí hodnoty.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Přechod k dalšímu kroku kurzu naleznete v tématu [krok 8: zapište kód pro zobrazení obslužné rutiny události obrázek tlačítka](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 6: pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md).
