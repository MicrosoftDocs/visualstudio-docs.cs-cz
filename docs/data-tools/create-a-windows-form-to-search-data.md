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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d503f8d1fd18817a30f49c64307d9fc14c74b3ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642709"
---
# <a name="create-a-windows-form-to-search-data"></a>Vytvoření formuláře Windows k vyhledávání dat

Běžným scénářem použití je zobrazení vybraných dat na formuláři. Například můžete chtít zobrazit objednávky konkrétního zákazníka nebo podrobnosti konkrétního objednávky. V tomto scénáři uživatel zadá informace do formuláře a následně se spustí dotaz se vstupem uživatele jako s parametrem. To znamená, že data jsou vybrána na základě parametrizovaného dotazu. Dotaz vrátí pouze data, která splňují kritéria zadaná uživatelem. Tento návod ukazuje, jak vytvořit dotaz, který vrací zákazníky v určitém městě, a upravit uživatelské rozhraní tak, aby uživatelé mohli zadat jméno města a stisknout tlačítko pro spuštění dotazu.

Použití parametrizovaných dotazů vám pomůže zajistit efektivitu vaší aplikace tím, že umožňuje databázi provádět práci, která je nejlepší, a rychle filtrovat záznamy. Na rozdíl od toho, pokud požadujete celou databázovou tabulku, přenesete ji přes síť a pak pomocí aplikační logiky vyhledejte požadované záznamy, aplikace může být pomalá a neefektivní.

Můžete přidat parametrizované dotazy do libovolného TableAdapter (a ovládací prvky pro přijímání hodnot parametrů a spuštění dotazu) pomocí dialogového okna **Tvůrce kritérií hledání** . Otevřete dialogové okno tak, že v nabídce **data** vyberete příkaz **Přidat dotaz** (nebo na libovolnou inteligentní značku TableAdapter).

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření a konfigurace zdroje dat v aplikaci pomocí průvodce **konfigurací zdroje dat** .

- Nastavení typu přetažení položek v okně **zdroje dat** .

- Vytváření ovládacích prvků, které zobrazují data přetažením položek z okna **zdroje dat** do formuláře.

- Přidání ovládacích prvků pro zobrazení dat ve formuláři.

- Dokončuje se dialogové okno **Tvůrce kritérií hledání** .

- Zadáním parametrů do formuláře a spuštěním parametrizovaného dotazu.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio**můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v **instalační program pro Visual Studio**.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms

Vytvořte nový projekt **aplikace model Windows Forms** pro buď C# nebo Visual Basic. Pojmenujte projekt **WindowsSearchForm**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Tento krok vytvoří zdroj dat z databáze pomocí průvodce **konfigurací zdroje dat** :

1. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte průvodce **konfigurací zdroje dat** .

3. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na tlačítko **Další**.

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **zvolit databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte tabulku **Customers (zákazníci** ) a pak klikněte na **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulka **Customers (zákazníci** ) se zobrazí v okně **zdroje dat** .

## <a name="create-the-form"></a>Vytvořit formulář

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře:

1. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

2. Přetáhněte uzel **zákazníci** z okna **zdroje dat** do formuláře.

     Na formuláři se zobrazí <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Přidat do dotazu Parametrizace (funkce vyhledávání)

Klauzuli WHERE můžete přidat k původnímu dotazu pomocí dialogového okna **Tvůrce kritérií hledání** :

1. Vyberte ovládací prvek <xref:System.Windows.Forms.DataGridView> a v nabídce **data** zvolte **Přidat dotaz** .

2. Do pole **nový název dotazu** v dialogovém okně **Tvůrce kritérií hledání** zadejte **FillByCity** .

3. Přidejte `WHERE City = @City` do dotazu v oblasti **textu dotazu** .

     Dotaz by měl vypadat přibližně takto:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Přístup ke zdrojům dat a jejich OLE DB používají otazník ('? ') k označení parametrů, takže klauzule WHERE by vypadala takto: `WHERE City = ?`.

4. Kliknutím na tlačítko **OK** zavřete dialogové okno **Tvůrce kritérií hledání** .

     Do formuláře se přidá **FillByCityToolStrip** .

## <a name="test-the-application"></a>Testování aplikace

Spuštění aplikace otevře formulář a zpřístupní ho pro použití parametru jako vstupu:

1. Stisknutím klávesy **F5** spusťte aplikaci.

2. Do textového pole **City** zadejte **Londýn** a pak klikněte na **FillByCity**.

     Datová mřížka je naplněna zákazníky, kteří splňují kritéria. V tomto příkladu datová mřížka zobrazuje pouze zákazníky, kteří mají ve sloupci **City** hodnotu **Londýn** .

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření parametrizovaného formuláře. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Přidávání ovládacích prvků, které zobrazují související data. Další informace najdete v tématu [relace v datových sadách](relationships-in-datasets.md).

- Úprava datové sady pro přidání nebo odebrání databázových objektů. Další informace najdete v tématu [Vytvoření a konfigurace datových sad](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
