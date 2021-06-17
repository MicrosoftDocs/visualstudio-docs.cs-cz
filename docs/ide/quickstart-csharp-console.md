---
title: Vytvoření první konzolové aplikace v jazyce C# pomocí sady Visual Studio
titleSuffix: ''
description: Naučte se, jak vytvořit jednoduchou konzolovou aplikaci Hello World v aplikaci Visual Studio pomocí jazyka C#, krok za krokem.
ms.custom: acquisition, seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 31759f3ae6359c9e366157012f6321c62085f8f9
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113218"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Rychlý Start: použití sady Visual Studio k vytvoření první konzolové aplikace v jazyce C#

V této 5-10 minutové seznámení s integrovaným vývojovým prostředím (IDE) sady Visual Studio vytvoříte jednoduchou aplikaci v jazyce C#, která bude spuštěna v konzole nástroje.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace v jazyce C#. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **C#** a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)**. Pak pojmenujte projekt *Hello*.

   ![Šablona projektu Konzolová aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , vyberte odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** .

   ![Vyberte odkaz otevřít Instalační program pro Visual Studio z dialogového okna Nový projekt.](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

     ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Potom v seznamu jazyk vyberte **C#** a pak v seznamu platforma zvolte **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly (.NET Core)** a pak zvolte možnost **Další**.

   ![Zvolit šablonu C# pro konzolovou aplikaci (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **Konzolová aplikace (.NET Core)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .
   >
   > ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte svůj projekt HelloWorld.](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio otevře nový projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

::: moniker range="vs-2017"

Po výběru šablony projektu C# a pojmenování projektu vytvoří Visual Studio jednoduchou aplikaci "Hello World".

::: moniker-end

::: moniker range="vs-2019"

Visual Studio obsahuje výchozí kód "Hello World" v projektu.

::: moniker-end

(K tomu je volána <xref:System.Console.WriteLine%2A> metoda pro zobrazení řetězcového literálu "Hello World!" v okně konzoly.)

   ![Zobrazit výchozí kód Hello World ze šablony](../ide/media/csharp-console-helloworld-template.png)

Pokud stisknete klávesu **F5**, můžete spustit program v režimu ladění. Okno konzoly je však viditelné pouze v okamžiku před jeho zavřením.

(K tomuto chování dochází `Main` , protože metoda se ukončí po provedení jednoho příkazu, a proto aplikace skončí.)

### <a name="add-some-code"></a>Přidat kód

Pojďme přidat nějaký kód pro pozastavení aplikace, aby okno konzoly nebylo ukončeno, dokud nestisknete klávesu **ENTER**.

1. Přidejte následující kód hned za volání <xref:System.Console.WriteLine%2A> metody:

   ```csharp
   Console.ReadLine();
   ```

1. Ověřte, že v editoru kódu vypadá takto:

   ![Přidání kódu pro pozastavení aplikace Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Kliknutím na tlačítko **HelloWorld** na panelu nástrojů spusťte aplikaci v režimu ladění. (Nebo, můžete stisknout klávesu **F5**.)

   ![Kliknutím na tlačítko Hello World spustíte aplikaci z panelu nástrojů.](../ide/media/csharp-console-hello-world-button.png)

1. Zobrazte svou aplikaci v okně konzoly.

   ![Okno konzoly zobrazující Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Zavřít aplikaci

1. Stisknutím klávesy **ENTER** zavřete okno konzoly.

1. Zavřete podokno **výstup** v aplikaci Visual Studio.

   ![Zavření podokna výstup v aplikaci Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zavřete Visual Studio.

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli trochu o jazyce C# a integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v následujících kurzech.

> [!div class="nextstepaction"]
> [Začínáme s konzolovou aplikací v jazyce C# v aplikaci Visual Studio](../get-started/csharp/tutorial-console.md)
