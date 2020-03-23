---
title: 'Krok 1: Vytvoření projektu aplikace pro Windows Forms'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579910"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Krok 1: Vytvoření projektu aplikace pro Windows Forms

Při vytváření prohlížeče obrázků je prvním krokem vytvoření projektu aplikace Pro Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Otevřít Visual Studio 2017

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**. Dialogové okno by mělo vypadat podobně jako na následujícím snímku obrazovky.

     ![Dialogové okno Nový projekt](../ide/media/newprojectdialogcallouts.png)<br/>***New project*** *Dialogové okno* Nový projekt

2. Na levé straně dialogového okna **Nový projekt** zvolte **visual c#** nebo **visual basic**a pak zvolte **Windows Desktop**.

3. V seznamu šablon projektu zvolte **Windows Forms App (.NET Framework)**. Pojmenujte nový formulář *PictureViewer*a pak zvolte tlačítko **OK.**

    >[!NOTE]
    >Pokud šablonu aplikace **Windows Forms App (.NET Framework)** nevidíte, nainstalujte pracovní vytížení **pro vývoj plochy .NET** pomocí Instalační služby visual studia.<br/><br/>![Úloha vývoje plochy rozhraní .NET v Instalační službě sady Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [Instalace sady Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Otevřít Visual Studio 2019

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte windows *forms* do vyhledávacího pole. Dále zvolte **Plocha** ze seznamu **typ projektu.**

   Po použití filtru **typu projektu** zvolte šablonu aplikace Windows Forms **App (.NET Framework)** pro c# nebo visual basic a pak zvolte **Další**.

   ![Zvolte šablonu jazyka C# nebo Visual Basic pro aplikaci Windows Forms App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud šablonu Aplikace **Windows Forms (.NET Framework)** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Dále v Instalační službě sady Visual Studio zvolte zvolte **úlohu vývoje plochy .NET.**
   >
   > ![Úloha jádra .NET v Instalační službě sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy.

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *PictureViewer* do pole **Název projektu.** Potom zvolte **Vytvořit**.

::: moniker-end

Visual Studio vytvoří řešení pro vaši aplikaci. Řešení funguje jako kontejner pro všechny projekty a soubory potřebné pro vaši aplikaci. Tyto termíny budou vysvětleny podrobněji dále v tomto kurzu.

## <a name="about-the-windows-forms-app-project"></a>Projekt aplikace Windows Forms App

1. Vývojové prostředí obsahuje tři okna: hlavní okno, **Průzkumník řešení**a okno **Vlastnosti.**

     Pokud některá z těchto oken chybí, můžete obnovit výchozí rozložení okna. Na řádku nabídek zvolte **Window** > **Reset Window Layout**.

     Okna můžete zobrazit také pomocí příkazů nabídky. Na řádku nabídek zvolte **Zobrazit** > **okno vlastností** nebo **Průzkumník řešení**.

     Pokud jsou otevřena některá další okna, zavřete je tak, že v pravém horním rohu zvolíte tlačítko **Zavřít** (x).

    ::: moniker range="vs-2017"

    * **Hlavní okno** V tomto okně budete dělat většinu práce, například práci s formuláři a úpravy kódu. V okně se zobrazí formulář v **Editoru formulářů**. V horní části okna se zobrazí karta **Úvodní stránka** a karta **Form1.cs [Design].** (V jazyce Visual Basic končí název karty *.vb* místo *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Hlavní okno** V tomto okně budete dělat většinu práce, například práci s formuláři a úpravy kódu. V okně se zobrazí formulář v **Editoru formulářů**.

    ::: moniker-end

    * **Okno Průzkumník řešení** V tomto okně můžete zobrazit a přejít na všechny položky v řešení.

    Pokud zvolíte soubor, změní se obsah okna **Vlastnosti.** Pokud otevřete soubor kódu (který končí *v .cs* v Jazyce C# a *.vb* v jazyce Visual Basic), zobrazí se soubor kódu nebo návrhář souboru kódu. Návrhář je vizuální povrch, do kterého můžete přidat ovládací prvky, jako jsou tlačítka a seznamy. Pro formuláře sady Visual Studio se návrhář nazývá **Návrhář formulářů systému Windows**.

    * **Okno Vlastnosti** V tomto okně můžete změnit vlastnosti položek, které zvolíte v jiných oknech. Pokud například zvolíte Form1, můžete změnit jeho název nastavením **vlastnosti Text** a můžete změnit barvu pozadí nastavením vlastnosti **Backcolor.**

      > [!NOTE]
      > Horní řádek v **Průzkumníku řešení** zobrazuje **řešení PictureViewer (1 projekt)**, což znamená, že Visual Studio vytvořilo řešení pro vás. Řešení může obsahovat více než jeden projekt, ale prozatím budete pracovat s řešeními, která obsahují pouze jeden projekt.

1. Na řádku nabídek zvolte **Soubor** > **Uložit vše**.

     Jako alternativu zvolte tlačítko **Uložit vše** na panelu nástrojů, které ukazuje následující obrázek.

     ![Tlačítko Uložit vše](../ide/media/express_iconsaveall.png)<br/>
     ***Tlačítko Uložit vše*** *toolbar button*

     Visual Studio automaticky vyplní název složky a název projektu a potom uloží projekt do složky projekty.

## <a name="next-steps"></a>Další kroky

* Další krok kurzu najdete v **[tématu Krok 2: Spuštění aplikace](../ide/step-2-run-your-program.md)**.

* Chcete-li se vrátit k tématu přehledu, [přečtěte si téma 1: Vytvoření prohlížeče obrázků](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
