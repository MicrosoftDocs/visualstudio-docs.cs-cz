---
title: Vytvoření první konzolové aplikace C# pomocí Visual Studia
titleSuffix: ''
description: Přečtěte si, jak vytvořit jednoduchou konzolovou aplikaci Hello World v sadě Visual Studio s c#, krok za krokem.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 20b2cf2bf12e9b24ca12d0a73b43e4a56e8246f4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579488"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Úvodní příručka: Vytvoření první konzolové aplikace C# pomocí Sady Visual Studio

V tomto 5-10 minut úvod do integrovaného vývojového prostředí Visual Studio (IDE), vytvoříte jednoduchou aplikaci C#, která běží na konzoli.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace C#. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat, ještě předtím, než něco přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku C#** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Console App (.NET Core)**. Pak pojmenujte projekt *HelloWorld*.

   ![Šablona projektu konzolové aplikace (.NET Core) v dialogovém okně Nový projekt v ide sady Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Pokud šablonu projektu **Console App (.NET Core)** nevidíte, zvolte odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt.**

   ![Zvolte odkaz Otevřít instalační program sady Visual Studio v dialogovém okně Nový projekt.](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

     ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **C#** ze seznamu jazyk a pak zvolte **Windows** ze seznamu platformy. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Console App (.NET Core)** a pak zvolte **Další**.

   ![Zvolte šablonu Jazyka C# pro konzolovou aplikaci (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud šablonu **Console App (.NET Core)** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Potom v Instalační službě sady Visual Studio zvolte vývojové úlohy **.NET Core napříč platformami.**
   >
   > ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt HelloWorld](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio otevře nový projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

::: moniker range="vs-2017"

Po výběru šablony projektu C# a pojmenování projektu, Visual Studio vytvoří jednoduchou aplikaci "Hello World" pro vás.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio obsahuje výchozí kód "Hello World" v projektu.

::: moniker-end

(Chcete-li tak učinit, volá metodu <xref:System.Console.WriteLine%2A> pro zobrazení literálu řetězec "Hello World!" v okně konzoly.)

   ![Zobrazit výchozí kód Hello World ze šablony](../ide/media/csharp-console-helloworld-template.png)

Pokud stisknete **klávesu F5**, můžete program spustit v režimu ladění. Okno konzoly je však viditelné pouze na chvíli před zavřením.

(Toto chování `Main` se stane, protože metoda ukončí po jeho jeden příkaz spustí, a tak aplikace končí.)

### <a name="add-some-code"></a>Přidání nějakého kódu

Přidáme nějaký kód pro pozastavení aplikace tak, aby se okno konzoly nezavřelo, dokud nestisknete **klávesu ENTER**.

1. Přidejte následující kód ihned <xref:System.Console.WriteLine%2A> po volání metody:

   ```csharp
   Console.ReadLine();
   ```

1. Ověřte, zda vypadá takto v editoru kódu:

   ![Přidání kódu pro pozastavení aplikace Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Chcete-li spustit aplikaci v režimu ladění, zvolte tlačítko **HelloWorld** na panelu nástrojů. (Nebo můžete stisknout **klávesu F5**.)

   ![Zvolte tlačítko Hello World pro spuštění aplikace z panelu nástrojů](../ide/media/csharp-console-hello-world-button.png)

1. Zobrazení aplikace v okně konzole.

   ![Okno konzole zobrazující Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Zavření aplikace

1. Stisknutím **klávesy ENTER** zavřete okno konzoly.

1. Zavřete podokno **Výstup** v sadě Visual Studio.

   ![Zavření podokna Výstup v sadě Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zavřete Visual Studio.

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli něco o Jazyce C# a IDE sady Visual Studio. Další informace najdete v následujících kurzech.

> [!div class="nextstepaction"]
> [Začínáme s konzolovou aplikací C# ve Visual Studiu](../get-started/csharp/tutorial-console.md)
