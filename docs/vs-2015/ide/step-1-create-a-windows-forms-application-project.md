---
title: 'Krok 1: vytvoření projektu model Windows Forms aplikace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9651c04c1d94459052d92cdda0afa58e344b650
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295787"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Krok 1: Vytvořte projekt formulářové aplikace Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vytváření prohlížeče obrázků je prvním krokem vytvoření projektu aplikace model Windows Forms.

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu najdete v tématu [kurz 1: vytvoření prohlížeče obrázků v Visual Basic-video 1](https://go.microsoft.com/fwlink/?LinkId=205209) nebo [kurz 1: vytvoření prohlížeče obrázků ve C# videu 1](https://go.microsoft.com/fwlink/?LinkId=205199). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio.

### <a name="to-create-a-windows-forms-application-project"></a>Vytvoření projektu aplikace model Windows Forms

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**. Dialogové okno by mělo vypadat takto.

     ![Dialog Nový projekt](../ide/media/newprojectdialogcallouts.png "NewProjectDialogCallouts") Nový projekt – dialogové okno

2. V seznamu **Nainstalované šablony** vyberte buď možnost **vizuál C#**  , nebo **Visual Basic** .

3. V seznamu šablony vyberte ikonu **aplikace model Windows Forms** . Pojmenujte novou formu **PictureViewer**a pak klikněte na tlačítko **OK** .

     Visual Studio vytvoří řešení pro váš program. Řešení funguje jako kontejner pro všechny projekty a soubory, které váš program potřebuje. Tyto výrazy budou podrobněji vysvětleny dále v tomto kurzu.

4. Následující ilustrace ukazuje, co byste teď měli vidět v rozhraní sady Visual Studio.

    > [!NOTE]
    > Rozložení okna nemusí vypadat stejně jako na ilustraci. Přesné rozložení okna závisí na verzi aplikace Visual Studio, programovacím jazyku, který používáte, a na dalších faktorech. Měli byste ale ověřit, že se zobrazují všechna tři okna.

     ![Okno IDE](../ide/media/express-ideoverview-visio.png "Express_IDEOverview_Visio") Okno IDE

     Rozhraní obsahuje tři okna: hlavní okno, **Průzkumník řešení**a okno **vlastnosti** .

     Pokud některý z těchto oken chybí, obnovte výchozí rozložení okna podle, v řádku nabídek zvolte **okno**, **obnovit rozložení okna**. Okna můžete zobrazit také pomocí příkazů nabídky. Na panelu nabídek vyberte možnost **zobrazení**, **okno Vlastnosti** nebo **Průzkumník řešení**. Pokud jsou ostatní okna otevřená, zavřete je kliknutím na tlačítko **Zavřít** (x) v pravém horním rohu.

5. Ilustrace zobrazuje následující okna (ve směru hodinových ručiček od levého horního rohu):

    - **Hlavní okno** V tomto okně provedete většinu práce, například práci s formuláři a úpravou kódu. Na ilustraci okno zobrazuje formulář v editoru formulářů. V horní části okna se zobrazí karta **Úvodní stránka** a **Form1.cs [Design]** . (V Visual Basic název karty končí příponou. vb namísto. cs.)

    - **Průzkumník řešení okno** V tomto okně můžete zobrazit a přejít na všechny položky ve vašem řešení. Pokud zvolíte soubor, obsah okna **vlastnosti** se změní. Pokud otevřete soubor kódu (který končí příponou. cs v souboru Visual C# a. vb v Visual Basic), zobrazí se soubor kódu nebo Návrhář souboru s kódem. Návrhář je vizuální plocha, do které můžete přidat ovládací prvky, jako jsou tlačítka a seznamy. Pro formuláře sady Visual Studio se Návrhář nazývá Návrhář formulářů.

    - **Okno Vlastnosti** V tomto okně můžete změnit vlastnosti položek, které zvolíte v ostatních oknech. Například pokud zvolíte Form1, můžete změnit jeho nadpis nastavením vlastnosti **text** a můžete změnit barvu pozadí nastavením vlastnosti **BackColor** .

    > [!NOTE]
    > Horní řádek v **Průzkumník řešení** zobrazuje **řešení ' PictureViewer ' (1 projekt)** , což znamená, že Visual Studio vytvořilo řešení za vás. Řešení může obsahovat více než jeden projekt, ale v současnosti budete pracovat s řešeními, která obsahují pouze jeden projekt.

6. Na panelu nabídek vyberte položku **soubor**, **Uložit vše**.

     Jako alternativu klikněte na tlačítko **Uložit vše** na panelu nástrojů, které ukazuje následující obrázek.

     ![Tlačítko Uložit vše na panelu nástrojů](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Tlačítko Uložit vše na panelu nástrojů

     Visual Studio automaticky vyplní název složky a název projektu a pak projekt uloží ve složce Projects.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 2: spuštění programu](../ide/step-2-run-your-program.md).

- Pokud se chcete vrátit k tématu Přehled, přečtěte si téma [kurz 1: vytvoření prohlížeče obrázků](../ide/tutorial-1-create-a-picture-viewer.md).
