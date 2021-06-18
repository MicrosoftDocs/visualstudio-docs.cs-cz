---
title: 'Krok 1: Vytvoření projektu aplikace modelu Windows Forms'
description: Zjistěte, jak vytvořit projekt model Windows Forms App pro váš prohlížeč obrázků.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fccce125b66101b05544cba22b3724a8a40dc0f3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307736"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Krok 1: Vytvoření projektu aplikace modelu Windows Forms

Při vytváření prohlížeče obrázků je prvním krokem vytvoření projektu model Windows Forms App.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Na řádku nabídek zvolte File New Project **(Soubor**  >  **nový**  >  **projekt).** Dialogové okno by mělo vypadat podobně jako na následujícím snímku obrazovky.

     ![Dialogové okno Nový projekt](../ide/media/newprojectdialogcallouts.png)<br/>***Nový projekt** _ _dialog box*

2. Na levé straně dialogového **okna Nový** projekt zvolte Buď **Visual C#** nebo **Visual Basic** a pak zvolte **Windows Desktop**.

3. V seznamu šablon projektů zvolte **model Windows Forms App (.NET Framework).** Pojmete nový formulář *PictureViewer* a pak zvolte **tlačítko OK.**

    >[!NOTE]
    >Pokud šablonu model Windows Forms **App (.NET Framework)** nevidíte, použijte Instalační program pro Visual Studio k instalaci úlohy vývoje desktopových aplikací **.NET.**<br/><br/>![Úloha vývoj desktopových aplikací .NET v Instalační program pro Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [Instalace Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-visual-studio"></a>Otevřete sadu Visual Studio.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

   ![Zobrazení okna Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V **okně Vytvořit nový** projekt zadejte nebo zadejte *model Windows Forms* do vyhledávacího pole. Potom v **seznamu Typ** projektu zvolte **Desktop.**

   Po použití filtru **Typ projektu** zvolte šablonu model Windows Forms **App (.NET Framework)** pro jazyk C# nebo Visual Basic a pak zvolte **Další.**

   ![Zvolte šablonu C# nebo Visual Basic pro aplikaci model Windows Forms (.NET Framework).](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud šablonu aplikace **model Windows Forms (.NET Framework),** můžete ji nainstalovat z okna Vytvořit **nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce.
   >
   > ![Odkaz Install more tools and features (Nainstalovat další nástroje a funkce) ze zprávy Not finding what you're looking for (Najít, co hledáte) v okně Create new project (Vytvořit nový projekt)](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V dalším kroku Instalační program pro Visual Studio zvolte úlohu Zvolte vývoj desktopových aplikací **pro .NET.**
   >
   > ![Úloha .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom zvolte tlačítko **Upravit** v Instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce. Pokud ano, proveďte to. Potom zvolte **Pokračovat a** nainstalujte úlohu.

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole **Project name (Název projektu) zadejte nebo zadejte** *PictureViewer.* Pak zvolte **Vytvořit.**

::: moniker-end

Visual Studio vytvoří řešení pro vaši aplikaci. Řešení funguje jako kontejner pro všechny projekty a soubory, které vaše aplikace potřebuje. Tyto termíny budou podrobněji vysvětleny dále v tomto kurzu.

## <a name="about-the-windows-forms-app-project"></a>O projektu model Windows Forms App

1. Vývojové prostředí obsahuje tři okna: hlavní okno, **Průzkumník řešení** a **okno** Vlastnosti.

     Pokud některé z těchto oken chybí, můžete výchozí rozložení okna obnovit. V řádku nabídek zvolte Window  >  **Reset Window Layout (Rozložení okna pro resetování okna).**

     Okna můžete zobrazit také pomocí příkazů nabídky. V řádku nabídek zvolte **Zobrazit okno**  >  **Vlastnosti nebo** **Průzkumník řešení**.

     Pokud jsou otevřená nějaká další okna, zavřete je výběrem tlačítka **Zavřít** (x) v pravém horním rohu.

    ::: moniker range="vs-2017"

    * **Hlavní okno** V tomto okně budete většinu práce dělat, třeba pracovat s formuláři a upravovat kód. V okně se zobrazí formulář v **Editoru formulářů.** V horní části okna se zobrazí **karty Úvodní stránka** a **Form1.cs [Návrh].** (V Visual Basic název karty končí *na .vb* místo *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Hlavní okno** V tomto okně budete většinu práce dělat, třeba pracovat s formuláři a upravovat kód. V okně se zobrazí formulář v **Editoru formulářů.**

    ::: moniker-end

    * **Průzkumník řešení okno** V tomto okně můžete zobrazit a přejít ke všem položkám v řešení.

    Pokud zvolíte soubor, obsah okna **Vlastnosti** se změní. Pokud otevřete soubor kódu (končí na *.cs* v jazyce C# a *.vb* v souboru Visual Basic), zobrazí se soubor kódu nebo návrhář souboru kódu. Návrhář je vizuální plocha, na kterou můžete přidat ovládací prvky, jako jsou tlačítka a seznamy. U Visual Studio formulářů se návrhář nazývá **Návrhář formulářů**.

    * **okno Vlastnosti** V tomto okně můžete změnit vlastnosti položek, které zvolíte v ostatních oknech. Pokud například zvolíte Form1, můžete změnit jeho název nastavením vlastnosti **Text** a nastavením vlastnosti **Backcolor** můžete změnit barvu pozadí.

      > [!NOTE]
      > Horní řádek v **Průzkumník řešení** řešení **PictureViewer (1 projekt),** což znamená, Visual Studio pro vás vytvořil řešení. Řešení může obsahovat více než jeden projekt, ale teď budete pracovat s řešeními, která obsahují pouze jeden projekt.

1. Na řádku nabídek zvolte Soubor  >  **Uložit vše.**

     Alternativně můžete zvolit tlačítko **Uložit vše** na panelu nástrojů, které je znázorněno na následujícím obrázku.

     ![Tlačítko Uložit vše na panelu nástrojů](../ide/media/express_iconsaveall.png)<br/>
     ***Uložit vše** _ _toolbar tlačítko*

     Visual Studio automaticky vyplní název složky a projektu a pak projekt uloží do složky projects.

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít k dalšímu kroku kurzu, přejděte **[na krok 2: Spuštění aplikace.](../ide/step-2-run-your-program.md)**

* Pokud se chcete vrátit k tématu přehledu, podívejte se [na Kurz 1: Vytvoření prohlížeče obrázků.](../ide/tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření matematického kvízu s časovým limitem](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: Vytvoření hry s shodou](tutorial-3-create-a-matching-game.md)
