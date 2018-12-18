---
title: Začínáme s testováním částí
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e8835edb2b340778c4431d3de5b554d6aeb6c6d
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158811"
---
# <a name="get-started-with-unit-testing"></a>Začínáme s testováním částí

Pomocí sady Visual Studio můžete definovat a spouštět testy jednotek Údržba kódu stavu, ujistěte se, pokrytí kódu a najít chyby a závad, než se vaši zákazníci.

## <a name="create-unit-tests"></a>Vytvořit testy jednotek

Vytvořit testy jednotek a spouštět je často abyste měli jistotu, že váš kód funguje správně.

1. Vytvořte projekt testu jednotek.

   ![Přidejte do svého řešení projekt testu jednotek](media/createunittest1.png)

1. Pojmenujte svůj projekt.

   ![Šablona projektu pro test jednotek](media/createunittest2.png)

   Projekt je přidán do řešení.

   ![Projekt testu jednotek v Průzkumníku řešení](media/createunittest5.png)

1. V projektu testování částí přidejte odkaz na projekt, který chcete testovat.

   ![Přidání odkazu do projektu jednotkového testu](media/createunittest6.png)

1. Vyberte projekt, který obsahuje kód, který budete testovat.

   ![Vyberte odkaz na přidání](media/createunittest7.png)

1. Kód pro testování částí.

   ![Přidejte kód pro testování částí](media/createunittest8.png)

Můžete také vytvořit test jednotky metoda zástupné procedury s **vytvořit testy jednotek** [příkaz](create-unit-tests-menu.md).

![Pomocí příkazu Vytvořit testy jednotek](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Spouštění testů jednotek

1. Otevřít **Průzkumník testů**.

   ![V nabídce Test otevřete Průzkumníka testů](media/rununittest1.png)

1. Spouštění testů jednotek.

   ![Spouštění testování částí v Průzkumníku testů](media/rununittest2.png)

   Můžete zobrazit, která úspěšný nebo neúspěšný v testování částí **Průzkumník testů**.

   ![Zkontrolujte výsledky testování částí v Průzkumníku testů](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>Zobrazení výsledků testu jednotek

Pokud používáte MSTest, xUnit a NUnit testovací rozhraní v sadě Visual Studio 2017 nebo později, zobrazí se živé výsledků testování částí.

> [!NOTE]
> Živé testování částí je pouze k dispozici v aplikaci Visual Studio 2017 Enterprise Edition.

1. Zapnout z testování jednotek **Test** nabídky.

   ![Zapnout živé testování částí](media/live-test-results-start.png)

1. Zobrazte výsledky testů v rámci okna editoru kódu během psaní a úpravy kódu.

   ![Zobrazit výsledky testů](media/live-test-results-ui.png)

1. Vyberte test výsledek ukazatelů pro zobrazení dalších informací.

   ![Vyberte test výsledek ukazatelů](media/live-test-results-details.png)

Další podrobnosti najdete v tématu [živé testování částí](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generování testů jednotek pomocí funkce IntelliTest

Při spuštění IntelliTest můžete snadno zobrazit, jaké testy se nedaří a přidejte všechny nezbytné kód a opravte je. Můžete vybrat, které z vygenerované testy k uložení do testovacího projektu poskytnout sadu regrese. Po provedení změny kódu, znovu spusťte IntelliTest pro synchronizaci vygenerované testy se změnami kódu. Další informace o postupu [generování testů jednotek pro kód pomocí funkce IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generování testů jednotek pomocí funkce IntelliTest](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů jednotek pomocí Průzkumníka testů

Použití **Průzkumníka testů** spouštění testů jednotek sady Visual Studio nebo projektů testování jednotky třetí strany, seskupte testy do kategorií, filtrovat seznam testů a vytvořit, uložit, a spusťte seznamy stop testů. Můžete také ladit testy a analyzovat pokrytí testu výkonu a kódu. Další informace o postupu [spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md).

![Provádění testů jednotek pomocí Průzkumníka testů](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Určení rozsahu testovaného kódu pomocí pokrytí kódu

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Pro efektivní ochranu před chybami, vaše testy měly využít velká část kódu. Další informace o postupu [použití pokrytí kódu k určení, kolik kódu je právě testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-different-unit-test-framework"></a>Používat různé testování částí

Můžete spustit testy jednotek v sadě Visual Studio s použitím rozhraní testování třetích stran, jako jsou Boost, Google a NUnit. Používání tak, že Visual Studio test runner můžete pracovat s tímto rozhraním pro rozhraní modulu plug-in.

Postup povolení rozhraní pro testování třetích stran jsou následující:

1. Zvolte **nástroje** > **rozšíření a aktualizace** z řádku nabídek.

1. V **rozšíření a aktualizace** dialogového okna rozbalte **Online** kategorie a potom **Visual Studio Marketplace**. Potom kliknutím na možnost **nástroje** > **testování**.

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. Vyberte rozhraní framework nebo adaptér, kterou chcete nainstalovat a klikněte na tlačítko **Stáhnout**.

1. Vytvořte projekt knihovny tříd a přidejte do svého řešení.

   ![Pojmenujte projekt knihovny tříd a přidejte ji](media/create3rdpartyunittest3.png)

1. Instalace modulu plug-in. V **Průzkumníka řešení**, vyberte projekt knihovny tříd a pak zvolte **spravovat balíčky NuGet** její nabídce klepněte pravým tlačítkem myši nebo kontext.

   ![Správa balíčků NuGet nainstalujte modul plug-in](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) je rozšíření sady Visual Studio, můžete přidávat a aktualizovat knihovny a nástroje pro vaše projekty.

1. V **Správce balíčků NuGet** vyhledejte a vyberte modul plug-in a klikněte na tlačítko **nainstalovat**.

   ![Nainstalujte rozhraní framework 3rd třetích stran](media/create3rdpartyunittest4.png)

   Rozhraní je odkazováno v projektu.

   ![Referenční dokumentace pro rozhraní pro testování částí od 3. stran se přidá do vašeho řešení](media/create3rdpartyunittest6.png)

1. Z projektu knihovny tříd **odkazy** uzlu, vyberte **přidat odkaz**.

   ![Přidejte odkaz na projekt](media/createunittest6.png)

1. V **správce odkazů** dialogového okna, vyberte projekt, který obsahuje kód, který budete testovat.

   ![Vyberte projekt kódu k otestování](media/createunittest7.png)

1. Kód pro testování částí.

   ![Přidejte kód do souboru kódu jednotkového testu](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>Viz také:

* [Vytvoření příkazu pro testování částí](create-unit-tests-menu.md)
* [Generování testů s Intellitestem](generate-unit-tests-for-your-code-with-intellitest.md)
* [Spouštění testů pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md)
* [Určení pokrytí kódu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Zlepšení kvality kódu](improve-code-quality.md)