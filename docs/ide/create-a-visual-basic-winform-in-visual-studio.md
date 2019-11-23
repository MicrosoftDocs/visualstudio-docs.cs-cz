---
title: Vytvoření aplikace model Windows Forms s Visual Basic
description: Zjistěte, jak vytvořit aplikaci Windows Forms v sadě Visual Studio pomocí jazyka Visual Basic, krok za krokem.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8be3edaaab970dab7ef41bd8bce75c84bac54a2e
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71681582"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Vytvoření Windows Forms aplikace v sadě Visual Studio pomocí jazyka Visual Basic

V této krátké Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou aplikaci Visual Basic, který má na základě Windows uživatelského rozhraní (UI).

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chtěli, najdete v článku [přizpůsobit IDE sady Visual Studio a Editor](../ide/quickstart-personalize-the-ide.md) stránku a zjistěte, jak.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace Visual Basic. Typ projektu obsahuje všechny soubory šablon, které potřebujete, než jste přidali ještě něco.

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017.

1. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V **nový projekt** dialogové okno v levém podokně rozbalte **jazyka Visual Basic**a klikněte na tlačítko **Windows Desktop**. V prostředním podokně vyberte **aplikace Windows Forms (.NET Framework)** . Potom zadejte název souboru `HelloWorld`.

     Pokud se nezobrazí **aplikace Windows Forms (.NET Framework)** projektu šablony, zrušte z celkového počtu **nový projekt** dialogového okna a v horní nabídce vyberte **nástroje**  >  **Získejte nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** úloh, klikněte na tlačítko **změnit**.

     ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)

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
   > ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte svůj projekt HelloWorld.](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu jazyka Visual Basic a název souboru, Visual Studio otevře formulář za vás. Formulář je uživatelské rozhraní Windows. Vytvoříme aplikaci "Hello World" přidáním ovládacích prvků do formuláře a pak aplikaci spustíme.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Klikněte na tlačítko **nástrojů** nabídka okno nástrojů.

     ![Klikněte na panelu nástrojů okno nástrojů](../ide/media/vb-toolbox-toolwindow.png)

     (Pokud se nezobrazí **nástrojů** nabídka možností, lze jej otevřít z řádku nabídek. Provedete to tak, že **zobrazíte** > **sadu nástrojů**. Také můžete stisknout klávesu **Ctrl**+**Alt**+**X**.)

1. Klikněte na tlačítko **Pin** ikonu ukotvení **nástrojů** okna.

     ![Klikněte na ikonu připínáčku připněte okno nástrojů do integrovaného vývojového prostředí](../ide/media/vb-pin-the-toolbox-window.png)

1. Klikněte na tlačítko **tlačítko** řídit a přetáhněte ji na formuláři.

     ![Přidání tlačítka do formuláře](../ide/media/vb-add-a-button-to-form1.png)

1. V části **vzhled** (nebo v části **písma** ) v okně **vlastnosti** zadejte `Click this`a potom stiskněte klávesu **ENTER**.

     ![Přidejte text pro tlačítko ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud se nezobrazí **vlastnosti** okna, lze jej otevřít z řádku nabídek. Chcete-li tak učinit, klikněte na tlačítko **zobrazení** > **okno vlastností**. Také můžete stisknout klávesu **F4**.)

1. V **návrhu** část **vlastnosti** okna, změňte název z **Button1** k `btnClickThis`a potom stiskněte klávesu **Enter**.

     ![Přidání funkce do tlačítko ve formuláři](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Pokud jste v okně **vlastnosti** v abecedním seznamu, zobrazí se v části **(DataBindings)** ikona **Button1** místo toho.

### <a name="add-a-label-to-the-form"></a>Přidejte popisek do formuláře

Teď, když jsme přidali ovládací prvek tlačítko Vytvořit akci, přidáme popisek ovládacího prvku k odeslání text, který se.

1. Vyberte **popisek** ovládacího prvku **nástrojů** okna a přetáhněte ji na formuláři a přetáhněte ho pod **kliknutím na tuto** tlačítko.

1. V části **Návrh** nebo **(datové vazby)** v okně **vlastnosti** změňte název **Label1** na `lblHelloWorld`a potom stiskněte klávesu **ENTER**.

### <a name="add-code-to-the-form"></a>Přidejte kód do formuláře

1. V **Form1.vb &#91;návrhu&#93;**  okna, dvakrát klikněte **kliknutím na tuto** tlačítko Otevřít **Form1.vb** okna.

      (Alternativně můžete rozbalit **Form1.vb** v **Průzkumníka řešení**a potom klikněte na tlačítko **Form1**.)

1. V okně **Form1. vb** zadejte mezi **soukromými** a **koncovými dílčími** řádky `lblHelloWorld.Text = "Hello World!"`, jak je znázorněno na následujícím snímku obrazovky:

     ![Přidejte kód do formuláře](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Klikněte na tlačítko **Start** tlačítko ke spuštění aplikace.

     ![Klikněte na příkaz Spustit ladění a spuštění aplikace](../ide/media/vb-click-start-hello-world.png)

   Stane se několik věcí. V sadě Visual Studio IDE **diagnostické nástroje** otevře se okno a **výstup** otevře se okno, příliš. Ale mimo rozhraní IDE **Form1** zobrazí se dialogové okno. Bude obsahovat vaše **kliknutím na tuto** tlačítko a text, který říká **Label1**.

1. Klikněte na tlačítko **kliknutím na tuto** tlačítko **Form1** dialogové okno. Všimněte si, **Label1** text změní na **Hello World!** .

    ![Dialogové okno Form1, které obsahuje Label1 text ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zavřením dialogového okna **Form1** zastavíte běh aplikace.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz: vytvoření prohlížeče obrázků](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Viz také:

* [Další kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [C#výuka](/visualstudio/get-started/csharp/)
* [C++výuka](/cpp/get-started/tutorial-console-cpp)
