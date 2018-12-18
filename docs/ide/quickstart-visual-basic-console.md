---
title: Vytvořte svoji první aplikaci konzoly pomocí jazyka Visual Basic
description: Zjistěte, jak vytvořit jednoduchou konzolovou aplikaci Hello World v sadě Visual Studio pomocí jazyka Visual Basic, krok za krokem.
ms.date: 12/10/2017
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.technology: vs-acquisition
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 67a990b98b385cacab89bfa8270d8409f9e9aa5f
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159604"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Rychlý start: Vytvoření první aplikace konzoly v sadě Visual Studio pomocí jazyka Visual Basic

V tomto úvodu 5 až 10 minut do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou aplikaci Visual Basic, která běží na konzole.

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace Visual Basic. Typ projektu obsahuje všechny soubory šablon, které potřebujete, než jste přidali ještě nic!

1. Otevřete Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V **nový projekt** dialogové okno v levém podokně rozbalte **jazyka Visual Basic**a klikněte na tlačítko **.NET Core**. V prostředním podokně vyberte **Konzolová aplikace (.NET Core)**. Zadejte název projektu *HelloWorld*.

   ![Konzole šablonu projektu aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Pokud se nezobrazí **Konzolová aplikace (.NET Core)** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno.

   ![Klikněte na odkaz otevřít instalační program Visual Studio z dialogového okna Nový projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Spustí se instalační program pro Visual Studio. Zvolte **vývoj pro různé platformy .NET Core** úlohy a klikněte na tlačítko **změnit**.

     ![Úlohy pro vývoj pro různé platformy .NET core v instalačním programu sady Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu jazyka Visual Basic a pojmenujte svůj projekt, Visual Studio vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine%2A> metodu pro zobrazení řetězcový literál "Hello World!" v okně konzoly.

![Zobrazení kódu Hello World výchozí ze šablony](../ide/media/vb-console-helloworld-template.png)

Pokud kliknete **HelloWorld** tlačítko v integrovaném vývojovém prostředí, můžete program spustit v režimu ladění.

  ![Klikněte na tlačítko Hello World a spusťte program v režimu ladění](../ide/media/vb-console-hello-world-button.png)

Když toto provedete, v okně konzoly je viditelné jenom na chvíli předtím, než se toto okno zavře. Proto, `Main` metoda ukončí po jeho jediném příkazu, takže aplikace se ukončí.

### <a name="add-some-code"></a>Přidání kódu

Přidejme nějaký kód pozastavení aplikace a poté požádat pro uživatelský vstup.

1. Přidejte následující kód bezprostředně po volání <xref:System.Console.WriteLine%2A> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Program to pozastaví, dokud stisknutím jakékoli klávesy.

2. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.

   Tento program zkompiluje do intermediate language (IL), která se převádí do binárního kódu, kompilátor just-in-time (JIT).

## <a name="run-the-application"></a>Spuštění aplikace

1. Klikněte na tlačítko **HelloWorld** tlačítko na panelu nástrojů.

   ![Klikněte na tlačítko Hello World a má program spustit z panelu nástrojů](../ide/media/vb-console-hello-world-button.png)

2. Stisknutím jakékoli klávesy zavřete okno konzoly.

   ![Okno Hello World konzoly a stisknutím libovolné klávesy pokračovat](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli ještě něco o jazyce Visual Basic a Visual Studio IDE. Další informace najdete dál v následujícím kurzu.

> [!div class="nextstepaction"]
> [Začínáme s jazykem Visual Basic v sadě Visual Studio](tutorial-visual-basic-console.md)
