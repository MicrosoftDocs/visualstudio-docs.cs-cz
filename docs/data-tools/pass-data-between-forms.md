---
title: Předávání dat mezi formuláři
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eb4b1c0af617bfd8e1771e500b4f12699e3f0ec4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641441"
---
# <a name="pass-data-between-forms"></a>Předávání dat mezi formuláři

Tento návod poskytuje podrobné pokyny pro předávání dat z jednoho formuláře do druhého. Pomocí tabulek zákazníci a objednávky z databáze Northwind jeden formulář umožňuje uživatelům vybrat zákazníka a druhý formulář zobrazuje objednávky vybraného zákazníka. Tento návod ukazuje, jak vytvořit metodu pro druhý formulář, který přijímá data z prvního formuláře.

> [!NOTE]
> Tento návod ukazuje pouze jeden způsob, jak předat data mezi formuláři. K dispozici jsou další možnosti pro předávání dat do formuláře, včetně vytvoření druhého konstruktoru pro příjem dat nebo vytvoření veřejné vlastnosti, kterou lze nastavit s daty z prvního formuláře.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se nový projekt **aplikace model Windows Forms** .

- Vytvoření a konfigurace datové sady pomocí [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

- Výběr ovládacího prvku, který má být vytvořen ve formuláři při přetahování položek z okna **zdroje dat** . Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Vytvoření ovládacího prvku vázaného na data přetažením položek z okna **zdroje dat** do formuláře.

- Vytvoření druhého formuláře s mřížkou pro zobrazení dat

- Vytvoření dotazu TableAdapter pro načtení objednávek pro konkrétního zákazníka.

- Předávání dat mezi formuláři.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V Instalační program pro Visual Studio lze SQL Server Express LocalDB nainstalovat jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-the-windows-forms-app-project"></a>Vytvoření projektu aplikace model Windows Forms

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  > **projekt**.

2. V levém podokně rozbalte buď **vizuál C#**  , nebo **Visual Basic** a pak vyberte **Desktop Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **PassingDataBetweenForms**a klikněte na **tlačítko OK**.

     Vytvoří se projekt **PassingDataBetweenForms** a přidá se do **Průzkumník řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

1. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte průvodce **konfigurací zdroje dat** .

3. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte databázový model** ověřte, zda je zadaná **datová sada** , a poté klikněte na tlačítko **Další**.

5. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

6. Pokud vaše databáze vyžaduje heslo, a pokud je povolená možnost zahrnout citlivá data, vyberte možnost a klikněte na **Další**.

7. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

8. Na stránce **zvolit databázové objekty** rozbalte uzel **tabulky** .

9. Vyberte tabulky **zákazníci** a **objednávky** a poté klikněte na tlačítko **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulky **zákazníci** a **objednávky** se zobrazí v okně **zdroje dat** .

## <a name="create-the-first-form-form1"></a>Vytvoření prvního formuláře (Form1)

Můžete vytvořit datovou mřížku (<xref:System.Windows.Forms.DataGridView> ovládací prvek) tak, že přetáhnete uzel **zákazníci** z okna **zdroje dat** do formuláře.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Vytvoření mřížky vázané na data na formuláři

- Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře **Form1**.

     @No__t_0 a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí na **Form1**. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form"></a>Vytvoření druhého formuláře

Vytvořte druhý formulář, do kterého se budou předávat data.

1. V nabídce **projekt** vyberte možnost **Přidat formulář Windows**.

2. Ponechte výchozí název **Form2**a klikněte na **Přidat**.

3. Přetáhněte uzel hlavní **objednávky** z okna **zdroje dat** do **Form2**.

     V **Form2**se zobrazí <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

4. Odstraňte **OrdersBindingNavigator** z panelu komponent.

     **OrdersBindingNavigator** zmizí z **Form2**.

## <a name="add-a-tableadapter-query"></a>Přidat dotaz TableAdapter

Přidejte dotaz TableAdapter k Form2 pro načtení objednávek pro vybraného zákazníka na Form1.

1. Dvakrát klikněte na soubor **NorthwindDataSet. xsd** v **Průzkumník řešení**.

2. Klikněte pravým tlačítkem na **OrdersTableAdapter**a vyberte **Přidat dotaz**.

3. Ponechte výchozí možnost **použít příkazy SQL**a pak klikněte na **Další**.

4. Ponechte výchozí možnost **vybrat, která vrátí řádky**, a pak klikněte na **Další**.

5. Přidejte do dotazu klauzuli WHERE, která vrátí `Orders` na základě `CustomerID`. Dotaz by měl vypadat přibližně takto:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Ověřte správnou syntaxi parametru pro vaši databázi. Například v aplikaci Microsoft Access by klauzule WHERE vypadala takto: `WHERE CustomerID = ?`.

6. Klikněte na tlačítko **Další**.

7. Pro **naplnění názvu DataTableMethod**zadejte `FillByCustomerID`.

8. Zrušte zaškrtnutí možnosti **vrátit DataTable** a potom klikněte na tlačítko **Další**.

9. Klikněte na tlačítko **Dokončit**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Vytvoření metody v Form2 k předání dat

1. Klikněte pravým tlačítkem na **Form2**a výběrem **Zobrazit kód** otevřete **Form2** v **editoru kódu**.

2. Do **Form2** přidejte následující kód za metodu `Form2_Load`:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Vytvoření metody na Form1 pro předání dat a zobrazení Form2

1. V poli **Form1**klikněte pravým tlačítkem myši na datovou mřížku zákaznických dat a pak klikněte na **vlastnosti**.

2. V okně **vlastnosti** klikněte na položku **události**.

3. Dvakrát klikněte na událost **CellDoubleClick** .

     Zobrazí se Editor kódu.

4. Aktualizujte definici metody tak, aby odpovídala následující ukázce:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Spuštění aplikace

- Stisknutím klávesy **F5** spusťte aplikaci.

- Dvojitým kliknutím na záznam zákazníka v **Form1** otevřete **Form2** s objednávkami zákazníka.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po předání dat mezi formuláři. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Úprava datové sady pro přidání nebo odebrání databázových objektů. Další informace najdete v tématu [Vytvoření a konfigurace datových sad](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Přidání funkce pro uložení dat zpět do databáze. Další informace najdete v tématu [uložení dat zpět do databáze](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)