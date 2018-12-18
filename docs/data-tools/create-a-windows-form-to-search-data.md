---
title: Vytvoření formuláře Windows k vyhledávání dat
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 15cfd136050d9a0e3fca89964c5a9712b7b5ae06
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159890"
---
# <a name="create-a-windows-form-to-search-data"></a>Vytvoření formuláře Windows k vyhledávání dat

Běžný scénář, kdy aplikace se má zobrazit vybraná data ve formuláři. Můžete například chtít zobrazujících objednávky pro konkrétního zákazníka nebo podrobnosti o určitém pořadí. V tomto scénáři uživatel zadá informace do formátu, a pak je dotaz proveden se vstupem uživatele jako parametr; To znamená data se určí parametrický dotaz. Dotaz vrátí pouze data, která splňuje kritéria zadaná uživatelem. Tento návod ukazuje, jak vytvořit dotaz, který vrátí zákazníky v konkrétním městě a upravte uživatelské rozhraní, aby uživatelé můžete zadat název města a kliknutím na tlačítko Spustit dotaz.

Použití parametrizovaných dotazů pomáhá zajištění efektivního aplikace tím, že databáze je nejvhodnější při práci – rychle filtrování záznamů. Naopak pokud vyžádáte tabulku celé databáze, přenos přes síť a pak použít k vyhledání záznamy, které chcete aplikaci logiky, aplikace může být pomalé a neefektivní.

Parametrizované dotazy můžete přidat všechny třídy TableAdapter (a ovládací prvky přijmout hodnoty parametrů a spusťte dotaz), pomocí **Tvůrce kritérií vyhledávání** dialogové okno. Otevřete dialogové okno tak, že vyberete **přidat dotaz** příkaz **Data** nabídce (nebo na libovolné klíčové slovo inteligentní TableAdapter).

Úlohy v tomto návodu zahrnují:

-   Vytvoření nového **formulářová aplikace Windows** projektu.

-   Vytvoření a konfigurace zdroje dat ve vaší aplikaci se **konfigurace zdroje dat** průvodce.

-   Typ rozevírací položky v nastavení **zdroje dat** okna.

-   Vytváření ovládacích prvků, které data zobrazit přetažením položek z **zdroje dat** okna do formuláře.

-   Přidání ovládacích prvků pro zobrazení dat ve formuláři.

-   Dokončuje **Tvůrce kritérií vyhledávání** dialogové okno.

-   Zadat parametry do formuláře a provádění parametrický dotaz.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** zatížení **instalační program sady Visual Studio**.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-the-windows-forms-application"></a>Vytvoření aplikace Windows Forms

Prvním krokem je vytvoření aplikace Windows Forms. Přiřazení názvu projektu je volitelné v tomto kroku, ale budete jí přiřadit názvu na toto vzhledem k tomu budete později uložení projektu:

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **WindowsSearchForm**a klikněte na tlačítko **OK**.

     **WindowsSearchForm** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Tento krok vytváří zdroj dat z databáze pomocí **konfigurace zdroje dat** průvodce:

1.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.

3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.

5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.

6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.

8.  Vyberte **zákazníkům** tabulku a pak klikněte na tlačítko **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** tabulky se zobrazí v **zdroje dat** okna.

## <a name="create-the-form"></a>Vytvoření formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře:

1.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.

2.  Přetáhněte **zákazníkům** uzlu z **zdroje dat** okna do formuláře.

     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Přidat do dotazu Parametrizace (funkce vyhledávání)

Můžete přidat klauzuli WHERE dotazu na původní pomocí **Tvůrce kritérií vyhledávání** dialogové okno:

1.  Vyberte <xref:System.Windows.Forms.DataGridView> ovládací prvek a klikněte na tlačítko **přidat dotaz** na **Data** nabídky.

2.  Typ **FillByCity** v **nový název dotazu** oblast na **Tvůrce kritérií vyhledávání** dialogové okno.

3.  Přidat `WHERE City = @City` do dotazu v **Text dotazu** oblasti.

     Dotaz by měl vypadat přibližně takto:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Přístup a technologie OLE DB zdroje dat používat otazník ("?") k označení parametrů, takže v klauzuli WHERE bude vypadat takto: `WHERE City = ?`.

4.  Klikněte na tlačítko **OK** zavřete **Tvůrce kritérií vyhledávání** dialogové okno.

     A **FillByCityToolStrip** je přidán do formuláře.

## <a name="test-the-application"></a>Testování aplikace

Spuštění aplikace otevře formulář a zpřístupňuje je připraven přijmout parametr jako vstup:

1.  Stisknutím klávesy **F5** ke spuštění aplikace.

2.  Typ **Londýn** do **Město** textové pole a pak klikněte na tlačítko **FillByCity**.

     Datové mřížce se vyplní zákazníky, kteří splňují kritéria. V tomto příkladu datové mřížky se zobrazí pouze zákazníci, kteří mají hodnotu **Londýn** v jejich **Město** sloupce.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření parametrizovaného formuláře. Mezi vylepšení, která je možné pro tento návod provést, patří:

-   Přidání ovládacích prvků, které zobrazují související data. Další informace najdete v tématu [vztahy v datových sadách](relationships-in-datasets.md).

-   Úpravy datové sady pro přidání nebo odebrání databázové objekty. Další informace najdete v tématu [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
