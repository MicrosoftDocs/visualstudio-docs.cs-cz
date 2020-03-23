---
title: 'Kurz: Začínáme s Visual Basicem'
description: Přečtěte si, jak vytvořit aplikace konzoly Visual Basic v sadě Visual Studio, krok za krokem.
ms.custom: seodec18, get-started
ms.date: 09/11/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 279bfb00a2466120d21c5c868c0987ec19202acc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579933"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Kurz: Začínáme s Visual Basicem v Sadě Visual Studio

V tomto kurzu pro Visual Basic (VB) použijete Visual Studio k vytvoření a spuštění několika různých konzolových aplikací a prozkoumání některých funkcí [integrovaného vývojového prostředí visual studia (IDE),](visual-studio-ide.md) zatímco to uděláte.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříme projekt aplikace jazyka Visual Basic. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat, ještě předtím, než něco přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Visual Basic**a pak zvolte **.NET Core**. V prostředním podokně zvolte **Console App (.NET Core)**. Pak pojmenujte projekt *WhatIsYourName*.

   ![Šablona projektu konzolové aplikace (.NET Core) v dialogovém okně Nový projekt v ide sady Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Přidání pracovního vytížení (volitelné)

Pokud nevidíte šablonu projektu **konzolové aplikace (.NET Core),** můžete ji získat přidáním **úlohy pro vývoj napříč platformami .NET Core.** Toto zatížení můžete přidat jedním ze dvou následujících způsobů, v závislosti na tom, které aktualizace Visual Studia 2017 jsou nainstalovány v počítači.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: Použití dialogového okna Nový projekt

1. Klepněte na odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt.**

   ![V dialogovém okně Nový projekt klepněte na odkaz Otevřít instalační program sady Visual Studio.](../media/vs-open-visual-studio-installer-generic.png)

1. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

   ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: Použití panelu nabídek Nástroje

1. Zrušit z dialogového okna **Nový projekt** a v horním řádku nabídek zvolte **Nástroje** > **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Některé screenshoty v tomto tutoriálu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, podívejte se na [stránku Přizpůsobit ide a editor u visual ateliéru,](../../ide/quickstart-personalize-the-ide.md) kde se dozvíte, jak na to.

1. Otevřete Visual Studio 2019.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **Visual Basic** ze seznamu Jazyk a pak zvolte **Windows** ze seznamu Platform. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Console App (.NET Core)** a pak zvolte **Další**.

   ![Volba šablony jazyka Visual Basic pro konzolovou aplikaci (.NET Framework)](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud šablonu **Console App (.NET Core)** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Potom v Instalační službě sady Visual Studio zvolte vývojové úlohy **.NET Core napříč platformami.**
   >
   > ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *whatisyourname* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt WhatIsYourName](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Vytvoření aplikace "Jaké je vaše jméno"

Vytvoříme aplikaci, která vás vyzve k zadání vašeho jména a zobrazí ji spolu s datem a časem. Zde je uveden postup:

 ::: moniker range="vs-2017"

1. Pokud ještě není otevřena, otevřete projekt *WhatIsYourName.*

1. Za dejte následující kód jazyka Visual Basic bezprostředně `Sub Main(args As String())` za otevírací `End Sub` závorku, která následuje za řádkem a před řádkem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Tento kód nahrazuje <xref:System.Console.WriteLine%2A>existující <xref:System.Console.Write%2A>příkazy , a <xref:System.Console.ReadKey%2A> příkazy.

   ![Okno Kód zobrazující kód What Is Your Name](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Použijte zelené tlačítko **Start** nebo stisknutím **klávesy F5** vytvořte a spusťte svou první aplikaci.

1. Po otevření okna konzoly zadejte své jméno. Okno konzole by mělo vypadat podobně jako na následujícím snímku obrazovky:

   ![Okno konzoly zobrazující datum, co je vaše jméno, čas a datum, a stisknutím libovolné klávesy pokračujte ve zprávě](media/vb-console-what-name.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

::: moniker-end

::: moniker range="vs-2019"

1. V projektu *WhatIsYourName* zadejte následující kód jazyka Visual Basic bezprostředně `Sub Main(args As String())` za počáteční `End Sub` závorku, která následuje za řádkem a před řádkem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Tento kód nahrazuje <xref:System.Console.WriteLine%2A>existující <xref:System.Console.Write%2A>příkazy , a <xref:System.Console.ReadKey%2A> příkazy.

   ![Okno Kód zobrazující kód What Is Your Name](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Použijte zelené tlačítko **Start** nebo stisknutím **klávesy F5** vytvořte a spusťte svou první aplikaci.

1. Po otevření okna konzoly zadejte své jméno. Okno konzole by mělo vypadat podobně jako na následujícím snímku obrazovky:

   ![Okno konzoly zobrazující datum, co je vaše jméno, čas a datum, a stisknutím libovolné klávesy pokračujte ve zprávě](media/vb-console-what-name.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Vytvoření aplikace "Vypočítat toto"

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017 a potom z horního řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Visual Basic**a pak zvolte **.NET Core**. V prostředním podokně zvolte **Console App (.NET Core)**. Potom pojmenujte soubor *CalculateThis*.

1. Mezi řádek a `Module Program` `End Module` řádek zadejte následující kód:

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

   Okno kódu by mělo vypadat jako následující snímek obrazovky:

   ![Okno kódu zobrazující kód CalculateThis](media/vb-codewindow-calculate-this.png)

1. Klepnutím na tlačítko **Vypočítat** spusťte program. Okno konzole by mělo vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující aplikaci CalculateThis, která obsahuje výzvy, které mají být akce podniknou.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. V počátečním okně zvolte **Vytvořit nový projekt**. 

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **Visual Basic** ze seznamu Jazyk a pak zvolte **Windows** ze seznamu Platform. 

1. Po použití filtrů jazyka a platformy zvolte šablonu **Console App (.NET Core)** a pak zvolte **Další**.

   Potom v okně **Konfigurovat nový projekt** zadejte nebo zadejte *CalculateThis* do pole **Název projektu.** Dále zvolte **Vytvořit**.

1. Mezi řádek a `Module Program` `End Module` řádek zadejte následující kód:

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

   Okno kódu by mělo vypadat jako následující snímek obrazovky:

   ![Okno kódu zobrazující kód CalculateThis](media/vb-codewindow-calculate-this.png)

1. Klepnutím na tlačítko **Vypočítat** spusťte program. Okno konzole by mělo vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující aplikaci CalculateThis, která obsahuje výzvy, které mají být akce podniknou.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Nejčastější dotazy týkající se rychlých odpovědí

Zde je rychlý FAQ upozornit na některé klíčové pojmy.

### <a name="what-is-visual-basic"></a>Co je visual basic?

Visual Basic je typově bezpečný programovací jazyk, který je navržen tak, aby se snadno naučil. Je odvozen od BASIC, což znamená "Začátečník je All-purpose symbolické instrukce kód".

### <a name="what-is-visual-studio"></a>Co je Visual Studio?

Visual Studio je integrovaná vývojová sada nástrojů pro zvýšení produktivity pro vývojáře. Přemýšlejte o tom jako o programu, který můžete použít k vytváření programů a aplikací.

### <a name="what-is-a-console-app"></a>Co je konzolová aplikace?

Konzolová aplikace přijímá vstup a zobrazuje výstup v okně příkazového řádku, aka konzoly.

### <a name="what-is-net-core"></a>Co je jádro .NET?

.NET Core je další evoluční krok rozhraní .NET Framework. Kde rozhraní .NET Framework umožňuje sdílet kód mezi programovacími jazyky, rozhraní .NET Core přidává možnost sdílet kód napříč platformami. Ještě lepší je, že je to open source. (Rozhraní .NET Framework i .NET Core zahrnují knihovny předem nastavených funkcí a také běžný jazyk ový runtime (CLR), který funguje jako virtuální počítač, ve kterém chcete spustit váš kód.)

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto výukového programu! Chcete-li se dozvědět ještě více, podívejte se na následující kurz.

> [!div class="nextstepaction"]
> [Vytvoření knihovny s visual basicem a sadou .NET Core SDK v sadě Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Viz také

* [Návody k jazyku jazyka Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Referenční dokumentace jazyka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Technologie IntelliSense pro soubory kódu jazyka Visual Basic](../../ide/visual-basic-specific-intellisense.md)
