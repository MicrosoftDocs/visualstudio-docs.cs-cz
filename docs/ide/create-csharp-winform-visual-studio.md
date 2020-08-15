---
title: 'Vytvoření aplikace model Windows Forms pomocí jazyka C #'
description: Naučte se, jak vytvořit aplikaci model Windows Forms v aplikaci Visual Studio pomocí jazyka C#, krok za krokem.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 79fb60f05d12b1105febc12a218b1f36ee498deb
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248731"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Vytvoření aplikace model Windows Forms v aplikaci Visual Studio pomocí jazyka C\#

V tomto krátkém úvodu do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou aplikaci v jazyce C#, která má uživatelské rozhraní (UI) založené na systému Windows.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, přečtěte si téma [přizpůsobení stránky IDE a editoru sady Visual Studio](../ide/quickstart-personalize-the-ide.md) , kde se dozvíte, jak.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace v jazyce C#. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual C#** a pak zvolte možnost **plocha systému Windows**. V prostředním podokně vyberte **model Windows Forms App (.NET Framework)**. Pak soubor pojmenujte `HelloWorld` .

     Pokud nevidíte šablonu projektu **model Windows Forms App (.NET Framework)** , zrušte z dialogového okna **Nový projekt** a v horním řádku nabídky vyberte **nástroje**  >  **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak zvolte **Upravit**.

     ![Zatížení .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** vyberte šablonu **aplikace model Windows Forms (.NET Framework)** pro C#.

   (Pokud chcete, můžete hledání upřesnit tak, abyste se rychle dostali k požadované šabloně. Do vyhledávacího pole zadejte například nebo zadejte *model Windows Forms App* . Potom v seznamu jazyk vyberte **C#** a pak v seznamu platforma zvolte **Windows** .)  

   ![Zvolit šablonu C# pro aplikaci model Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **aplikace model Windows Forms App (.NET Framework)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V části Instalační program pro Visual Studio klikněte na možnost zvolit úlohu **vývoj desktopových aplikací .NET** .
   >
   > ![Zatížení .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte svůj projekt HelloWorld.](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu v jazyce C# a pojmenování souboru aplikace Visual Studio otevře formulář za vás. Formulář je uživatelské rozhraní systému Windows. Vytvoříme aplikaci "Hello World" přidáním ovládacích prvků do formuláře a pak aplikaci spustíme.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Vyberte **panel nástrojů** a otevřete tak okno s časovým obdobím panelu nástrojů.

     ![Vyberte sadu nástrojů a otevřete tak okno panelu nástrojů.](../ide/media/csharp-toolbox-toolwindow.png)

     (Pokud nevidíte možnost rozevíracího seznamu **nástrojů** , můžete ji otevřít z řádku nabídek. Provedete to tak, že **zobrazíte**  >  **sadu nástrojů**. Nebo stiskněte klávesu **CTRL** + **ALT** + **X**.)

1. Vyberte ikonu **připnutí** pro ukotvení okna **panelu nástrojů** .

     ![Vyberte ikonu připnutí pro připnutí okna nástrojů k prostředí IDE.](../ide/media/vb-pin-the-toolbox-window.png)

1. Vyberte ovládací prvek **tlačítko** a přetáhněte ho na formulář.

     ![Přidání tlačítka do formuláře](../ide/media/csharp-add-button-form1.png)

1. V okně **vlastnosti** vyhledejte **text**, změňte název z **Button1** na a `Click this` potom stiskněte klávesu **ENTER**.

     ![Přidat text na tlačítko ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud se okno **vlastnosti** nezobrazí, můžete ho otevřít z řádku nabídek. Chcete-li to provést, klikněte na tlačítko **Zobrazit**  >  **okno vlastností**. Nebo stiskněte **F4**.)

1. V části **Návrh** okna Vlastnosti změňte název z **Možnosti** **Button1** na a `btnClickThis` potom stiskněte klávesu **ENTER**.

     ![Přidání funkce na tlačítko ve formuláři](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Pokud jste v okně **vlastnosti** v abecedním seznamu, zobrazí se v části **(DataBindings)** ikona **Button1** místo toho.

### <a name="add-a-label-to-the-form"></a>Přidání popisku do formuláře

Teď, když jsme přidali ovládací prvek tlačítko pro vytvoření akce, Pojďme přidat ovládací prvek popisek, do kterého se má text poslat.

1. V okně **panelu nástrojů** vyberte ovládací prvek **popisek** a přetáhněte ho do formuláře a přetáhněte ho pod **tlačítko toto** tlačítko.

1. V části **Návrh** nebo **(datové vazby)** v okně **vlastnosti** změňte název **Label1** na a `lblHelloWorld` potom stiskněte klávesu **ENTER**.

### <a name="add-code-to-the-form"></a>Přidat kód do formuláře

1. V okně **Form1.cs &#91;Design&#93;** dvakrát klikněte **na tlačítko,** čímž otevřete okno **Form1.cs** .

      (Případně můžete rozbalit **Form1.cs** v **Průzkumník řešení**a pak vybrat **Form1**.)

1. V okně **Form1.cs** po **privátní řádce void** zadejte nebo zadejte, `lblHelloWorld.Text = "Hello World!";` jak je znázorněno na následujícím snímku obrazovky:

     ![Přidat kód do formuláře](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Spusťte aplikaci kliknutím na tlačítko **Spustit** .

     ![Zvolit spustit pro ladění a spuštění aplikace](../ide/media/vb-click-start-hello-world.png)

   Proběhne několik věcí. V integrovaném vývojovém prostředí sady Visual Studio se otevře okno **diagnostické nástroje** a otevře se okno **výstup** . Ale mimo integrované vývojové prostředí (IDE), zobrazí se dialogové okno **Form1** . Bude obsahovat vaše **kliknutí na toto** tlačítko a text, který říká **Label1**.

1. Vyberte **Toto** tlačítko v dialogovém okně **Form1** . Všimněte si, že text **Label1** se změní na **Hello World!**.

    ![Dialogové okno Form1, které obsahuje text Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zavřením dialogového okna **Form1** zastavíte běh aplikace.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz: vytvoření prohlížeče obrázků](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také

* [Další kurzy C#](/visualstudio/get-started/csharp/)
* [Kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [Kurzy C++](/cpp/get-started/tutorial-console-cpp)
