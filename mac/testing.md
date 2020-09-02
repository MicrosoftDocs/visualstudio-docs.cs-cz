---
title: Nástroje pro Visual Studio pro Mac testování
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: acf34677e8d9b477512763be3c43bb9df0c53c46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88200976"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Testovací nástroje v Visual Studio pro Mac

Visual Studio pro Mac testovací nástroje vám pomůžou a váš tým vyvíjejí a udržuje vysoké standardy kvality kódu. Testování částí lze zapsat a spustit pomocí rozhraní Microsoft Unit Test Framework (MSTest), xUnit nebo NUnit.

## <a name="creating-tests"></a>Vytváření testů
Chcete-li začít s testováním, můžete vytvořit nový projekt testu ve vašem řešení kliknutím pravým tlačítkem myši na řešení a zvolením nabídky **přidat > nový projekt...** . Pak zvolte jednu z kategorií testu na levé straně dialogového okna (například kategorie **web a konzola > testy** ). Vyberte typ testovacího projektu, který chcete vytvořit, a klikněte na tlačítko Další. Postupujte podle pokynů v dialogových oknech a potom se do vašeho řešení přidá nový testovací projekt.

![Dialog Nový projekt s vybraným oddílem webové a konzolové > testy zobrazující projekty xUnit, MSTest a NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Další informace o testování částí aplikací .NET Core a výběru rozhraní pro testování částí naleznete v tématu [testování částí v rozhraní .NET Core a v dokumentaci .NET Standard](https://docs.microsoft.com/dotnet/core/testing/?pivots=xunit) .

## <a name="running-tests"></a>Spouštění testů
Okno **testy jednotek** se používá ke spouštění testů jednotek a je otevřeno pomocí nabídky **zobrazit > panelu > testy jednotek** . Testy jednotek v řešení se automaticky zjišťují a zobrazují v tomto okně, kde můžete spustit všechny testy nebo sadu testů, které jste vybrali.

![Testovací okno znázorňující seznam testů jednotek a panel nástrojů pro spouštění nebo zastavování testů.](media/test-window.PNG)

Při úpravách třídy jazyka C#, která obsahuje testy jednotek, můžete spustit testy kliknutím pravým tlačítkem na testovací třídu nebo testovací metodou a výběrem nabídky **Spustit testy** nebo **zkušebního ladění** . Výběr položky nabídky pro **spuštění** testů spustí testy v testovacím okně. výběr nabídky **zkušebních testů (ů)** bude stejný a připojí ladicí program, abyste mohli řešit potíže s kódem.

![Editor v nabídce klikněte pravým tlačítkem na možnosti Spustit a ladit testy](media/run-tests-context-menu.PNG)

Pokud jsou testy spuštěny, zobrazí se okno **výsledky testů** , abyste mohli zkontrolovat úspěšné nebo neúspěšné testy a výstup spuštění těchto testů.

![Okno výsledky testu znázorňující jeden neúspěšný test a počet 21 úspěšných testů a 1 neúspěšný test.](media/test-results-window.PNG)

## <a name="see-also"></a>Viz také

- [Testování částí v .NET Core a .NET Standard](/dotnet/core/testing)
- [Začínáme s testováním částí (Visual Studio ve Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Základy testování částí (Visual Studio ve Windows)](/visualstudio/test/unit-test-basics)
