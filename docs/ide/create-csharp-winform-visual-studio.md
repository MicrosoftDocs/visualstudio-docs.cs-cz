---
title: 'Vytvoření aplikace pro Windows Forms s C #'
description: Přečtěte si, jak vytvořit aplikaci pro Windows Forms ve Visual Studiu s C#, krok za krokem.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4017ee2da040ccef36c58b17d896abab199c3517
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71682142"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Vytvoření aplikace pro Windows Forms ve Visual Studiu s C #

V tomto krátkém úvodu k integrované vývojové prostředí sady Visual Studio (IDE) vytvoříte jednoduchou aplikaci jazyka C#, která má uživatelské rozhraní (UI) založené na systému Windows.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

> [!NOTE]
> Některé screenshoty v tomto tutoriálu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, podívejte se na [stránku Přizpůsobit ide a editor u visual ateliéru,](../ide/quickstart-personalize-the-ide.md) kde se dozvíte, jak na to.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace C#. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat, ještě předtím, než něco přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Visual C#** a pak zvolte **Plochu systému Windows**. V prostředním podokně zvolte **Windows Forms App (.NET Framework)**. Poté soubor `HelloWorld`pojmenujte .

     Pokud šablonu projektu **aplikace Windows Forms App (.NET Framework)** nevidíte, zrušte ji z dialogového okna **Nový projekt** a v horním řádku nabídek zvolte **Nástroje** > **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje plochy .NET** a pak zvolte **Změnit**.

     ![Úloha jádra .NET v Instalační službě sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zvolte šablonu aplikace Windows Forms App **(.NET Framework)** pro C#.

   (Pokud chcete, můžete upřesnit hledání, abyste se rychle dostali k požadované šabloně. Do vyhledávacího pole například zadejte nebo zadejte *aplikaci Windows Forms App.* Dále zvolte **C#** ze seznamu Jazyk a pak zvolte **Windows** ze seznamu platformy.)  

   ![Zvolte šablonu Jazyka C# pro aplikaci Windows Forms App (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Pokud šablonu **Aplikace Windows Forms (.NET Framework)** nevidíte, můžete ji nainstalovat z okna Vytvořit nový **projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Dále v Instalační službě sady Visual Studio zvolte zvolte **úlohu vývoje plochy .NET.**
   >
   > ![Úloha jádra .NET v Instalační službě sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt HelloWorld](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu C# a pojmenování souboru visual studio otevře formulář pro vás. Formulář je uživatelské rozhraní systému Windows. Vytvoříme aplikaci "Hello World" přidáním ovládacích prvků do formuláře a pak spustíme aplikaci.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Zvolte **Panel nástrojů,** chcete-li otevřít okno pro rozluštití panelu nástrojů.

     ![Výběr panelu nástrojů pro otevření okna Panelu nástrojů](../ide/media/csharp-toolbox-toolwindow.png)

     (Pokud možnost rámeček **nástrojů** nevidíte, můžete ji otevřít z panelu nabídek. Chcete-li tak učinit, **zobrazit** > **panel nástrojů**. Nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**X**.)

1. Zvolte ikonu **Pin,** chcete-li ukotvit okno **Panelu nástrojů.**

     ![Výběrem ikony Pin připnete okno panelu nástrojů na ide.](../ide/media/vb-pin-the-toolbox-window.png)

1. Zvolte ovládací prvek **Tlačítko** a přetáhněte jej do formuláře.

     ![Přidání tlačítka do formuláře](../ide/media/csharp-add-button-form1.png)

1. V okně **Vlastnosti** vyhledejte **text**, změňte název z **Button1** na `Click this`a stiskněte **Enter**.

     ![Přidání textu k tlačítku ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud okno **Vlastnosti** nevidíte, můžete ho otevřít z panelu nabídek. Chcete-li tak učinit, zvolte **Zobrazit** > **okno vlastností**. Nebo stiskněte **klávesu F4**.)

1. V části **Návrh** v okně **Vlastnosti** změňte `btnClickThis`název z **Button1** na a stiskněte **Enter**.

     ![Přidání funkce k tlačítku ve formuláři](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Pokud jste seznam seřazeni podle abecedy v okně **Vlastnosti,** zobrazí se místo toho **button1** v části **(DataBindings).**

### <a name="add-a-label-to-the-form"></a>Přidání popisku do formuláře

Teď, když jsme přidali ovládací prvek tlačítka pro vytvoření akce, přidáme ovládací prvek popisku pro odeslání textu.

1. Vyberte ovládací **prvek Popisek** z okna **Panelu nástrojů** a přetáhněte ho do formuláře a přetáhněte ho pod **tlačítko Klepnout na toto** tlačítko.

1. V části **Návrh** nebo v části **(DataBindings)** v okně **Vlastnosti** `lblHelloWorld`změňte název **labelu1** na a stiskněte **klávesu Enter**.

### <a name="add-code-to-the-form"></a>Přidání kódu do formuláře

1. V okně **&#93;Form1.cs &#91;návrh** poklepáním na **toto** tlačítko otevřete **okno Form1.cs.**

      (Případně můžete rozbalit **Form1.cs** v **Průzkumníku řešení**a pak zvolit **Form1**.)

1. V **Form1.cs** okně za **řádek soukromé holčice** zadejte nebo zadejte, `lblHelloWorld.Text = "Hello World!";` jak je znázorněno na následujícím snímku obrazovky:

     ![Přidání kódu do formuláře](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Chcete-li aplikaci spustit, zvolte tlačítko **Start.**

     ![Zvolte Začít, chcete-li ladit a spouštět aplikaci.](../ide/media/vb-click-start-hello-world.png)

   Stane se několik věcí. V ide sady Visual Studio se otevře okno **Nástroje diagnostiky** a otevře se také okno **Výstup.** Ale mimo ide, **form1** dialogové okno se zobrazí. Bude obsahovat vaše **Klikněte na toto** tlačítko a text, který říká **Label1**.

1. Zvolte **Klepněte na toto** tlačítko v dialogovém okně **Formulář1.** Všimněte si, že **text Label1** se změní na **Hello World!**.

    ![Dialogové okno Formulář1 obsahující text Popisek1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zavřete dialogové okno **Formulář1,** chcete-li aplikaci zastavit.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz: Vytvoření prohlížeče obrázků](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také

* [Další výukové programy pro C#](/visualstudio/get-started/csharp/)
* [Výukové programy jazyka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Výukové programy pro C++](/cpp/get-started/tutorial-console-cpp)
