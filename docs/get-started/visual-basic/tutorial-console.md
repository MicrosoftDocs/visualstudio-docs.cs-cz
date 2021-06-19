---
title: 'Kurz: Začínáme s Visual Basic'
description: Naučte se Visual Basic konzolové aplikace v Visual Studio krok za krokem.
ms.custom: vs-acquisition,  get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 8d34fef6251da95b6c3ac99430b87d853d4b5ba7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390708"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Kurz: Začínáme s Visual Basic v Visual Studio

V tomto kurzu pro Visual Basic (VB) použijete Visual Studio k vytvoření a spuštění několika různých konzolových aplikací a prozkoumáte některé funkce integrovaného vývojového prostředí [(IDE) Visual Studio.](visual-studio-ide.md)

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

Nejprve vytvoříme projekt Visual Basic aplikace. Typ projektu se dodává se všemi soubory šablony, které budete potřebovat, ještě než budete něco přidávat.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

3. V dialogovém **okně Nový** projekt v levém podokně rozbalte **Visual Basic** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Konzolová aplikace (.NET Core).** Pak projekt pojmnuje *WhatIsYourName*.

   ![Šablona projektu Konzolová aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém Visual Studio Ide](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Přidání úlohy (volitelné)

Pokud šablonu projektu Konzolová **aplikace (.NET Core)** nevidíte, můžete ji získat přidáním úlohy vývoj pro **různé platformy v .NET Core.** Tuto úlohu můžete přidat jedním ze dvou následujících způsobů v závislosti na tom, které aktualizace Visual Studio 2017 jsou nainstalované na vašem počítači.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: Použití dialogového okna Nový projekt

1. V **levém Instalační program pro Visual Studio** dialogového okna Nový projekt klikněte na **odkaz** Otevřít nový projekt.

   ![V dialogovém okně Instalační program pro Visual Studio projektu klikněte na odkaz Otevřít projekt.](../media/vs-open-visual-studio-installer-generic.png)

1. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**

   ![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: Použití řádku nabídek Nástroje

1. Zrušte dialogové **okno Nový** projekt a v horním řádku nabídek zvolte Nástroje **Získat** nástroje a > **funkce.**

1. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud tmavý motiv používáte, ale chcete, podívejte se na stránku Přizpůsobení integrovaného vývojového Visual Studio a [editoru,](../../ide/quickstart-personalize-the-ide.md) kde se dozvíte, jak.

1. Otevřete sadu Visual Studio.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

   ![Zobrazení okna Vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V **okně Vytvořit nový** projekt zvolte **Visual Basic** ze seznamu Jazyk. Dále v seznamu Platforma zvolte **Windows** a **ze** seznamu typů projektů zvolte Konzola.

   Po použití filtrů jazyka, platformy a typu projektu zvolte šablonu **Konzolová** aplikace a pak zvolte **Další.**

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Zvolte šablonu Visual Basic pro konzolovou aplikaci.":::

   > [!NOTE]
   > Pokud šablonu Konzolová **aplikace nevidíte,** můžete ji nainstalovat z **okna Vytvořit nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce.
   >
   > ![Odkaz Install more tools and features (Nainstalovat další nástroje a funkce) ze zprávy Not finding what you're looking for (Najít, co hledáte) v okně Create new project (Vytvořit nový projekt)](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Potom v části Instalační program pro Visual Studio úlohu **Vývoj pro různé platformy v .NET Core.**
   >
   > ![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Potom zvolte tlačítko **Upravit** v Instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce. Pokud ano, proveďte to. Potom zvolte **Pokračovat a** nainstalujte úlohu. Pak se vraťte ke kroku 2 v[této proceduře "Vytvoření](#create-a-project)projektu".

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole Project name (Název **projektu)** zadejte nebo zadejte *WhatIsYourName.* Pak zvolte **Další.**

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="V okně Konfigurovat nový projekt pojmnujte projekt WhatIsYourName.":::

1. V okně **Další informace** by už mělo být pro cílovou rozhraní vybrané **rozhraní .NET Core 3.1.** Pokud ne, vyberte **.NET Core 3.1.** Pak zvolte **Vytvořit.**

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="V okně Další informace se ujistěte, že je vybraná možnost .NET Core 3.1.":::

   Visual Studio nový projekt otevřete.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Vytvoření aplikace "What Is Your Name" (Jaké je vaše jméno)

Vytvoříme aplikaci, která vás vyzve k zadání vašeho jména a pak ji zobrazí spolu s datem a časem. Jak na to:

 ::: moniker range="vs-2017"

1. Pokud ještě není otevřený, otevřete projekt *WhatIsYourName.*

1. Zadejte následující kód Visual Basic za otevírací závorku, která následuje řádek `Sub Main(args As String())` a před řádek `End Sub` :

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Tento kód nahrazuje existující příkazy <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> , a <xref:System.Console.ReadKey%2A> .

   ![Okno kódu zobrazující kód What Is Your Name (Jaké je vaše jméno)](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Pomocí zeleného **tlačítka Start** nebo stisknutím **klávesy F5** sestavte a spusťte svou první aplikaci.

1. Po otevření okna konzoly zadejte své jméno. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

   ![Okno konzoly zobrazující What Is Your Name (Jaké je vaše jméno), datum a čas a stisknutím libovolné klávesy pokračujte ve zprávě](media/vb-console-what-name.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

::: moniker-end

::: moniker range=">=vs-2019"

1. V projektu *WhatIsYourName* zadejte následující kód Visual Basic za otevírací závorku, která následuje po řádku a před `Sub Main(args As String())` řádek `End Sub` :

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Tento kód nahrazuje existující příkazy <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> , a <xref:System.Console.ReadKey%2A> .

   ![Okno kódu zobrazující kód What Is Your Name (Jaké je vaše jméno)](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Pomocí zeleného **tlačítka Start** nebo stisknutím **klávesy F5** sestavte a spusťte svou první aplikaci.

1. Po otevření okna konzoly zadejte své jméno. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

   ![Okno konzoly zobrazující What Is Your Name (Jaké je vaše jméno), datum a čas a stisknutím libovolné klávesy pokračujte ve zprávě](media/vb-console-what-name.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Vytvoření aplikace Calculate This

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017 a pak v horním řádku nabídek zvolte File New Project **(Soubor** > **nový** > **projekt).**

1. V dialogovém **okně Nový** projekt v levém podokně rozbalte **Visual Basic** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Konzolová aplikace (.NET Core).** Pak soubor pojmechte *CalculateThis*.

1. Mezi řádek a řádek zadejte `Module Program` následující `End Module` kód:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Okno kódu by mělo vypadat jako na následujícím snímku obrazovky:

   ![Okno kódu s kódem CalculateThis](media/vb-codewindow-calculate-this.png)

1. Klikněte **na VypočítatTuto** a spusťte program. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující aplikaci CalculateThis, které obsahuje výzvy k tomu, které akce se mají provádět.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range=">=vs-2019"

1. V úvodním okně zvolte **Vytvořit nový projekt.** 

1. V **okně Vytvořit nový** projekt zvolte **Visual Basic** ze seznamu Jazyk. Dále v seznamu Platforma zvolte **Windows** a **ze** seznamu typů projektů zvolte Konzola.

1. Po použití filtrů jazyka, platformy a typu projektu zvolte šablonu **Konzolová** aplikace a pak zvolte **Další.**

   Potom v okně **Configure your new project** (Konfigurace nového projektu) zadejte nebo zadejte *CalculateThis* do **pole Project name (Název** projektu). Pak zvolte **Další.**

1. V okně **Další informace** by už mělo být pro cílovou rozhraní vybrané **rozhraní .NET Core 3.1.** Pokud ne, vyberte **.NET Core 3.1.** Pak zvolte **Vytvořit.**

1. Mezi řádek a řádek zadejte `Module Program` následující `End Module` kód:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Okno kódu by mělo vypadat jako na následujícím snímku obrazovky:

   ![Okno kódu s kódem CalculateThis](media/vb-codewindow-calculate-this.png)

1. Klikněte **na VypočítatTuto** a spusťte program. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

    ![V okně konzoly se zobrazuje aplikace CalculateThis, která obsahuje výzvy, které akce provést.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Rychlé odpovědi – Nejčastější dotazy

Tady je rychlý přehled nejčastějších dotazů, které vám pomůžeme zvýraznit některé klíčové koncepty.

### <a name="what-is-visual-basic"></a>Co je Visual Basic?

Visual Basic je typově bezpečný programovací jazyk, který je navržený tak, aby se snadno dozvěděl. Je odvozen od BASIC, což znamená "začátečník kód" na "začátečník".

### <a name="what-is-visual-studio"></a>Co je Visual Studio?

Visual Studio je integrovaná vývojová sada nástrojů pro produktivitu pro vývojáře. Představte si ho jako program, který můžete použít k vytvoření programů a aplikací.

### <a name="what-is-a-console-app"></a>Co je Konzolová aplikace?

Konzolová aplikace přebírá vstup a zobrazuje výstup v okně příkazového řádku, označované také jako konzola.

### <a name="what-is-net-core"></a>Co je .NET Core?

.NET Core je vývojovým dalším krokem .NET Framework. Pokud .NET Framework umožňují sdílet kód mezi programovacími jazyky, .NET Core přidá možnost sdílení kódu napříč platformami. Ještě lepší, jedná se o open source. (.NET Framework i .NET Core zahrnují knihovny předem sestavených funkcí i modul CLR (Common Language Runtime), který funguje jako virtuální počítač, ve kterém se má váš kód spustit.)

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Další informace najdete v následujícím kurzu.

> [!div class="nextstepaction"]
> [Sestavení knihovny pomocí Visual Basic a .NET Core SDK v aplikaci Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Viz také

* [Názorné postupy Visual Basic jazyka](/dotnet/visual-basic/walkthroughs)
* [Referenční dokumentace jazyka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense pro Visual Basic soubory kódu](../../ide/visual-basic-specific-intellisense.md)
