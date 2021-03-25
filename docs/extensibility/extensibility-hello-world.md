---
title: Kurz k rozšíření Hello World | Microsoft Docs
description: Naučte se, jak přidat nový příkaz jako rozšíření do sady Visual Studio, která zahrnuje vytvoření projektu, přidání příkazu a úpravu zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec465eda5a0bd7d017c3822390d68b43f76b5c47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070177"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Kurz – vytvoření prvního rozšíření: Hello World

Tento Hello World příklad vás provede vytvořením prvního rozšíření pro Visual Studio. V tomto kurzu se dozvíte, jak přidat nový příkaz do sady Visual Studio.

V tomto procesu se naučíte:

* **[Vytvořit projekt rozšiřitelnosti](#create-an-extensibility-project)**
* **[Přidat vlastní příkaz](#add-a-custom-command)**
* **[Úprava zdrojového kódu](#modify-the-source-code)**
* **[Spusťte skript.](#run-it)**

V tomto příkladu budete pomocí jazyka Visual C# přidat vlastní tlačítko nabídky s názvem "vyslovit Hello World!". to vypadá takto:

![Hello World – příkaz](media/hello-world-say-hello-world.png)

> [!NOTE]
> Tento článek se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [návod k rozšíření v Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Požadavky

Než začnete, ujistěte se, že máte nainstalovanou úlohu **vývoj rozšíření sady Visual Studio** , která obsahuje i šablonu VSIX, kterou budete potřebovat, a ukázkový kód.

> [!NOTE]
> K vytvoření projektu rozšiřitelnosti sady Visual Studio můžete použít libovolnou edici sady Visual Studio (Community, Professional nebo Enterprise).

## <a name="create-an-extensibility-project"></a>Vytvořit projekt rozšiřitelnosti

::: moniker range="vs-2017"

Krok 1. V nabídce **soubor** vyberte možnost **Nový**  >  **projekt**.

Krok 2. Do vyhledávacího pole v pravém horním rohu zadejte "VSIX" a vyberte **projekt VSIX** Visual C#. Jako **název** v dolní části dialogového okna zadejte "HelloWorld" a vyberte **OK**.

![Nový projekt](media/hello-world-new-project.png)

Nyní by se měla zobrazit stránka Začínáme a některé ukázkové prostředky.

Pokud potřebujete tento kurz opustit a vrátit se k němu, můžete nový projekt HelloWorld najít na **úvodní stránce** v části **Poslední** .

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. V nabídce **soubor** vyberte možnost **Nový**  >  **projekt**. Vyhledejte "VSIX" a vyberte **projekt VSIX** Visual C# a pak **Další**.

Krok 2. Jako **název projektu** zadejte HelloWorld a vyberte **vytvořit**.

![Nový projekt](media/hello-world-new-project-2019.png)

Nyní byste měli vidět projekt HelloWorld v **Průzkumník řešení**.

::: moniker-end

## <a name="add-a-custom-command"></a>Přidat vlastní příkaz

Krok 1. Pokud vyberete soubor manifestu *. vsixmanifest* , můžete zjistit, jaké možnosti jsou měnitelné, jako je popis, autor a verze.

Krok 2. Klikněte pravým tlačítkem na projekt (ne řešení). V místní nabídce vyberte položku **Přidat** a **Nová položka**.

Krok 3. Vyberte oddíl **rozšiřitelnost** a pak zvolte **příkaz**.

Krok 4: V dolní části pole **název** zadejte název souboru, například *Command. cs*.

![vlastní příkaz](media/hello-world-vsix-command.png)

Váš nový soubor příkazů je viditelný v **Průzkumník řešení**. V uzlu **Resources (prostředky** ) najdete další soubory, které souvisejí s vaším příkazem. Například pokud chcete upravit obrázek, soubor PNG je zde.

## <a name="modify-the-source-code"></a>Úprava zdrojového kódu

V tuto chvíli je text příkazu a tlačítka automaticky vygenerován a není velmi zajímavý. V případě, že chcete provést změny, můžete upravit soubor VSCT a soubor CS.

* Soubor VSCT je místo, kde můžete přejmenovat příkazy a definovat, kde se nacházejí v příkazovém systému sady Visual Studio. Při zkoumání souboru VSCT si všimnete komentářů, které vysvětlují, co jednotlivé části ovládacích prvků kódu VSCT.

* Soubor CS je tam, kde můžete definovat akce, jako je například obslužná rutina kliknutí.

::: moniker range="vs-2017"

Krok 1. V **Průzkumník řešení** vyhledejte soubor vsct pro nový příkaz. V takovém případě se bude volat *CommandPackage. vsct*.

![vsct balíčku příkazů](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Krok 1. V **Průzkumník řešení** vyhledejte soubor vsct pro balíček rozšíření vs. V takovém případě se bude volat *HelloWorldPackage. vsct*.

::: moniker-end

Krok 2. Změňte `ButtonText` parametr na `Say Hello World!` .

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

Krok 3. Vraťte se na **Průzkumník řešení** a vyhledejte soubor *Command. cs* . V `Execute` metodě změňte řetězec `message` z `string.Format(..)` na `Hello World!` .

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

Ujistěte se, že jste změny uložili do každého souboru.

## <a name="run-it"></a>Spusťte skript.

Nyní můžete spustit zdrojový kód v experimentální instanci sady Visual Studio.

Krok 1. Stisknutím klávesy **F5** spusťte příkaz **Spustit ladění** . Tento příkaz sestaví projekt a spustí ladicí program, který spouští novou instanci sady Visual Studio s názvem **experimentální instance**.

::: moniker range="vs-2017"

V záhlaví sady Visual Studio se zobrazí slova **experimentální instance** .

![experimentální záhlaví instance](media/hello-world-exp-instance.png)

::: moniker-end

Krok 2. V nabídce **nástroje** **experimentální instance** klikněte na příkaz **Hello World!**.

![konečný výsledek](media/hello-world-final-result.png)

Měl by se zobrazit výstup z nového vlastního příkazu, v tomto případě se zobrazí dialogové okno uprostřed obrazovky, které vám nabídne **Hello World!** .

## <a name="next-steps"></a>Další kroky

Teď, když znáte základy práce s rozšiřitelným rozšířením sady Visual Studio, se dozvíte, kde se můžete dozvědět víc:

* [Začněte vyvíjet rozšíření sady Visual Studio](starting-to-develop-visual-studio-extensions.md) – ukázky, kurzy. a publikování rozšíření
* [Co je nového v sadě Visual studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) – nové funkce rozšíření v sadě visual Studio 2017
* [Co je nového v sadě Visual studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) – nové funkce rozšíření v sadě visual Studio 2019
* V sadě [Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) se dozvíte podrobnosti o rozšiřitelnosti sady Visual Studio.
