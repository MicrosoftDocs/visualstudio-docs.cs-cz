---
title: Kurz Hello World rozšíření | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2122a98778372690990a75269be2f3087653678
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349462"
---
# <a name="create-your-first-extension-hello-world"></a>Vytvořit své první rozšíření: Hello World

V tomto příkladu Hello World vás provede vytvořením své první rozšíření pro Visual Studio. V tomto kurzu se dozvíte, jak přidat nový příkaz do sady Visual Studio.

V procesu, se dozvíte, jak:

* **[Vytvořit projekt rozšíření](#create-an-extensibility-project)**
* **[Přidat vlastní příkaz.](#add-a-custom-command)**
* **[Změnit zdrojový kód](#modify-the-source-code)**
* **[Infrastruktura.](#run-it)**

V tomto příkladu použijete Visual C# můžete přidat že vlastní tlačítko s názvem "Řekněme, že Hello World!" který vypadá takto:

![Příkaz Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Tento článek se týká k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [návod rozšíření v sadě Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Požadavky

Než začnete, ujistěte se, že jste nainstalovali **vývoj rozšíření sady Visual Studio** úlohu, která zahrnuje VSIX šablony budete potřebovat a ukázkový kód.

> [!NOTE]
> Můžete použít všechny edice sady Visual Studio (Community, Professional nebo Enterprise) Chcete-li vytvořit projekt rozšíření sady Visual Studio.

## <a name="create-an-extensibility-project"></a>Vytvořit projekt rozšíření

Krok 1. Z **souboru** nabídky, klikněte na tlačítko **nový projekt**. V dolní části obrazovky zadejte název vašeho projektu.

Krok 2. Z **šablony** nabídky, klikněte na tlačítko **Visual C#**, klikněte na tlačítko **rozšiřitelnost**a potom klikněte na tlačítko **projekt VSIX**.

![Nový projekt](media/hello-world-new-project.png)

Teď byste měli vidět stránku Začínáme a některé ukázkové prostředky.

Pokud potřebujete ponechat v tomto kurzu, vraťte se do něj, můžete najít váš nový projekt Hello World na **úvodní stránka** v **poslední** oddílu.

## <a name="add-a-custom-command"></a>Přidat vlastní příkaz.

Krok 1. Pokud vyberete manifest, uvidíte, jaké možnosti jsou uvažovat instance, metadat, popis a verze.

Krok 2. Klikněte pravým tlačítkem na projekt (nikoli řešení). V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nová položka**.

Krok 3. Vyberte **rozšiřitelnost** části a potom klikněte na tlačítko **vlastního příkazu**.

Krok 4. V **název** pole v dolní části, pojmenujte ho, například *Command.cs*.

![vlastní příkaz.](media/hello-world-custom-command.png)

Nový příkaz je uveden v **Průzkumníka řešení** pod **prostředky** větve. Toto je také kde najdete další soubory související s příkazu, jako jsou soubory PNG a ICO, pokud chcete změnit bitovou kopii.

## <a name="modify-the-source-code"></a>Změnit zdrojový kód

V tomto okamžiku je tlačítko, které přidáváte poměrně Obecné. Budete muset upravit VSCT soubor a soubor CS, pokud chcete provádět změny.

* Soubor VSCT je, kde je můžete přejmenovat příkazům, jakož i definují, kam obrátit příkaz systému Visual Studio. Při prohlížení souboru VSCT uvidíte velké množství komentářem kódu, který vysvětluje, co každý oddíl ovládacích prvků kódu.

* Soubor CS je, ve kterém můžete definovat akce, jako je například obslužné rutiny kliknutí.

Krok 1. V **Průzkumníka řešení**, najít soubor VSCT pro nový příkaz. V takovém případě bude volána *CommandPackage.vsct*.

![příkaz balíčku vsct](media/hello-world-command-package-vsct.png)

Krok 2. Změnit `ButtonText` parametr `Say Hello World!`.

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

Krok 3. Přejděte zpět na **Průzkumníka řešení** a najít *Command.cs* souboru. Změňte řetězec `message` pro příkaz `string.Format(..)` k `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

Nezapomeňte si uložit změny do každého souboru.

## <a name="run-it"></a>Infrastruktura.

Nyní můžete spustit zdrojový kód v experimentální instanci aplikace Visual Studio.

Krok 1. Klikněte na tlačítko **Start** na panelu nástrojů. Toto sestavení vašeho projektu a spustí ladicí program spouští novou instanci sady Visual Studio, volá se, **experimentální instanci**.

Zobrazí se slova **experimentální instanci** v záhlaví programu sady Visual Studio.

![experimentální instanci záhlaví](media/hello-world-exp-instance.png)

Krok 2. Na **nástroje** nabídku **experimentální instanci**, klikněte na tlačítko **Say Hello World!**.

![Konečný výsledek](media/hello-world-final-result.png)

Byste měli vidět výstup z vlastního příkazu, v tomto případě dialogové okno do středu obrazovky, který poskytuje **Hello World!** zpráva.

## <a name="next-steps"></a>Další kroky

Teď, když znáte základy práce se rozšíření produktu Visual Studio, zde je, kde můžete další informace:

* [Začněte vyvíjet rozšíření aplikace Visual Studio](starting-to-develop-visual-studio-extensions.md) – ukázky, kurzy. a publikování rozšíření
* [Co je nového ve Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) – nové funkce rozšíření v sadě Visual Studio 2017
* [V sadě Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) – další podrobnosti o rozšíření produktu Visual Studio