---
title: 'Kurz: Začínáme s Visual Basic'
description: Naučte se vytvářet Visual Basic konzolové aplikace v aplikaci Visual Studio, krok za krokem.
ms.custom: seodec18, get-started
ms.date: 09/11/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 684cd4762eed38d947d76655bd9632fc10d0aacd
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829996"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Kurz: Začínáme s Visual Basic v aplikaci Visual Studio

V tomto kurzu pro Visual Basic (VB) použijete Visual Studio k vytvoření a spuštění několika různých konzolových aplikací a Prozkoumejte některé funkce [integrovaného vývojového prostředí (IDE) sady Visual Studio](visual-studio-ide.md) .

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříme projekt aplikace Visual Basic. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual Basic**a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)** . Pak pojmenujte projekt *WhatIsYourName*.

   ![Šablona projektu Konzolová aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Přidat úlohu (volitelné)

Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , můžete ji získat přidáním úlohy **vývoje .NET Core pro různé platformy** . Tuto úlohu můžete přidat jedním ze dvou způsobů, v závislosti na tom, které aktualizace sady Visual Studio 2017 jsou nainstalovány na vašem počítači.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: použití dialogového okna Nový projekt

1. Klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** .

   ![Klikněte na odkaz otevřít Instalační program pro Visual Studio v dialogovém okně Nový projekt.](../media/vs-open-visual-studio-installer-generic.png)

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

   ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: použití panelu nabídky nástroje

1. Zrušte výběr dialogového okna **Nový projekt** a v horním řádku nabídky vyberte **nástroje** > **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Některé snímky obrazovky v tomto kurzu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chtěli, najdete v článku [přizpůsobit IDE sady Visual Studio a Editor](../../ide/quickstart-personalize-the-ide.md) stránku a zjistěte, jak.

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly (.NET Core)** a pak zvolte možnost **Další**.

   ![Zvolit šablonu Visual Basic pro konzolovou aplikaci (.NET Framework)](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **Konzolová aplikace (.NET Core)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .
   >
   > ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *WhatIsYourName* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte projekt ' WhatIsYourName '.](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Vytvoření aplikace "Co je vaše jméno"

Pojďme vytvořit aplikaci, která vás vyzve k zadání vašeho jména a zobrazí se spolu s datem a časem. Tady je postup:

 ::: moniker range="vs-2017"

1. Pokud ještě není otevřený, otevřete projekt *WhatIsYourName* .

1. Zadejte následující kód Visual Basic hned za levou hranatou závorku, která následuje `Sub Main(args As String())` čára a před `End Sub` řádek:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Tento kód nahrazuje stávající příkazy <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>a <xref:System.Console.ReadKey%2A>.

   ![Okno Code zobrazující, jaký je váš kód vašeho názvu](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Použijte zelené tlačítko **Start** nebo stiskněte klávesu **F5** a sestavte a spusťte svoji první aplikaci.

1. Po otevření okna konzoly zadejte své jméno. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

   ![Okno konzoly ukazující vaše jméno, datum a čas a stisknutí libovolné klávesy pro pokračování zprávy](media/vb-console-what-name.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

::: moniker-end

::: moniker range="vs-2019"

1. V projektu *WhatIsYourName* zadejte následující kód Visual Basic hned za levou hranatou závorku, která následuje `Sub Main(args As String())` čára a před `End Sub` řádek:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Tento kód nahrazuje stávající příkazy <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>a <xref:System.Console.ReadKey%2A>.

   ![Okno Code zobrazující, jaký je váš kód vašeho názvu](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Použijte zelené tlačítko **Start** nebo stiskněte klávesu **F5** a sestavte a spusťte svoji první aplikaci.

1. Po otevření okna konzoly zadejte své jméno. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

   ![Okno konzoly ukazující vaše jméno, datum a čas a stisknutí libovolné klávesy pro pokračování zprávy](media/vb-console-what-name.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Vytvoření aplikace "vypočítat tuto aplikaci"

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017 a potom v horním panelu nabídek zvolte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual Basic**a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)** . Pak název souboru *CalculateThis*.

1. Zadejte následující kód mezi `Module Program`ovou čárou a `End Module` řádek:

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

   Okno Code by mělo vypadat jako na následujícím snímku obrazovky:

   ![Okno Code zobrazující kód CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknutím na **CalculateThis** spustíte program. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

    ![V okně konzoly se zobrazuje aplikace CalculateThis, která obsahuje výzvy, které akce provést.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**. 

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **Windows** . 

1. Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly (.NET Core)** a pak zvolte možnost **Další**.

   Pak v okně **Konfigurovat nový projekt** zadejte nebo zadejte *CalculateThis* do pole **název projektu** . Pak vyberte **vytvořit**.

1. Zadejte následující kód mezi `Module Program`ovou čárou a `End Module` řádek:

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

   Okno Code by mělo vypadat jako na následujícím snímku obrazovky:

   ![Okno Code zobrazující kód CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknutím na **CalculateThis** spustíte program. Okno konzoly by mělo vypadat podobně jako na následujícím snímku obrazovky:

    ![V okně konzoly se zobrazuje aplikace CalculateThis, která obsahuje výzvy, které akce provést.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Rychlé odpovědi – Nejčastější dotazy

Tady je rychlý přehled nejčastějších dotazů, které vám pomůžeme zvýraznit některé klíčové koncepty.

### <a name="what-is-visual-basic"></a>Co je Visual Basic?

Visual Basic je typově bezpečný programovací jazyk, který je navržený tak, aby se snadno dozvěděl. Je odvozen od BASIC, což znamená "začátečník kód" na "začátečník".

### <a name="what-is-visual-studio"></a>Co je Visual Studio?

Visual Studio je integrovaná vývojová sada nástrojů pro produktivitu pro vývojáře. Představte si ho jako program, který můžete použít k vytvoření programů a aplikací.

### <a name="what-is-a-console-app"></a>Co je Konzolová aplikace?

Konzolová aplikace přebírá vstup a zobrazuje výstup v okně příkazového řádku, a to také. Konzola.

### <a name="what-is-net-core"></a>Co je .NET Core?

.NET Core je vývojovým dalším krokem .NET Framework. Pokud .NET Framework umožňují sdílet kód mezi programovacími jazyky, .NET Core přidá možnost sdílení kódu napříč platformami. Ještě lepší, jedná se o open source. (.NET Framework i .NET Core zahrnují knihovny předem sestavených funkcí i modul CLR (Common Language Runtime), který funguje jako virtuální počítač, ve kterém se má váš kód spustit.)

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Další informace najdete v následujícím kurzu.

> [!div class="nextstepaction"]
> [Sestavení knihovny pomocí Visual Basic a .NET Core SDK v aplikaci Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Viz také:

* [Názorné postupy Visual Basic jazyka](/dotnet/visual-basic/walkthroughs)
* [Reference jazyka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense pro Visual Basic soubory kódu](../../ide/visual-basic-specific-intellisense.md)
