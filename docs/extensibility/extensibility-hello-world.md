---
title: Hello World rozšíření tutorial | Dokumenty společnosti Microsoft
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711663"
---
# <a name="create-your-first-extension-hello-world"></a>Vytvořte si první rozšíření: Hello World

Tento příklad Hello World vás provede vytvořením prvního rozšíření pro Visual Studio. Tento kurz ukazuje, jak přidat nový příkaz do sady Visual Studio.

V tomto procesu se naučíte, jak:

* **[Vytvoření projektu rozšiřitelnosti](#create-an-extensibility-project)**
* **[Přidání vlastního příkazu](#add-a-custom-command)**
* **[Úprava zdrojového kódu](#modify-the-source-code)**
* **[Spusťte skript.](#run-it)**

V tomto příkladu použijete visual c# k přidání vlastního tlačítka nabídky s názvem "Say Hello World!" to vypadá takto:

![Hello World, příkaz](media/hello-world-say-hello-world.png)

> [!NOTE]
> Tento článek se vztahuje na Visual Studio v systému Windows. Visual Studio pro Mac najdete [v návodu k rozšiřitelnosti v Visual Studiu pro Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Požadavky

Než začnete, ujistěte se, že jste nainstalovali zatížení **vývoje rozšíření Sady Visual Studio,** která obsahuje šablonu VSIX, kterou budete potřebovat, a ukázkový kód.

> [!NOTE]
> K vytvoření projektu rozšiřitelnosti sady Visual Studio můžete použít libovolnou edici sady Visual Studio (Community, Professional nebo Enterprise).

## <a name="create-an-extensibility-project"></a>Vytvoření projektu rozšiřitelnosti

::: moniker range="vs-2017"

Krok 1. V nabídce **Soubor** vyberte **Nový** > **projekt**.

Krok 2. Do vyhledávacího pole v pravém horním horním textu zadejte "vsix" a vyberte visual c# **vsix projektu**. Zadejte "HelloWorld" pro **název** v dolní části dialogového okna a vyberte **OK**.

![nový projekt](media/hello-world-new-project.png)

Nyní byste měli vidět stránku Začínáme a některé ukázkové prostředky.

Pokud potřebujete opustit tento kurz a vrátit se k němu, můžete najít svůj nový projekt HelloWorld na **úvodní stránce** v části **Poslední.**

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. V nabídce **Soubor** vyberte **Nový** > **projekt**. Vyhledejte "vsix" a vyberte Visual C# **VSIX Project** a potom **Další**.

Krok 2. Zadejte "HelloWorld" pro **název projektu** a vyberte **Vytvořit**.

![nový projekt](media/hello-world-new-project-2019.png)

Nyní byste měli vidět HelloWorld projektu v **Průzkumníku řešení**.

::: moniker-end

## <a name="add-a-custom-command"></a>Přidání vlastního příkazu

Krok 1. Pokud vyberete soubor manifestu *.vsixmanifest,* uvidíte, jaké možnosti lze změnit, například popis, autor a verze.

Krok 2. Klikněte pravým tlačítkem myši na projekt (ne na řešení). V místní nabídce vyberte **Přidat**a potom **Položku Nová**.

Krok 3. Vyberte část **Rozšiřitelnost** a pak zvolte **Příkaz**.

Krok 4. Do pole **Název** v dolní části zadejte název souboru, například *Command.cs*.

![vlastní příkaz](media/hello-world-vsix-command.png)

Nový soubor příkazů je viditelný v **Průzkumníku řešení**. V uzlu **Prostředky** najdete další soubory související s vaším příkazem. Chcete-li například upravit obrázek, soubor PNG je zde.

## <a name="modify-the-source-code"></a>Úprava zdrojového kódu

V tomto okamžiku příkaz a tlačítko text jsou automaticky generovány a není příliš zajímavé. Chcete-li provést změny, můžete upravit soubor VSCT a soubor CS.

* Soubor VSCT je místo, kde můžete přejmenovat příkazy, stejně jako definovat, kam jdou v systému příkazů sady Visual Studio. Při zkoumání souboru VSCT, všimnete si komentáře, které vysvětlují, co jednotlivé části ovládacích prvků kódu VSCT.

* Soubor CS je místo, kde můžete definovat akce, jako je například obslužná rutina kliknutí.

::: moniker range="vs-2017"

Krok 1. V **Průzkumníku řešení**vyhledejte soubor VSCT pro nový příkaz. V tomto případě se bude jmenovat *CommandPackage.vsct*.

![příkaz balíček vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. V **Průzkumníku řešení**vyhledejte soubor VSCT pro příponu VS balíček. V tomto případě se bude jmenovat *HelloWorldPackage.vsct*.

::: moniker-end

Krok 2. Změňte `ButtonText` parametr `Say Hello World!`na .

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Krok 3. Vraťte se do **Průzkumníka řešení** a vyhledejte *soubor Command.cs.* V `Execute` metodě změňte `message` `string.Format(..)` řetězec `Hello World!`z na .

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Nezapomeňte uložit změny do každého souboru.

## <a name="run-it"></a>Spusťte skript.

Nyní můžete spustit zdrojový kód v instanci experimentální sady Visual Studio.

Krok 1. Stisknutím **klávesy F5** spusťte příkaz **Spustit ladění.** Tento příkaz vytvoří projekt a spustí ladicí program a spustí novou instanci sady Visual Studio nazvanou **Experimentální instance**.

::: moniker range="vs-2017"

Slova **Experimentální instance** se zobrazí v záhlaví sady Visual Studio.

![záhlaví experimentální instance](media/hello-world-exp-instance.png)

::: moniker-end

Krok 2. V nabídce **Nástroje** **experimentální instance**klikněte na Say **Hello World!**.

![konečný výsledek](media/hello-world-final-result.png)

Měli byste vidět výstup z vašeho nového vlastního příkazu, v tomto případě dialog ve středu obrazovky, který vám **Hello World!** zpráva.

## <a name="next-steps"></a>Další kroky

Teď, když znáte základy práce s rozšiřitelností sady Visual Studio, se dozvíte více:

* [Začněte vyvíjet rozšíření sady Visual Studio – ukázky,](starting-to-develop-visual-studio-extensions.md) kurzy. a publikování rozšíření
* [Co je nového ve Visual Studiu 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) – Nové funkce rozšiřitelnosti ve Visual Studiu 2017
* [Co je nového ve Visual Studiu 2019 SDK](whats-new-visual-studio-2019-sdk.md) – Nové funkce rozšiřitelnosti ve Visual Studiu 2019
* [Uvnitř sady Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) – naučte se podrobnosti o rozšiřitelnosti sady Visual Studio
