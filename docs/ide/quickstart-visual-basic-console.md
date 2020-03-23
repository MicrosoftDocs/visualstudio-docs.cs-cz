---
title: Vytvoření první konzolové aplikace pomocí jazyka Visual Basic
description: Přečtěte si, jak vytvořit jednoduchou konzolovou aplikaci Hello World v Sadě Visual Studio s visual basicem krok za krokem.
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
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34f3dc8642e2cf8e965e2ad303bed79931d2645c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579494"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Úvodní příručka: Vytvoření první konzolové aplikace v Visual Studiu pomocí Jazyka Visual Basic

V tomto 5-10 minut úvod do integrovaného vývojového prostředí Sady Visual Studio (IDE), vytvoříte jednoduchou aplikaci jazyka, který běží na konzoli.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace jazyka Visual Basic. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat, ještě předtím, než něco přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Visual Basic**a pak zvolte **.NET Core**. V prostředním podokně zvolte **Console App (.NET Core)**. Pak pojmenujte projekt *HelloWorld*.

   ![Šablona projektu konzolové aplikace (.NET Core) v dialogovém okně Nový projekt v ide sady Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Pokud šablonu projektu **Console App (.NET Core)** nevidíte, klikněte v levém podokně dialogového okna **Nový projekt** na odkaz Otevřít instalační program **sady Visual Studio.**

   ![V dialogovém okně Nový projekt klepněte na odkaz Otevřít instalační program sady Visual Studio.](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

     ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Některé snímky obrazovky v tomto rychlém startu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, podívejte se na [stránku Přizpůsobit ide a editor u visual ateliéru,](quickstart-personalize-the-ide.md) kde se dozvíte, jak na to.

1. Otevřete Visual Studio 2019.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **Visual Basic** ze seznamu Jazyk a pak zvolte **Windows** ze seznamu Platform. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Console App (.NET Core)** a pak zvolte **Další**.

   ![Volba šablony jazyka Visual Basic pro konzolovou aplikaci (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud šablonu **Console App (.NET Core)** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Potom v Instalační službě sady Visual Studio zvolte vývojové úlohy **.NET Core napříč platformami.**
   >
   > ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *whatisyourname* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt WhatIsYourName](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu jazyka Visual Basic a pojmenování projektu, Visual Studio vytvoří jednoduchou aplikaci "Hello World" pro vás. Volá metodu <xref:System.Console.WriteLine%2A> pro zobrazení literálu řetězec "Hello World!" v okně konzoly.

![Zobrazit výchozí kód Hello World ze šablony](../ide/media/vb-console-helloworld-template.png)

Pokud klepnete na tlačítko **HelloWorld** v ide, můžete spustit program v režimu ladění.

  ![Kliknutím na tlačítko Hello World spustíte program v režimu ladění.](../ide/media/vb-console-hello-world-button.png)

Když toto uděláte, okno konzoly je viditelné pouze chvíli před zavřením. K tomu `Main` dochází, protože metoda ukončí po jeho jeden příkaz spustí a tak aplikace končí.

### <a name="add-some-code"></a>Přidání nějakého kódu

Přidáme nějaký kód pro pozastavení aplikace a pak požádat o vstup uživatele.

1. Přidejte následující kód ihned <xref:System.Console.WriteLine%2A> po volání metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Tím program pozastavíte, dokud nestisknete klávesu.

2. Na řádku nabídek vyberte **Build** > **Build Build Solution**.

   To zkompiluje váš program do zprostředkujícího jazyka (IL), který je převeden na binární kód kompilátorem just-in-time (JIT).

## <a name="run-the-application"></a>Spuštění aplikace

1. Klepněte na tlačítko **HelloWorld** na panelu nástrojů.

   ![Kliknutím na tlačítko Hello World spustíte program z panelu nástrojů.](../ide/media/vb-console-hello-world-button.png)

2. Stisknutím libovolné klávesy zavřete okno konzoly.

   ![Okno konzoly zobrazující Hello World a stisknutím libovolné klávesy pokračujte](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli něco o Visual Basic a Visual Studio IDE. Další informace najdete v následujícím kurzu.

> [!div class="nextstepaction"]
> [Začínáme s Visual Basicem v Sadě Visual Studio](../get-started/visual-basic/tutorial-console.md)
