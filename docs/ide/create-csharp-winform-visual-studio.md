---
title: 'Vytvoření model Windows Forms pomocí jazyka C #'
description: Podrobné informace o vytvoření model Windows Forms v Visual Studio pomocí jazyka C#.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0efdb7d35549a32e1151a134ce3a665337bb27ce
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308308"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Vytvoření model Windows Forms aplikace v Visual Studio pomocí jazyka C\#

V tomto krátkém úvodu Visual Studio integrované vývojové prostředí (IDE) vytvoříte jednoduchou aplikaci v jazyce C#, která má uživatelské rozhraní založené na Windows.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud tmavý motiv používáte, ale chcete, podívejte se na stránku Přizpůsobení integrovaného vývojového Visual Studio a [editoru,](../ide/quickstart-personalize-the-ide.md) kde se dozvíte, jak.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio, nainstalujte si ho zdarma na [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) downloads.

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud tmavý motiv používáte, ale chcete, podívejte se na stránku Přizpůsobení integrovaného vývojového Visual Studio a [editoru,](../ide/quickstart-personalize-the-ide.md) kde se dozvíte, jak.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace v jazyce C#. Typ projektu se dodává se všemi soubory šablony, které budete potřebovat, ještě než cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

1. V dialogovém **okně Nový** projekt v levém podokně rozbalte **Visual C#** a pak zvolte **Windows Desktop.** V prostředním podokně zvolte **model Windows Forms App (.NET Framework).** Pak soubor pojmechte `HelloWorld` .

     Pokud nevidíte šablonu projektu **model Windows Forms App (.NET Framework),** zrušte v dialogovém okně  Nový projekt a v horním řádku nabídek zvolte Nástroje Získat nástroje a  >  **funkce.** Spustí se instalační program pro Visual Studio. Zvolte **úlohu Vývoj desktopových aplikací .NET** a pak zvolte **Upravit.**

     ![Úloha .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

   ![Zobrazení okna Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V **okně Vytvořit nový** projekt zvolte šablonu **model Windows Forms App (.NET Framework)** pro jazyk C#.

   (Pokud chcete, můžete upřesnit hledání a rychle se dostat k šabloně, kterou chcete. Do vyhledávacího pole zadejte *například model Windows Forms App.* Potom v seznamu Jazyk zvolte **C#** a pak **v** seznamu Platforma zvolte Windows.)  

   ![Zvolte šablonu C# pro aplikaci model Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Pokud se šablona **model Windows Forms App (.NET Framework),** můžete ji nainstalovat z okna Vytvořit **nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce.
   >
   > ![Odkaz Install more tools and features (Nainstalovat další nástroje a funkce) ze zprávy Not finding what you're looking for (Najít, co hledáte) v okně Create new project (Vytvořit nový projekt)](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V dalším kroku Instalační program pro Visual Studio zvolte úlohu Zvolte vývoj desktopových aplikací **pro .NET.**
   >
   > ![Úloha .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom zvolte tlačítko **Upravit** v Instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce. Pokud ano, proveďte to. Potom zvolte **Pokračovat a** nainstalujte úlohu. Pak se vraťte ke kroku 2 v[této proceduře "Vytvoření](#create-a-project)projektu".

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole Project name **(Název projektu) zadejte nebo zadejte** *HelloWorld.* Pak zvolte **Vytvořit.**

   ![V okně Configure your new project (Konfigurace nového projektu) zadejte název projektu HelloWorld.](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio nový projekt otevřete.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu C# a názvu souboru Visual Studio otevře formulář. Formulář je uživatelské rozhraní Systému Windows. Aplikaci "Hello World" vytvoříme přidáním ovládacích prvků do formuláře a pak aplikaci spustíme.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Zvolte **Panel** nástrojů a otevřete tak okno panelu nástrojů.

     ![Výběrem panelu nástrojů otevřete okno Panelu nástrojů.](../ide/media/csharp-toolbox-toolwindow.png)

     (Pokud nevidíte možnost  panelu nástrojů, můžete ji otevřít z řádku nabídek. Chcete-li to provést, **zobrazte panel**  >  **nástrojů**. Nebo stiskněte **Ctrl** + **Alt** + **X**.)

1. Zvolte **ikonu Připnout** a ukotvit **okno Panelu** nástrojů.

     ![Zvolte ikonu Připnout a připněte okno panelu nástrojů do integrovaného vývojového prostředí(IDE).](../ide/media/vb-pin-the-toolbox-window.png)

1. Zvolte ovládací **prvek** Tlačítko a přetáhněte ho na formulář.

     ![Přidání tlačítka do formuláře](../ide/media/csharp-add-button-form1.png)

1. V okně **Vlastnosti** vyhledejte **Text,** změňte název z **Button1** na a `Click this` pak stiskněte **Enter.**

     ![Přidání textu na tlačítko ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud okno Vlastnosti nevidíte, můžete ho otevřít z řádku nabídek.  Pokud to chcete udělat, zvolte **Zobrazit**  >  **okno Vlastnosti.** Nebo stiskněte **klávesu F4**.)

1. V části **Návrh** v okně **Vlastnosti** změňte název z **Button1** na a `btnClickThis` pak stiskněte **Enter.**

     ![Přidání funkce na tlačítko ve formuláři](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Pokud jste v okně Vlastnosti  seřadí seznam podle abecedy, zobrazí se v **části (Datové vazby)** tlačítko **Button1.**

### <a name="add-a-label-to-the-form"></a>Přidání popisku do formuláře

Teď, když jsme přidali ovládací prvek tlačítko pro vytvoření akce, přidáme ovládací prvek popisek pro odeslání textu.

1. V okně **Panelu** nástrojů vyberte ovládací prvek **Popisek,** přetáhněte ho na formulář a táhněte ho pod tlačítko Klikněte na **toto** tlačítko.

1. V části **Návrh** nebo **(Datové vazby)** okna  Vlastnosti změňte název **prvku Label1** na a `lblHelloWorld` stiskněte **Enter.**

### <a name="add-code-to-the-form"></a>Přidání kódu do formuláře

1. V okně **formuláře Form1.cs &#91;Design&#93;** poklikejte na tlačítko Click **this** (Kliknutím na toto tlačítko) otevřete **okno Form1.cs.**

      (Případně můžete rozbalit **form1.cs** **v Průzkumník řešení** a pak zvolit **Form1**.)

1. V okně **Form1.cs** za řádek **private void** zadejte nebo zadejte , `lblHelloWorld.Text = "Hello World!";` jak je znázorněno na následujícím snímku obrazovky:

     ![Přidání kódu do formuláře](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Zvolte **tlačítko Spustit** a spusťte aplikaci.

     ![Pokud chcete aplikaci ladit a spustit, zvolte Spustit.](../ide/media/vb-click-start-hello-world.png)

   Stane se několik věcí. V Visual Studio IDE se otevře  okno Diagnostické nástroje **a** otevře se také okno Výstup. Ale mimo integrované vývojové prostředí (IDE) se zobrazí dialogové okno **Form1.** Bude obsahovat vaše kliknutí **na toto tlačítko** a text s textem **Popisek1.**

1. Zvolte **tlačítko Click this** (Kliknout na toto) v **dialogovém okně Form1.** Všimněte **si, že** text Label1 se **změní na Hello World!**.

    ![Dialogové okno Form1 obsahující text Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zavřete **dialogové okno Form1,** aby se aplikace zastavila.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz: Vytvoření prohlížeče obrázků](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také

* [Další kurzy k C#](../get-started/csharp/index.yml)
* [Visual Basic kurzy](../get-started/visual-basic/index.yml)
* [Kurzy k C++](/cpp/get-started/tutorial-console-cpp)