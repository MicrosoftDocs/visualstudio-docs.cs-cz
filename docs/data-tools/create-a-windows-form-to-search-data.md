---
title: Vytvoření formuláře Windows k vyhledávání dat
description: Přečtěte si příklad vytvoření formuláře Windows Pro vyhledávání dat. Vytvořte aplikaci Windows Form, zdroj dat a formulář. Přidejte parametrizaci. Otestujete aplikaci.
ms.custom: SEO-VS-2020
ms.date: 06/07/2021
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2ce9d3eeebf42855ad69f02b2d72330190a2b390
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761092"
---
# <a name="create-a-windows-form-to-search-data"></a>Vytvoření formuláře Windows k vyhledávání dat

Běžným scénářem aplikace je zobrazení vybraných dat ve formuláři. Můžete například chtít zobrazit objednávky pro konkrétního zákazníka nebo podrobnosti o konkrétní objednávce. V tomto scénáři uživatel zadá informace do formuláře a pak se spustí dotaz se vstupem uživatele jako parametrem. To znamená, že data jsou vybrána na základě parametrizovaného dotazu. Dotaz vrátí pouze data, která splňují kritéria zadaná uživatelem. Tento názorný postup ukazuje, jak vytvořit dotaz, který vrátí zákazníky v určitém městě, a upravit uživatelské rozhraní tak, aby uživatelé mohli zadat název města a stisknout tlačítko pro provedení dotazu.

Použití parametrizovaných dotazů pomáhá zajistit efektivitu aplikace tím, že databázi umožňuje provádět nejlepší práci– rychle filtrovat záznamy. Naproti tomu pokud si vyžádáte celou databázovou tabulku, přenesete ji přes síť a pak pomocí aplikační logiky najdete záznamy, které chcete, může být vaše aplikace pomalá a neefektivní.

Parametrizované dotazy můžete přidat do libovolného objektu TableAdapter (a ovládacích prvků pro příjem hodnot parametrů a spuštění dotazu) pomocí **dialogového** okna Tvůrce kritérií vyhledávání. Výběrem příkazu Přidat  dotaz v nabídce **Data** (nebo jakékoli inteligentní značky TableAdapter) otevřete dialogové okno.

Mezi úlohy znázorněné v tomto názorném postupu patří:

- Vytvoření a konfigurace zdroje dat v aplikaci pomocí Průvodce konfigurací **zdroje** dat

- Nastavení typu přetažení položek v **okně Zdroje** dat

- Vytváření ovládacích prvků, které zobrazují data přetažením položek **z okna Zdroje** dat na formulář

- Přidání ovládacích prvků pro zobrazení dat ve formuláři

- Dokončení dialogového **okna Tvůrce** kritérií vyhledávání

- Zadání parametrů do formuláře a spuštění parametrizovaného dotazu.

> [!NOTE]
> Postupy v tomto článku se vztahují pouze .NET Framework model Windows Forms projekty, nikoli pro projekty .NET Core model Windows Forms projekty.

## <a name="prerequisites"></a>Požadavky

Musíte mít **nainstalovanou úlohu Ukládání a zpracování** dat. Viz [Úprava Visual Studio](../install/modify-visual-studio.md).

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud localdb nemáte, SQL Server Express si ho buď ze stránky pro stažení [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo přes **Instalační program pro Visual Studio**. V **Instalační program pro Visual Studio** můžete nainstalovat SQL Server Express LocalDB jako součást úlohy Ukládání  a zpracování dat nebo jako jednotlivou komponentu.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V Visual Studio otevřete okno **Průzkumník objektů systému SQL Server.** (Průzkumník objektů systému SQL Server se instaluje jako součást úlohy **Ukládání** a zpracování dat v **Instalační program pro Visual Studio**.) Rozbalte **uzel SQL Server.** Klikněte pravým tlačítkem na instanci LocalDB a vyberte **New Query (Nový dotaz).**

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript jazyka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak zvolte **tlačítko** Provést.

       Po ch chvíli se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-the-windows-forms-application"></a>Vytvoření model Windows Forms aplikace

:::moniker range="vs-2017"

Vytvořte nový projekt **model Windows Forms App (.NET Framework)** pro jazyk C# nebo Visual Basic. Projekt **pojmechnte WindowsSearchForm**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Tento krok vytvoří zdroj dat z databáze pomocí průvodce **konfigurací zdroje** dat:

1. Pokud chcete otevřít **okno Zdroje** dat, klikněte v **nabídce Data** na Zobrazit **zdroje dat.**

2. V okně **Zdroje** dat vyberte **Přidat nový zdroj dat** a spusťte průvodce konfigurací **zdroje** dat.

3. Na **stránce** Zvolte typ **zdroje dat vyberte** Databáze a pak klikněte na **Další.**

4. Na **stránce Zvolte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Výběrem **možnosti Nové** připojení spusťte **dialogové okno Přidat nebo** upravit připojení.

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na **Další.**

6. Na stránce Save connection string to the Application Configuration file (Uložit připojovací řetězec do **konfiguračního souboru aplikace)** klikněte na **Next (Další).**

7. Na stránce **Zvolte databázové objekty** rozbalte **uzel Tabulky.**

8. Vyberte **tabulku Customers** (Zákazníci) a pak klikněte na **Finish (Dokončit).**

     **NorthwindDataSet** se přidá do projektu a tabulka **Customers** se zobrazí v **okně Zdroje** dat.

:::moniker-end

:::moniker range=">=vs-2019"

Vytvořte nový projekt **model Windows Forms App (.NET Framework)** pro jazyk C# nebo Visual Basic. Projekt **pojmechnte WindowsSearchForm**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Tento krok vytvoří zdroj dat z databáze pomocí průvodce **konfigurací zdroje** dat:

1. Pokud chcete otevřít **okno Zdroje** dat, použijte rychlé hledání (**Ctrl** Q ) a + vyhledejte **Zdroje dat**.

1. V okně **Zdroje** dat vyberte **Přidat nový zdroj dat** a spusťte průvodce konfigurací **zdroje** dat.

1. Na **stránce** Zvolte typ **zdroje dat vyberte** Databáze a pak klikněte na **Další.**

1. Na **obrazovce Zvolit model databáze** zvolte Datová **sada** a pak klikněte na **Další.**

1. Na **stránce Zvolte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Výběrem **možnosti Nové** připojení spusťte **dialogové okno Přidat nebo** upravit připojení.

1. Na stránce Save connection string to the Application Configuration file (Uložit připojovací řetězec do **konfiguračního souboru aplikace)** klikněte na **Next (Další).**

1. Na stránce **Zvolte databázové objekty** rozbalte **uzel Tabulky.**

1. Vyberte **tabulku Customers** (Zákazníci) a pak klikněte na **Finish (Dokončit).**

     **NorthwindDataSet** se přidá do projektu a tabulka **Customers** se zobrazí v **okně Zdroje** dat.

:::moniker-end

## <a name="create-the-form"></a>Vytvoření formuláře

Ovládací prvky vázané na data můžete vytvořit přetažením položek z **okna Zdroje dat** do formuláře:

1. Ujistěte se, model Windows Forms návrhář dat má  aktivní fokus a že je otevřené a připnuté okno Zdroje dat.

1. Rozbalte **uzel** Zákazníci v **okně Zdroje** dat.

1. Přetáhněte **uzel** Customers z **okna Zdroje** dat do formuláře.

     Na formuláři se zobrazí pruh nástrojů a ( ) pro <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingNavigator> navigaci v záznamech. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a se zobrazí v hlavním panelu <xref:System.Windows.Forms.BindingNavigator> komponent.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Přidání parametrizace (funkce vyhledávání) do dotazu

Klauzuli WHERE můžete do původního dotazu přidat pomocí **dialogového okna Tvůrce kritérií** vyhledávání:

1. Hned pod návrhovou plochou formuláře vyberte tlačítko **customersTableAdapter** a pak v okně **Vlastnosti** zvolte **Přidat dotaz...**.

2. Do oblasti Nový název dotazu v **dialogovém** okně **Tvůrce** kritérií hledání zadejte **FillByCity.**

3. Přidejte `WHERE City = @City` do dotazu v oblasti **Text** dotazu.

     Dotaz by měl být podobný následujícímu:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Přístup a OLE DB zdroje dat používají otazník (?) k označení parametrů, takže klauzule WHERE by vypadala takhle: `WHERE City = ?` .

4. Kliknutím **na OK** zavřete dialogové okno Tvůrce **kritérií** hledání.

     Do **formuláře se přidá FillByCityToolStrip.**

## <a name="test-the-application"></a>Testování aplikace

Spuštění aplikace otevře formulář a připraví ho k použití parametru jako vstupu:

1. Stisknutím **klávesy F5** spusťte aplikaci.

2. Do **textového** pole Město zadejte **London** a potom klikněte na **FillByCity**.

     Datová mřížka se naplní zákazníky, kteří splňují uvedená kritéria. V tomto příkladu zobrazí datová mřížka pouze  zákazníky, kteří mají ve sloupci **City** hodnotu London.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace můžete po vytvoření parametrizovaného formuláře provést několik kroků. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Přidání ovládacích prvků, které zobrazují související data Další informace najdete v tématu [Relace v datových sadách.](relationships-in-datasets.md)

- Úprava datové sady pro přidání nebo odebrání databázových objektů Další informace najdete v tématu [Vytvoření a konfigurace datových sad.](../data-tools/create-and-configure-datasets-in-visual-studio.md)

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
