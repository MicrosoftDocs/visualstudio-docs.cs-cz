---
title: Vytvoření aplikace model Windows Forms s Visual Basic
description: Naučte se, jak vytvořit aplikaci model Windows Forms v aplikaci Visual Studio pomocí Visual Basic, krok za krokem.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 89effbfd31e0194a88067a340c9332d888ef23df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81224547"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Vytvoření aplikace model Windows Forms v aplikaci Visual Studio s Visual Basic

V tomto krátkém úvodu do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou Visual Basic aplikaci, která má uživatelské rozhraní (UI) založené na systému Windows.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, přečtěte si téma [přizpůsobení stránky IDE a editoru sady Visual Studio](../ide/quickstart-personalize-the-ide.md) , kde se dozvíte, jak.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace Visual Basic. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual Basic**a pak zvolte možnost **plocha systému Windows**. V prostředním podokně vyberte **model Windows Forms App (.NET Framework)**. Pak soubor pojmenujte `HelloWorld` .

     Pokud nevidíte šablonu projektu **model Windows Forms App (.NET Framework)** , zrušte z dialogového okna **Nový projekt** a v horním řádku nabídky vyberte **nástroje**  >  **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak zvolte **Upravit**.

     ![Zatížení .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** vyberte šablonu **aplikace model Windows Forms (.NET Framework)** pro Visual Basic.

   (Pokud chcete, můžete hledání upřesnit tak, abyste se rychle dostali k požadované šabloně. Do vyhledávacího pole zadejte například nebo zadejte *model Windows Forms App* . Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **Windows** .)  

   ![Vyberte šablonu Visual Basic pro aplikaci model Windows Forms (.NET Framework).](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

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

   ![v okně Konfigurovat nový projekt pojmenujte svůj projekt HelloWorld.](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu Visual Basic a pojmenování souboru aplikace Visual Studio otevře formulář za vás. Formulář je uživatelské rozhraní systému Windows. Vytvoříme aplikaci "Hello World" přidáním ovládacích prvků do formuláře a pak aplikaci spustíme.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Kliknutím na **panel nástrojů** otevřete okno s časovým intervalem panelu nástrojů.

     ![Kliknutím na panel nástrojů otevřete okno panelu nástrojů.](../ide/media/vb-toolbox-toolwindow.png)

     (Pokud nevidíte možnost rozevíracího seznamu **nástrojů** , můžete ji otevřít z řádku nabídek. Provedete to tak, že **zobrazíte**  >  **sadu nástrojů**. Nebo stiskněte klávesu **CTRL** + **ALT** + **X**.)

1. Kliknutím na ikonu **připnutí** můžete ukotvit okno **panelu nástrojů** .

     ![Kliknutím na ikonu připnutí připnete okno nástrojů do integrovaného vývojového prostředí (IDE).](../ide/media/vb-pin-the-toolbox-window.png)

1. Klikněte na ovládací prvek **tlačítko** a přetáhněte ho na formulář.

     ![Přidání tlačítka do formuláře](../ide/media/vb-add-a-button-to-form1.png)

1. V části **vzhled** (nebo oddílu **písma** ) v okně **vlastnosti** zadejte `Click this` a stiskněte klávesu **ENTER**.

     ![Přidat text na tlačítko ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud se okno **vlastnosti** nezobrazí, můžete ho otevřít z řádku nabídek. Uděláte to tak, že kliknete na **Zobrazit**  >  **okno Vlastnosti**. Nebo stiskněte **F4**.)

1. V části **Návrh** okna Vlastnosti změňte název z **Možnosti** **Button1** na a `btnClickThis` potom stiskněte klávesu **ENTER**.

     ![Přidání funkce na tlačítko ve formuláři](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Pokud jste v okně **vlastnosti** v abecedním seznamu, zobrazí se v části **(DataBindings)** ikona **Button1** místo toho.

### <a name="add-a-label-to-the-form"></a>Přidání popisku do formuláře

Teď, když jsme přidali ovládací prvek tlačítko pro vytvoření akce, Pojďme přidat ovládací prvek popisek, do kterého se má text poslat.

1. V okně **panelu nástrojů** vyberte ovládací prvek **popisek** a přetáhněte ho do formuláře a přetáhněte ho pod **tlačítko toto** tlačítko.

1. V části **Návrh** nebo **(datové vazby)** v okně **vlastnosti** změňte název **Label1** na a `lblHelloWorld` potom stiskněte klávesu **ENTER**.

### <a name="add-code-to-the-form"></a>Přidat kód do formuláře

1. V okně **&#93;. vb &#91;návrhu ** dvakrát klikněte na tlačítko **kliknutím na toto** tlačítko otevřete okno **Form1. vb** .

      (Případně můžete rozbalit **Form1. vb** v **Průzkumník řešení**a potom kliknout na **Form1**.)

1. V okně **Form1. vb** , mezi **soukromými** a **koncovými dílčími** řádky zadejte nebo zadejte, `lblHelloWorld.Text = "Hello World!"` jak je znázorněno na následujícím snímku obrazovky:

     ![Přidat kód do formuláře](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Kliknutím na tlačítko **Spustit** spusťte aplikaci.

     ![Kliknutím na spustit můžete aplikaci ladit a spustit.](../ide/media/vb-click-start-hello-world.png)

   Proběhne několik věcí. V integrovaném vývojovém prostředí sady Visual Studio se otevře okno **diagnostické nástroje** a otevře se okno **výstup** . Ale mimo integrované vývojové prostředí (IDE), zobrazí se dialogové okno **Form1** . Bude obsahovat vaše **kliknutí na toto** tlačítko a text, který říká **Label1**.

1. Klikněte na tlačítko **Toto** tlačítko v dialogovém okně **Form1** . Všimněte si, že text **Label1** se změní na **Hello World!**.

    ![Dialogové okno Form1, které obsahuje text Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zavřením dialogového okna **Form1** zastavíte běh aplikace.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz: vytvoření prohlížeče obrázků](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také

* [Další kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [Kurzy C#](/visualstudio/get-started/csharp/)
* [Kurzy C++](/cpp/get-started/tutorial-console-cpp)
