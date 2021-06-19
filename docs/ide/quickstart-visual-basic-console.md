---
title: Vytvoření první konzolové aplikace pomocí Visual Basic
description: Naučte se vytvářet jednoduchou Hello World konzoly v Visual Studio s Visual Basic pomocí podrobných kroků.
ms.custom: vs-acquisition
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 658faaf5b044f1c4fed70fa62f205c2fa025f640
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386238"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Rychlý start: Vytvoření první konzolové aplikace v Visual Studio pomocí Visual Basic

V tomto 5 až 10minutových úvodu Visual Studio integrovaného vývojového prostředí (IDE) vytvoříte jednoduchou aplikaci pro Visual Basic, která běží na konzole.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio 2022 Preview, přejděte na stránku [stahování Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt Visual Basic aplikace. Typ projektu se dodává se všemi soubory šablony, které budete potřebovat, ještě než budete něco přidávat.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

3. V dialogovém **okně Nový** projekt v levém podokně rozbalte **Visual Basic** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Konzolová aplikace (.NET Core).** Pak projekt pojmnujte *HelloWorld*.

   ![Šablona projektu Konzolová aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém Visual Studio Ide](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Pokud šablonu projektu Konzolová aplikace **(.NET Core)** nevidíte, klikněte na odkaz Otevřít **Instalační program pro Visual Studio** v levém podokně dialogového okna **Nový** projekt.

   ![V dialogovém okně Instalační program pro Visual Studio projektu klikněte na odkaz Otevřít projekt.](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**

     ![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Některé snímky obrazovky v tomto rychlém startu používají tmavý motiv. Pokud tmavý motiv používáte, ale chcete, podívejte se na stránku Přizpůsobení integrovaného vývojového Visual Studio a [editoru,](quickstart-personalize-the-ide.md) kde se dozvíte, jak.

1. Otevřete sadu Visual Studio.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

   ![Zobrazení okna Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V **okně Vytvořit nový** projekt zvolte **Visual Basic** ze seznamu Jazyk. Dále v seznamu Platforma zvolte **Windows** a **ze** seznamu typů projektů zvolte Konzola.

   Po použití filtrů jazyka, platformy a typu projektu zvolte šablonu **Konzolová** aplikace a pak zvolte **Další.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Zvolte šablonu Visual Basic pro konzolovou aplikaci.":::

   > [!NOTE]
   > Pokud šablonu Konzolová **aplikace nevidíte,** můžete ji nainstalovat z **okna Vytvořit nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce.
   >
   > ![Odkaz Install more tools and features (Nainstalovat další nástroje a funkce) ze zprávy Not finding what you're looking for (Najít, co hledáte) v okně Create new project (Vytvořit nový projekt)](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Potom v části Instalační program pro Visual Studio úlohu **Vývoj pro různé platformy v .NET Core.**
   >
   > ![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Potom zvolte tlačítko **Upravit** v Instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce. Pokud ano, proveďte to. Potom zvolte **Pokračovat a** nainstalujte úlohu. Pak se vraťte ke kroku 2 v[této proceduře "Vytvoření](#create-a-project)projektu".

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole Project name (Název **projektu)** zadejte nebo zadejte *WhatIsYourName.* Pak zvolte **Další.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="V okně Konfigurovat nový projekt pojmnujte projekt WhatIsYourName.":::

1. V okně **Další informace** by už mělo být pro cílovou rozhraní vybrané **rozhraní .NET Core 3.1.** Pokud ne, vyberte **.NET Core 3.1.** Pak zvolte **Vytvořit.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="V okně Další informace se ujistěte, že je vybraná možnost .NET Core 3.1.":::

   Visual Studio nový projekt otevřete.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony Visual Basic projektu a názvu projektu Visual Studio vytvoří jednoduchou "Hello World" aplikaci. Volá metodu <xref:System.Console.WriteLine%2A> , která zobrazí řetězec literálu "Hello World!" v okně konzoly.

![Zobrazení výchozího Hello World kódu ze šablony](../ide/media/vb-console-helloworld-template.png)

Pokud v integrovaném **vývojovém prostředí kliknete** na tlačítko HelloWorld, můžete program spustit v režimu ladění.

  ![Kliknutím na tlačítko Hello World spusťte program v režimu ladění.](../ide/media/vb-console-hello-world-button.png)

Když to použijete, zobrazí se okno konzoly jen na chvíli před jeho zavřením. K tomu `Main` dochází, protože metoda se ukončí po spuštění jediného příkazu, a proto aplikace skončí.

### <a name="add-some-code&quot;></a>Přidání kódu

Přidejme kód, který aplikaci pozastaví a potom požádá o uživatelský vstup.

1. Ihned po volání metody přidejte následující <xref:System.Console.WriteLine%2A> kód:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

    Program se pozastaví, dokud nestiskáte klávesu .

2. V řádku nabídek vyberte **Sestavit**  >  **řešení sestavení.**

   Tento kód zkompiluje program do převodní jazyka (IL), který je převeden na binární kód kompilátorem JIT (just-in-time).

## <a name="run-the-application"></a>Spuštění aplikace

1. Klikněte na **tlačítko HelloWorld** na panelu nástrojů.

   ![Kliknutím na Hello World tlačítko Pro spuštění programu z panelu nástrojů](../ide/media/vb-console-hello-world-button.png)

2. Stisknutím libovolné klávesy zavřete okno konzoly.

   ![Okno konzoly s Hello World a pokračovat stisknutím libovolné klávesy](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se trochu dozvěděli o Visual Basic a Visual Studio IDE. Další informace najdete v následujícím kurzu.

> [!div class="nextstepaction"]
> [Začínáme s Visual Basic v Visual Studio](../get-started/visual-basic/tutorial-console.md)
