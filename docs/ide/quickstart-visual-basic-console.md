---
title: Vytvořte svou první konzolovou aplikaci pomocí Visual Basic
description: Naučte se, jak vytvořit jednoduchou konzolovou aplikaci Hello World v aplikaci Visual Studio s Visual Basic, krok za krokem.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 24e34bbd72810932f385d53a25ca1670fa059c1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939926"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Rychlý Start: Vytvoření první konzolové aplikace v aplikaci Visual Studio pomocí Visual Basic

V této 5-10 minut Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou Visual Basic aplikaci, která se spouští v konzole nástroje.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace Visual Basic. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual Basic** a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)**. Pak pojmenujte projekt *Hello*.

   ![Šablona projektu Konzolová aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** .

   ![Klikněte na odkaz otevřít Instalační program pro Visual Studio v dialogovém okně Nový projekt.](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

     ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Některé snímky obrazovky v tomto rychlém startu používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, přečtěte si téma [přizpůsobení stránky IDE a editoru sady Visual Studio](quickstart-personalize-the-ide.md) , kde se dozvíte, jak.

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly (.NET Core)** a pak zvolte možnost **Další**.

   ![Zvolit šablonu Visual Basic pro konzolovou aplikaci (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **Konzolová aplikace (.NET Core)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .
   >
   > ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *WhatIsYourName* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte projekt ' WhatIsYourName '.](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu Visual Basic a pojmenování projektu vytvoří Visual Studio jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine%2A> metodu pro zobrazení řetězcového literálu "Hello World!" v okně konzoly.

![Zobrazit výchozí kód Hello World ze šablony](../ide/media/vb-console-helloworld-template.png)

Pokud kliknete na tlačítko **HelloWorld** v integrovaném vývojovém prostředí, můžete spustit program v režimu ladění.

  ![Kliknutím na tlačítko Hello World spustíte program v režimu ladění.](../ide/media/vb-console-hello-world-button.png)

Když to uděláte, okno konzoly bude viditelné pouze chvilku před jeho zavřením. K tomu dochází `Main` , protože metoda se ukončí po provedení samostatného příkazu a aplikace skončí.

### <a name="add-some-code"></a>Přidat kód

Pojďme přidat nějaký kód pro pozastavení aplikace a pak požádat o vstup uživatele.

1. Přidejte následující kód hned za volání <xref:System.Console.WriteLine%2A> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Tím se program pozastaví, dokud nestisknete klávesu.

2. Na řádku nabídek vyberte **sestavení**  >  **sestavení**.

   Tím se program zkompiluje do mezilehlého jazyka (IL), který je převeden do binárního kódu pomocí kompilátoru JIT (just-in-time).

## <a name="run-the-application"></a>Spuštění aplikace

1. Klikněte na tlačítko **HelloWorld** na panelu nástrojů.

   ![Kliknutím na tlačítko Hello World spustíte program z panelu nástrojů.](../ide/media/vb-console-hello-world-button.png)

2. Stisknutím libovolné klávesy zavřete okno konzoly.

   ![Okno konzoly zobrazující Hello World a pokračujte stisknutím libovolné klávesy](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli trochu o Visual Basic a integrovaném vývojovém prostředí sady Visual Studio. Pokud se chcete dozvědět víc, pokračujte v následujícím kurzu.

> [!div class="nextstepaction"]
> [Začínáme s Visual Basic v aplikaci Visual Studio](../get-started/visual-basic/tutorial-console.md)
