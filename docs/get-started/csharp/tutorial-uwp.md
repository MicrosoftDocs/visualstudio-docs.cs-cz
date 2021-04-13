---
title: 'Vytvoření aplikace pro UWP pomocí sady Visual Studio a C #'
description: 'Vytvoření aplikace UWP v aplikaci Visual Studio s použitím jazyka XAML a jazyka C #'
titleSuffix: ''
ms.custom: seodec18, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2e68039e02a6181ef7970fdc6a1b3bd6ad173093
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295634"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Kurz: Vytvoření první aplikace Univerzální platforma Windows v aplikaci Visual Studio s použitím jazyka XAML a jazyka C&#35;

V tomto úvodu do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte aplikaci Hello World, která běží na jakémkoli zařízení s Windows 10. K tomu použijete šablonu projektu Univerzální platforma Windows (UWP), jazyk Extensible Application Markup Language (XAML) (XAML) a programovací jazyk C#.

::: moniker range="vs-2017"
Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.
::: moniker-end
::: moniker range="vs-2019"
Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.
::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvořte projekt Univerzální platforma Windows. Typ projektu se dodává se všemi soubory šablon, které potřebujete, předtím, než jste dokonce přidali cokoli!

::: moniker range="vs-2017"
1. Otevřete sadu Visual Studio.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **Visual C#** a pak zvolte možnost **univerzální pro systém Windows**. V prostředním podokně vyberte **prázdná aplikace (univerzální pro Windows)**. Pak pojmenujte projekt *Hello* a zvolte **OK**.

   > [!NOTE]
   > Zajistěte, aby umístění zdrojového projektu bylo na nové jednotce se systémem **souborů NTFS (Technology File System)** , například na jednotce operačního systému (OS). V opačném případě může dojít k potížím při sestavování a spouštění projektu. 

   ![Šablona univerzálního projektu Windows v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Pokud nevidíte šablonu projektu **prázdná aplikace (univerzální pro Windows)** , klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** .<br><br>![Klikněte na odkaz otevřít Instalační program pro Visual Studio v dialogovém okně Nový projekt.](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Spustí se instalační program pro Visual Studio. Zvolte **Univerzální platforma Windows úlohy vývoje** a pak zvolte **Upravit**.<br><br>![Univerzální platforma Windows úlohy vývoje v Instalační program pro Visual Studio](media/uwp-dev-workload.png)

1. V dialogovém okně **Nový projekt Univerzální platforma Windows** přijměte výchozí nastavení **cílové verze** a **Minimální verze** .

   ![Přijměte výchozí cílovou verzi a minimální verzi nastavení v dialogovém okně Nový projekt Univerzální platforma Windows.](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otevřete Visual Studio a v okně Start vyberte **vytvořit nový projekt**.

1. Na obrazovce **vytvořit nový projekt** do vyhledávacího pole zadejte *Universal Windows* , zvolte šablonu C# pro **prázdnou aplikaci (univerzální pro Windows)** a klikněte na tlačítko **Další**.

   ![Snímek obrazovky s vytvořením nového projektu](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Pokud nevidíte šablonu projektu **prázdná aplikace (univerzální pro Windows)** , klikněte na odkaz **instalovat další nástroje a funkce** .<br><br>![Klikněte na odkaz instalovat další nástroje a funkce.](media/vs-2019/uwp-not-finding.png)<br><br>Spustí se instalační program pro Visual Studio. Zvolte **Univerzální platforma Windows úlohy vývoje** a pak zvolte **Upravit**.<br><br>![Univerzální platforma Windows úlohy vývoje v Instalační program pro Visual Studio](media/uwp-dev-workload.png)

1. Dejte projektu název, _HelloWorld_ a klikněte na **vytvořit**.

   ![Obrazovka konfigurace projektu](media/vs-2019/uwp-configure-your-project.png)

1. V dialogovém okně **Nový projekt Univerzální platforma Windows** přijměte výchozí nastavení **cílové verze** a **Minimální verze** .

   ![Přijměte výchozí cílovou verzi a minimální verzi nastavení v dialogovém okně Nový projekt Univerzální platforma Windows.](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Pokud jste aplikaci Visual Studio poprvé použili k vytvoření aplikace pro UWP, může se zobrazit dialogové okno **Nastavení** . Zvolte **režim vývojář** a pak zvolte **Ano**.<br><br>
   > ![Povolení režimu vývojářů v dialogovém okně nastavení UWP](media/enable-developer-mode.png)<br><br>Sada Visual Studio nainstaluje další balíček vývojářského režimu za vás. Po dokončení instalace balíčku zavřete dialogové okno **Nastavení** .

## <a name="create-the-application"></a>Vytvoření aplikace

Je čas začít vyvíjet. Přidáte ovládací prvek tlačítko, přidáte pro něj akci a pak spustíte aplikaci "Hello World", abyste viděli, co vypadá jako.

### <a name="add-a-button-to-the-design-canvas"></a>Přidání tlačítka na plátno návrhu

1. V **Průzkumník řešení** dvakrát klikněte na *MainPage. XAML* a otevřete rozdělené zobrazení.

   ::: moniker range="vs-2017"
   ![Otevřete MainPage. XAML z Průzkumník řešení ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Otevřete MainPage. XAML z Průzkumník řešení](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Existují dvě podokna: **Návrhář XAML**, který obsahuje plátno návrhu, a **Editor jazyka XAML**, kde můžete přidat nebo změnit kód.

   ![Podokno Návrhář XAML v editoru XAML](media/uwp-xaml-editor.png)

1. Vyberte **panel nástrojů** a otevřete tak okno s časovým obdobím panelu nástrojů.

   ![Kliknutím na panel nástrojů otevřete okno s časovým obdobím panelu nástrojů.](media/uwp-toolbox.png)

   (Pokud nevidíte možnost **panelu nástrojů** , můžete ji otevřít z řádku nabídek. Provedete to tak , že kliknete na  >  **panel nástrojů** zobrazení. Nebo stiskněte klávesu **CTRL** + **ALT** + **X**.)

1. Kliknutím na ikonu **připnutí** můžete ukotvit okno panelu nástrojů.

   ![Kliknutím na ikonu připnutí můžete ukotvit okno panelu nástrojů.](media/uwp-toolbox-autohide.png)

1. Klikněte na ovládací prvek **tlačítko** a přetáhněte ho na plátno pro návrh.

   ![Klikněte na ovládací prvek tlačítko a přetáhněte ho na plátno pro návrh.](media/uwp-toolbox-add-button-control.png)

   Pokud se podíváte na kód v **editoru XAML**, uvidíte, že tlačítko bylo přidáno také.

   ![Zobrazit tlačítko v editoru XAML](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Přidání popisku na tlačítko

1. V **editoru XAML** změňte hodnotu obsahu tlačítka z "tlačítko" na "Hello World!"

   ![Změňte hodnotu obsahu tlačítka na Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. Všimněte si, že se změní tlačítko v **Návrhář XAML** .

   ![Tlačítko se změní na Hello World na plátně návrhu](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Přidání obslužné rutiny události

"Obslužná rutina události" je složitá, ale je to pouze jiný název kódu, který je volán, když dojde k události. V tomto případě přidá akci do "Hello World!". .

1. Dvakrát klikněte na ovládací prvek tlačítko na plátně návrhu.

1. Upravte kód obslužné rutiny události v souboru *MainPage. XAML. cs*, na stránce s kódem na pozadí.

   Tady je místo, kde se dostanete zajímavě. Výchozí obslužná rutina události vypadá takto:

   ![Výchozí obslužná rutina události Button_Click ](media/uwp-button-click-code.png)

   Pojďme změnit, aby vypadala takto:

   ![Nová obslužná rutina události asynchronního Button_Click ](media/uwp-add-hello-world-async-code.png)

   Zde je kód ke zkopírování a vložení:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>Co máme jenom vy?

Kód používá některá rozhraní API systému Windows k vytvoření objektu syntézy řeči a pak mu dává text, který je třeba vyslovit. (Další informace o použití naleznete v `SpeechSynthesis` tématu  <xref:System.Speech.Synthesis> .)

## <a name="run-the-application"></a>Spuštění aplikace

::: moniker range="vs-2017"
Je čas sestavování, nasazování a spuštění aplikace "Hello World", která zobrazuje vzhled a zvuky jako. Jak na to:

1. K spuštění aplikace v místním počítači použijte tlačítko Přehrát ( **místní počítač** obsahuje text).

   ![Kliknutím na místní počítač spustíte a naladíte aplikaci UWP.](media/uwp-start-or-debug.png)

   (Případně můžete zvolit **ladění** > **Spusťte ladění** z řádku nabídek nebo stiskněte klávesu F5 pro spuštění aplikace.)

1. Zobrazte si aplikaci, která se zobrazí, jakmile se nezobrazí úvodní obrazovka. Aplikace by měla vypadat nějak takto:

   ![Aplikace Hello World UWP](media/uwp-hello-world-app.png)

1. Klikněte na tlačítko **Hello World** .

   Vaše zařízení s Windows 10 bude doslova vyslovit text "Hello, World!".

1. Pokud chcete aplikaci zavřít, klikněte na tlačítko **Zastavit ladění** na panelu nástrojů. (Případně můžete zvolit **ladění**  >  **Zastavte ladění** z řádku nabídek nebo stiskněte klávesy Shift + F5.)

::: moniker-end
::: moniker range=">=vs-2019"
Je čas sestavování, nasazování a spuštění aplikace "Hello World", která zobrazuje vzhled a zvuky jako. Jak na to:

1. K spuštění aplikace v místním počítači použijte tlačítko Přehrát ( **místní počítač** obsahuje text).

   ![Kliknutím na místní počítač spustíte a naladíte aplikaci UWP.](media/uwp-start-or-debug.png)

   (Případně můžete zvolit **ladění** > **Spusťte ladění** z řádku nabídek nebo stiskněte klávesu F5 pro spuštění aplikace.)

1. Zobrazte si aplikaci, která se zobrazí, jakmile se nezobrazí úvodní obrazovka. Aplikace by měla vypadat nějak takto:

   ![Aplikace Hello World UWP](media/vs-2019/uwp-hello-world-app.png)

1. Klikněte na tlačítko **Hello World** .

   Vaše zařízení s Windows 10 bude doslova vyslovit text "Hello, World!".

1. Pokud chcete aplikaci zavřít, klikněte na tlačítko **Zastavit ladění** na panelu nástrojů. (Případně můžete zvolit **ladění**  >  **Zastavte ladění** z řádku nabídek nebo stiskněte klávesy Shift + F5.)

::: moniker-end

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Doufáme, že jste se seznámili se základními informacemi o UWP a prostředí IDE sady Visual Studio. Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Vytvoření uživatelského rozhraní](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Viz také

- [Přehled UPW](/windows/uwp/get-started/universal-application-platform-guide)
- [Získat ukázky aplikace pro UWP](/windows/uwp/get-started/get-uwp-app-samples)
