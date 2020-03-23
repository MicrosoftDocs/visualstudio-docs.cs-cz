---
title: 'Vytvoření aplikace pro univerzální platformu Windows (UPW) s Visual Studio a C #'
description: 'Vytvoření aplikace UPW v Sadě Visual Studio s XAML a C #'
titleSuffix: ''
ms.custom: seodec18, get-started
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8be56581374aefbef41a5173836d1189cceff290
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579997"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Kurz: Vytvořte první univerzální aplikaci platformy Windows v sadě Visual Studio s xaml a c&#35;

V tomto úvodu do integrovaného vývojového prostředí Visual Studio (IDE) vytvoříte aplikaci "Hello World", která běží na libovolném zařízení s Windows 10. Chcete-li tak učinit, budete používat šablonu projektu univerzální platformy Windows (UPW), extensible application markup language (XAML) a programovací jazyk C#.

::: moniker range="vs-2017"
Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.
::: moniker-end
::: moniker range="vs-2019"
Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.
::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvořte projekt univerzální platformy Windows. Typ projektu je dodáván se všemi soubory šablon, které potřebujete, ještě předtím, než jste něco přidali!

::: moniker range="vs-2017"
1. Otevřete sadu Visual Studio.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte **položku Visual C#** a pak zvolte **Windows Universal**. V prostředním podokně zvolte **Prázdná aplikace (Univerzální Windows).** Poté pojmenujte projekt *HelloWorld* a zvolte **OK**.

   ![Šablona projektu Windows Universal v dialogovém okně Nový projekt v prostředí IDE sady Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Pokud šablonu projektu **Blank App (Universal Windows)** nevidíte, klikněte v levém podokně dialogového okna **Nový projekt** na odkaz Otevřít instalační program sady **Visual Studio.**<br><br>![V dialogovém okně Nový projekt klepněte na odkaz Otevřít instalační program sady Visual Studio.](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje univerzální platformy Windows** a pak zvolte **Změnit**.<br><br>![Úloha vývoje univerzální platformy Windows v Instalační službě sady Visual Studio](media/uwp-dev-workload.png)

1. Přijměte výchozí **cílovou verzi** a minimální nastavení **verze** v dialogovém okně Nový projekt **univerzální platformy Windows.**

   ![Přijetí výchozí cílové verze a minimálního nastavení verze v dialogovém okně Nový projekt univerzální platformy Windows](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otevřete Visual Studio a v počátečním okně zvolte **Vytvořit nový projekt**.

1. Na obrazovce **Vytvořit nový projekt** zadejte do vyhledávacího pole univerzální systém *Windows,* zvolte šablonu C# pro **prázdnou aplikaci (Univerzální windows)** a pak zvolte **Další**.

   ![Snímek obrazovky Vytvořit nový projekt](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Pokud šablonu projektu **Blank App (Universal Windows)** nevidíte, klikněte na odkaz **Instalovat další nástroje a funkce.**<br><br>![Klikněte na odkaz Instalovat další nástroje a funkce.](media/vs-2019/uwp-not-finding.png)<br><br>Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje univerzální platformy Windows** a pak zvolte **Změnit**.<br><br>![Úloha vývoje univerzální platformy Windows v Instalační službě sady Visual Studio](media/uwp-dev-workload.png)

1. Pojmenujte projekt _HelloWorld_a zvolte **Vytvořit**.

   ![Konfigurace obrazovky projektu](media/vs-2019/uwp-configure-your-project.png)

1. Přijměte výchozí **cílovou verzi** a minimální nastavení **verze** v dialogovém okně Nový projekt **univerzální platformy Windows.**

   ![Přijetí výchozí cílové verze a minimálního nastavení verze v dialogovém okně Nový projekt univerzální platformy Windows](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Pokud je to poprvé, co jste pomocí sady Visual Studio vytvořili aplikaci UPW, může se zobrazit dialogové okno **Nastavení.** Zvolte **Režim vývojáře**a pak zvolte **Ano**.<br><br>
   > ![Povolení režimu vývojáře v dialogovém okně Nastavení UPW](media/enable-developer-mode.png)<br><br>Visual Studio nainstaluje další balíček režimu pro vývojáře pro vás. Po dokončení instalace balíčku zavřete dialogové okno **Nastavení.**

## <a name="create-the-application"></a>Vytvoření aplikace

Je čas začít se rozvíjet. Přidáte ovládací prvek tlačítka, přidáte k tlačítku akci a pak spustíte aplikaci "Hello World", abyste zjistili, jak vypadá.

### <a name="add-a-button-to-the-design-canvas"></a>Přidání tlačítka na plátno Návrh

1. V **Průzkumníku řešení**poklepáním na *soubor MainPage.xaml* otevřete rozdělené zobrazení.

   ::: moniker range="vs-2017"
   ![Otevření souboru MainPage.xaml z Průzkumníka řešení ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Otevření souboru MainPage.xaml z Průzkumníka řešení](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Existují dvě podokna: **Návrhář XAML**, který obsahuje plátno návrhu, a **Editor XAML**, kde můžete přidat nebo změnit kód.

   ![Podokno Návrhář XAML v editoru XAML](media/uwp-xaml-editor.png)

1. Zvolte **Panel nástrojů,** chcete-li otevřít okno pro rozluštití panelu nástrojů.

   ![Kliknutím na Panel nástrojů otevřete okno pro rozluštit.](media/uwp-toolbox.png)

   (Pokud možnost **Panel nástrojů** nevidíte, můžete ji otevřít z řádku nabídek. Chcete-li tak učinit, zvolte **Zobrazit** > **panel nástrojů**. Nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**X**.)

1. Kliknutím na ikonu **Pin** ukotvíte okno Panelu nástrojů.

   ![Kliknutím na ikonu Pin ukotvíte okno panelu nástrojů.](media/uwp-toolbox-autohide.png)

1. Klikněte na ovládací prvek **Button** a přetáhněte ho na plátno návrhu.

   ![Klikněte na ovládací prvek Button a přetáhněte ho na plátno Návrh.](media/uwp-toolbox-add-button-control.png)

   Pokud se podíváte na kód v **Editoru XAML**, uvidíte, že tlačítko bylo přidáno i tam:

   ![Klikněte na ovládací prvek Button a přetáhněte ho na plátno Návrh.](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Přidání popisku k tlačítku

1. V **Editoru XAML**změňte hodnotu obsahu tlačítka z "Button" na "Hello World!"

   ![Změna hodnoty obsahu tlačítka na Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. Všimněte si, že se změní také tlačítko v **návrháři XAML.**

   ![Tlačítko se změní na Hello World na návrhovém plátně](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Přidání obslužné rutiny události

"Obslužná rutina události" zní složitě, ale je to jen jiný název kódu, který se nazývá, když dojde k události. V tomto případě přidá akci do "Hello World!" .

1. Poklepejte na ovládací prvek tlačítka na návrhovém plátně.

1. Upravte kód obslužné rutiny události v *MainPage.xaml.cs*, na stránce s kódem na pozadí.

   Zde je místo, kde se věci zajímavé. Výchozí obslužná rutina události vypadá takto:

   ![Výchozí obslužná rutina události Button_Click ](media/uwp-button-click-code.png)

   Změníme to, aby to vypadalo takto:

   ![Nová obslužná rutina události asynchronní Button_Click ](media/uwp-add-hello-world-async-code.png)

   Zde je kód pro kopírování a vkládání:

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

#### <a name="what-did-we-just-do"></a>Co jsme to právě udělali?

Kód používá některá okna API systému Windows k vytvoření objektu pro syntézu řeči a pak mu dává nějaký text. (Další informace o `SpeechSynthesis`používání <xref:System.Speech.Synthesis>naleznete v tématu .)

## <a name="run-the-application"></a>Spuštění aplikace


::: moniker range="vs-2017"
Je čas vytvořit, nasadit a spustit aplikaci "Hello World" UWP, abyste zjistili, jak vypadá a zní. Jak na to:

1. Pomocí tlačítka Přehrát (obsahuje text **Místní počítač)** spusťte aplikaci v místním počítači.

   ![Kliknutím na místní počítač spusťte a laděte aplikaci UPW.](media/uwp-start-or-debug.png)

   (Případně můžete zvolit **ladění** > **start ladění** z panelu nabídek nebo stisknutím klávesy F5 spustit aplikaci.)

1. Prohlédněte si aplikaci, která se objeví brzy po zmizení úvodní obrazovky. Aplikace by měla vypadat podobně jako tato:

   ![Aplikace "Hello World" pro UPW](media/uwp-hello-world-app.png)

1. Klikněte na tlačítko **Hello World.**

   Vaše zařízení se systémem Windows 10 doslova řekne: "Hello, World!"

1. Chcete-li aplikaci zavřít, klepněte na tlačítko **Zastavit ladění** na panelu nástrojů. (Případně zvolte **Ladění** > **Zastavte ladění** z řádku nabídek nebo stiskněte Shift+F5.)

::: moniker-end
::: moniker range=">=vs-2019"
Je čas vytvořit, nasadit a spustit aplikaci "Hello World" UWP, abyste zjistili, jak vypadá a zní. Jak na to:

1. Pomocí tlačítka Přehrát (obsahuje text **Místní počítač)** spusťte aplikaci v místním počítači.

   ![Kliknutím na místní počítač spusťte a laděte aplikaci UPW.](media/uwp-start-or-debug.png)

   (Případně můžete zvolit **ladění** > **start ladění** z panelu nabídek nebo stisknutím klávesy F5 spustit aplikaci.)

1. Prohlédněte si aplikaci, která se objeví brzy po zmizení úvodní obrazovky. Aplikace by měla vypadat podobně jako tato:

   ![Aplikace "Hello World" pro UPW](media/vs-2019/uwp-hello-world-app.png)

1. Klikněte na tlačítko **Hello World.**

   Vaše zařízení se systémem Windows 10 doslova řekne: "Hello, World!"

1. Chcete-li aplikaci zavřít, klepněte na tlačítko **Zastavit ladění** na panelu nástrojů. (Případně zvolte **Ladění** > **Zastavte ladění** z řádku nabídek nebo stiskněte Shift+F5.)

::: moniker-end

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto výukového programu! Doufáme, že jste se dozvěděli některé základy o UWP a Visual Studio IDE. Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Vytvoření uživatelského rozhraní](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Viz také

- [Přehled UPW](/windows/uwp/get-started/universal-application-platform-guide)
- [Získání ukázek aplikací UPW](/windows/uwp/get-started/get-uwp-app-samples)