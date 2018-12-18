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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4a0d248f59754d3f46e8fab0e0924c36a80b0d89
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305543"
---
# <a name="pass-data-between-forms"></a>Předávání dat mezi formuláři

Tento názorný postup obsahuje podrobné pokyny pro předávání dat z jednoho formuláře. Pomocí zákazníci a objednávky tabulky z databáze Northwind, jeden formulář umožňuje uživatelům vybrat zákazníka a druhý formulář pro zobrazení objednávek pro vybraného zákazníka. Tento návod ukazuje, jak vytvořit metodu na druhý formulář, který přijímá data z první formuláře.

> [!NOTE]
> Tento návod ukazuje pouze jeden ze způsobů předání dat mezi formuláři. Existují další možnosti pro předávání dat do formuláře, včetně vytváření druhý konstruktor pro příjem dat, nebo vytvoření veřejné vlastnosti, které lze nastavit s daty z první formuláře.

Úlohy v tomto návodu zahrnují:

-   Vytvoření nového **formulářová aplikace Windows** projektu.

-   Vytvoření a konfigurace datové sady [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

-   Výběr ovládacího prvku, aby se ve formuláři vytvořen při přetažení položky z **zdroje dat** okna. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Vytvoření ovládacího prvku vázané na data přetažením položek z **zdroje dat** okna do formuláře.

-   Vytváří se druhý formulář s mřížce se zobrazí data.

-   Vytváření dotazu TableAdapter načíst objednávek pro konkrétního zákazníka.

-   Předávání dat mezi formuláři.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V aplikaci Visual Studio Instalační služby systému SQL Server Express LocalDB lze nainstalovat jako součást **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-the-windows-forms-app-project"></a>Vytvoření projektu aplikace Windows Forms

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **PassingDataBetweenForms**a klikněte na tlačítko **OK**.

     **PassingDataBetweenForms** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

1.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.

3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

4.  Na **vyberte databázový model** stránce ověřte, jestli **datovou sadu** je zadán a potom klikněte na **Další**.

5.  Na **vyberte datové připojení** stránce, proveďte jednu z následujících akcí:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.

6.  Pokud vaše databáze vyžaduje heslo, a pokud je povolena možnost zahrnutí důvěrných osobních údajů, vyberte možnost a potom klikněte na tlačítko **Další**.

7.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

8.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.

9. Vyberte **zákazníkům** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** a **objednávky** tabulky se zobrazí v **zdroje dat** okna.

## <a name="create-the-first-form-form1"></a>Vytvoření první formulář (Form1)

Můžete vytvořit mřížky vázané na data ( <xref:System.Windows.Forms.DataGridView> ovládací prvek), přetažením **zákazníkům** uzlu z **zdroje dat** okna do formuláře.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>K vytvoření mřížky vázané na data ve formuláři

-   Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.

     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí na **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

## <a name="create-the-second-form"></a>Druhý formulář pro vytvoření

Druhý formulář k předávání dat k vytvoření.

1.  Z **projektu** nabídce zvolte **přidat formulář Windows**.

2.  Ponechte výchozí název **Form2**a klikněte na tlačítko **přidat**.

3.  Přetáhněte hlavní **objednávky** uzlu z **zdroje dat** okna do **Form2**.

     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí na **Form2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

4.  Odstranit **OrdersBindingNavigator** z panelu komponent.

     **OrdersBindingNavigator** dané zařízení zmizí z **Form2**.

## <a name="add-a-tableadapter-query"></a>Přidání dotazu TableAdapter

Přidání dotazu TableAdapter Form2 načíst objednávek pro vybraného zákazníka na Form1.

1.  Dvakrát klikněte **NorthwindDataSet.xsd** ve **Průzkumníka řešení**.

2.  Klikněte pravým tlačítkem myši **OrdersTableAdapter**a vyberte **přidat dotaz**.

3.  Ponechte výchozí možnost **použít SQL příkazy**a potom klikněte na tlačítko **Další**.

4.  Ponechte výchozí možnost **SELECT, který vrátí řádky**a potom klikněte na tlačítko **Další**.

5.  Přidat klauzuli WHERE do dotazu vrátit `Orders` na základě `CustomerID`. Dotaz by měl vypadat přibližně takto:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Ověření parametru správná syntaxe pro vaši databázi. Například v aplikaci Microsoft Access, klauzuli WHERE vypadat nějak takto: `WHERE CustomerID = ?`.

6.  Klikněte na tlačítko **Další**.

7.  Pro **zadejte název DataTableMethod**, typ `FillByCustomerID`.

8.  Zrušte **vrátit tabulku DataTable** možnost a potom klikněte na tlačítko **Další**.

9. Klikněte na tlačítko **Dokončit**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Vytvořit metodu na Form2 k předávání dat do

1.  Klikněte pravým tlačítkem na **Form2**a vyberte **zobrazit kód** otevřete **Form2** v **Editor kódu**.

2.  Přidejte následující kód, který **Form2** po `Form2_Load` metody:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Vytvořit metodu na Form1 k předání dat a zobrazení Form2

1.  V **Form1**, klikněte pravým tlačítkem na mřížce dat zákazníků a pak klikněte na **vlastnosti**.

2.  V **vlastnosti** okna, klikněte na tlačítko **události**.

3.  Dvakrát klikněte **CellDoubleClick** událostí.

     Zobrazí se editor kódu.

4.  Aktualizujte definici metody tak, aby odpovídala následující ukázce:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Spuštění aplikace

-   Stisknutím klávesy **F5** ke spuštění aplikace.

-   Klikněte dvakrát na záznam zákazníka v **Form1** otevřete **Form2** s objednávek tohoto zákazníka.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po předávání dat mezi formuláři. Mezi vylepšení, která je možné pro tento návod provést, patří:

-   Úpravy datové sady pro přidání nebo odebrání databázové objekty. Další informace najdete v tématu [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Přidáváme funkci pro uložení dat zpět do databáze. Další informace najdete v tématu [uložit data zpět do databáze](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)