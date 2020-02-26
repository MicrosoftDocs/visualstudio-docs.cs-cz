---
title: 'Krok 1: vytvoření projektu aplikace model Windows Forms'
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579910"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Krok 1: vytvoření projektu aplikace model Windows Forms

Při vytváření prohlížeče obrázků je prvním krokem vytvoření projektu aplikace model Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**. Dialogové okno by mělo vypadat podobně jako na následujícím snímku obrazovky.

     dialog ![nový projekt](../ide/media/newprojectdialogcallouts.png)<br/>***Nový projekt*** – *dialogové okno*

2. Na levé straně dialogového okna **Nový projekt** vyberte možnost **vizuál C#**  nebo **Visual Basic**a pak zvolte možnost **plocha systému Windows**.

3. V seznamu šablony projektu vyberte možnost **model Windows Forms aplikace (.NET Framework)** . Pojmenujte novou formu *PictureViewer*a pak klikněte na tlačítko **OK** .

    >[!NOTE]
    >Pokud nevidíte šablonu **aplikace model Windows Forms App (.NET Framework)** , nainstalujte úlohu **vývoj desktopových aplikací .NET** pomocí instalační program pro Visual Studio.<br/><br/>![úlohy vývoj desktopových aplikací .NET v Instalační program pro Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [instalace sady Visual Studio](../install/install-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Open Visual Studio 2019

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** zadejte nebo zadejte *model Windows Forms* do vyhledávacího pole. V dalším kroku vyberte možnost **plocha** ze seznamu **typ projektu** .

   Po použití filtru **typu projektu** zvolte šablonu **aplikace model Windows Forms (.NET Framework)** pro buď C# nebo Visual Basic, a pak zvolte možnost **Další**.

   ![Vyberte šablonu C# nebo Visual Basic pro aplikaci model Windows Forms (.NET Framework).](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **aplikace model Windows Forms App (.NET Framework)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V části Instalační program pro Visual Studio klikněte na možnost zvolit úlohu **vývoj desktopových aplikací .NET** .
   >
   > ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu.

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *PictureViewer* do pole **název projektu** . Pak zvolte **vytvořit**.

::: moniker-end

Visual Studio vytvoří řešení pro vaši aplikaci. Řešení funguje jako kontejner pro všechny projekty a soubory, které vaše aplikace potřebuje. Tyto výrazy budou podrobněji vysvětleny dále v tomto kurzu.

## <a name="about-the-windows-forms-app-project"></a>O projektu aplikace model Windows Forms

1. Vývojové prostředí obsahuje tři okna: hlavní okno, **Průzkumník řešení**a okno **vlastnosti** .

     Pokud chybí některá z těchto oken, můžete obnovit výchozí rozložení okna. Na panelu nabídek vyberte možnost **okno** > **obnovit rozložení okna**.

     Okna můžete zobrazit také pomocí příkazů nabídky. Na panelu nabídek vyberte možnost **zobrazit** > **vlastnosti okno** nebo **Průzkumník řešení**.

     Pokud jsou ostatní okna otevřená, zavřete je kliknutím na tlačítko **Zavřít** (x) v pravém horním rohu.

    ::: moniker range="vs-2017"

    * **Hlavní okno** V tomto okně provedete většinu práce, například práci s formuláři a úpravou kódu. Okno zobrazuje formulář v **editoru formulářů**. V horní části okna se zobrazí karta **Úvodní stránka** a **Form1.cs [Design]** . (V Visual Basic název karty končí příponou *. vb* namísto *. cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Hlavní okno** V tomto okně provedete většinu práce, například práci s formuláři a úpravou kódu. Okno zobrazuje formulář v **editoru formulářů**.

    ::: moniker-end

    * **Průzkumník řešení okno** V tomto okně můžete zobrazit a přejít na všechny položky ve vašem řešení.

    Pokud zvolíte soubor, obsah okna **vlastnosti** se změní. Pokud otevřete soubor kódu (který končí na *. cs* v C# a *. vb* v Visual Basic), zobrazí se soubor kódu nebo Návrhář souboru s kódem. Návrhář je vizuální plocha, do které můžete přidat ovládací prvky, jako jsou tlačítka a seznamy. Pro formuláře sady Visual Studio se Návrhář nazývá **Návrhář formulářů**.

    * **Okno Vlastnosti** V tomto okně můžete změnit vlastnosti položek, které zvolíte v ostatních oknech. Například pokud zvolíte Form1, můžete změnit jeho nadpis nastavením vlastnosti **text** a můžete změnit barvu pozadí nastavením vlastnosti **BackColor** .

      > [!NOTE]
      > Horní řádek v **Průzkumník řešení** zobrazuje **řešení ' PictureViewer ' (1 projekt)** , což znamená, že Visual Studio vytvořilo řešení za vás. Řešení může obsahovat více než jeden projekt, ale v současnosti budete pracovat s řešeními, která obsahují pouze jeden projekt.

1. Na panelu nabídek vyberte možnost **soubor** > **Uložit vše**.

     Jako alternativu klikněte na tlačítko **Uložit vše** na panelu nástrojů, které ukazuje následující obrázek.

     ![uložit všechna tlačítka panelu nástrojů](../ide/media/express_iconsaveall.png)<br/>
     Tlačítko ***Uložit vše*** na *panelu nástrojů*

     Visual Studio automaticky vyplní název složky a název projektu a pak projekt uloží ve složce Projects.

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si **[článek krok 2: spuštění vaší aplikace](../ide/step-2-run-your-program.md)** .

* Pokud se chcete vrátit k tématu Přehled, přečtěte si téma [kurz 1: vytvoření prohlížeče obrázků](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
