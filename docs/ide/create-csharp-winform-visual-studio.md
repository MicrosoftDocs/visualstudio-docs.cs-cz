---
title: Vytvoření aplikace model Windows Forms sC#
description: Naučte se, jak vytvořit aplikaci model Windows Forms v aplikaci Visual C#Studio s nástrojem, krok za krokem.
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
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682142"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Vytvoření aplikace model Windows Forms v aplikaci Visual Studio sC#

V tomto krátkém úvodu do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou C# aplikaci, která má uživatelské rozhraní (UI) založené na systému Windows.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chtěli, najdete v článku [přizpůsobit IDE sady Visual Studio a Editor](../ide/quickstart-personalize-the-ide.md) stránku a zjistěte, jak.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt C# aplikace. Typ projektu obsahuje všechny soubory šablon, které potřebujete, než jste přidali ještě něco.

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017.

1. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **vizuál C#** a pak zvolte možnost **plocha systému Windows**. V prostředním podokně vyberte **aplikace Windows Forms (.NET Framework)** . Potom zadejte název souboru `HelloWorld`.

     Pokud se nezobrazí **aplikace Windows Forms (.NET Framework)** projektu šablony, zrušte z celkového počtu **nový projekt** dialogového okna a v horní nabídce vyberte **nástroje**  >  **Získejte nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** úloh, klikněte na tlačítko **změnit**.

     ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** vyberte šablonu **aplikace model Windows Forms (.NET Framework)** pro C#.

   (Pokud chcete, můžete hledání upřesnit tak, abyste se rychle dostali k požadované šabloně. Do vyhledávacího pole zadejte například nebo zadejte *model Windows Forms App* . Dále zvolte **C#** ze seznamu jazyk a v seznamu platforma zvolte možnost **Windows** .)  

   ![Zvolit C# šablonu pro aplikaci model Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **aplikace model Windows Forms App (.NET Framework)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V části Instalační program pro Visual Studio klikněte na možnost zvolit úlohu **vývoj desktopových aplikací .NET** .
   >
   > ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte svůj projekt HelloWorld.](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony C# projektu a pojmenování souboru aplikace Visual Studio otevře formulář za vás. Formulář je uživatelské rozhraní Windows. Vytvoříme aplikaci "Hello World" přidáním ovládacích prvků do formuláře a pak aplikaci spustíme.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Vyberte **panel nástrojů** a otevřete tak okno s časovým obdobím panelu nástrojů.

     ![Vyberte sadu nástrojů a otevřete tak okno panelu nástrojů.](../ide/media/csharp-toolbox-toolwindow.png)

     (Pokud se nezobrazí **nástrojů** nabídka možností, lze jej otevřít z řádku nabídek. Provedete to tak, že **zobrazíte** > **sadu nástrojů**. Také můžete stisknout klávesu **Ctrl**+**Alt**+**X**.)

1. Vyberte ikonu **připnutí** pro ukotvení okna **panelu nástrojů** .

     ![Vyberte ikonu připnutí pro připnutí okna nástrojů k prostředí IDE.](../ide/media/vb-pin-the-toolbox-window.png)

1. Vyberte ovládací prvek **tlačítko** a přetáhněte ho na formulář.

     ![Přidání tlačítka do formuláře](../ide/media/csharp-add-button-form1.png)

1. V okně **vlastnosti** vyhledejte **text**, změňte název z **Button1** na `Click this`a potom stiskněte klávesu **ENTER**.

     ![Přidejte text pro tlačítko ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud se nezobrazí **vlastnosti** okna, lze jej otevřít z řádku nabídek. Provedete to tak, že kliknete na **zobrazit** > **okno Vlastnosti**. Také můžete stisknout klávesu **F4**.)

1. V **návrhu** část **vlastnosti** okna, změňte název z **Button1** k `btnClickThis`a potom stiskněte klávesu **Enter**.

     ![Přidání funkce do tlačítko ve formuláři](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Pokud jste v okně **vlastnosti** v abecedním seznamu, zobrazí se v části **(DataBindings)** ikona **Button1** místo toho.

### <a name="add-a-label-to-the-form"></a>Přidejte popisek do formuláře

Teď, když jsme přidali ovládací prvek tlačítko Vytvořit akci, přidáme popisek ovládacího prvku k odeslání text, který se.

1. Vyberte **popisek** ovládacího prvku **nástrojů** okna a přetáhněte ji na formuláři a přetáhněte ho pod **kliknutím na tuto** tlačítko.

1. V části **Návrh** nebo **(datové vazby)** v okně **vlastnosti** změňte název **Label1** na `lblHelloWorld`a potom stiskněte klávesu **ENTER**.

### <a name="add-code-to-the-form"></a>Přidejte kód do formuláře

1. V okně **Návrh &#91;&#93; Form1.cs** dvakrát klikněte na **Toto** tlačítko a otevřete okno **Form1.cs** .

      (Případně můžete rozbalit **Form1.cs** v **Průzkumník řešení**a pak vybrat **Form1**.)

1. V okně **Form1.cs** po **privátní řádce void** zadejte nebo zadejte `lblHelloWorld.Text = "Hello World!";`, jak je znázorněno na následujícím snímku obrazovky:

     ![Přidejte kód do formuláře](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Spusťte aplikaci kliknutím na tlačítko **Spustit** .

     ![Zvolit spustit pro ladění a spuštění aplikace](../ide/media/vb-click-start-hello-world.png)

   Stane se několik věcí. V sadě Visual Studio IDE **diagnostické nástroje** otevře se okno a **výstup** otevře se okno, příliš. Ale mimo rozhraní IDE **Form1** zobrazí se dialogové okno. Bude obsahovat vaše **kliknutím na tuto** tlačítko a text, který říká **Label1**.

1. Vyberte **Toto** tlačítko v dialogovém okně **Form1** . Všimněte si, **Label1** text změní na **Hello World!** .

    ![Dialogové okno Form1, které obsahuje Label1 text ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zavřením dialogového okna **Form1** zastavíte běh aplikace.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz: vytvoření prohlížeče obrázků](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také:

* [Další C# kurzy](/visualstudio/get-started/csharp/)
* [Kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++výuka](/cpp/get-started/tutorial-console-cpp)
