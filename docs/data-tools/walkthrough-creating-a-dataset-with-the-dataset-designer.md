---
title: 'Návod: Vytvoření datové sady pomocí Návrháře DataSet'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8c525d55de16e859005b9746eb52e5516928b9e6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586026"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Návod: vytvoření datové sady pomocí Návrhář datových sad

V tomto návodu vytvoříte datovou sadu pomocí **Návrhář datových sad**. Tento článek vás provede procesem vytvoření nového projektu a přidáním nové položky **DataSet** do tohoto článku. Naučíte se vytvářet tabulky založené na tabulkách v databázi bez použití průvodce.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V Instalační program pro Visual Studio lze SQL Server Express LocalDB nainstalovat jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editor dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Vytvoření nového projektu model Windows Forms aplikace

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.

2. V levém podokně rozbalte buď **vizuál C#**  , nebo **Visual Basic** a pak vyberte **Desktop Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **DatasetDesignerWalkthrough**a klikněte na **tlačítko OK**.

     Visual Studio přidá projekt do **Průzkumník řešení** a zobrazí nový formulář v návrháři.

## <a name="add-a-new-dataset-to-the-application"></a>Přidání nové datové sady do aplikace

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

     **Přidat novou položku** zobrazí se dialogové okno.

2. V levém podokně vyberte **data**a potom v prostředním podokně vyberte **datová sada** .

3. Pojmenujte datovou sadu **NorthwindDataSet**a pak zvolte **Přidat**.

     Visual Studio přidá do projektu soubor s názvem **NorthwindDataSet. xsd** a otevře ho v **Návrhář datových sad**.

## <a name="create-a-data-connection-in-server-explorer"></a>Vytvoření datového připojení v Průzkumník serveru

1. V nabídce **zobrazení** klikněte na příkaz **Průzkumník serveru**.

2. V **Průzkumník serveru**klikněte na tlačítko **připojit k databázi** .

3. Vytvořte připojení ke vzorové databázi Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Vytvoření tabulek v datové sadě

V této části se dozvíte, jak přidat tabulky do datové sady.

### <a name="to-create-the-customers-table"></a>Vytvoření tabulky Zákazníci

1. Rozbalte datové připojení, které jste vytvořili v **Průzkumník serveru**a potom rozbalte uzel **tabulky** .

2. Přetáhněte tabulku **Customers** z **Průzkumník serveru** na **Návrhář datových sad**.

     Do datové sady jsou přidána tabulka dat **Customers** a **CustomersTableAdapter** .

### <a name="to-create-the-orders-table"></a>Vytvoření tabulky objednávek

- Přetáhněte tabulku **Orders** z **Průzkumník serveru** na **Návrhář datových sad**.

     Tabulka dat **Orders** , **OrdersTableAdapter**a data relace mezi tabulkami **Customers** a **Orders** se přidají do datové sady.

### <a name="to-create-the-orderdetails-table"></a>Postup vytvoření tabulky OrderDetails

- Přetáhněte tabulku **Order Details** z **Průzkumník serveru** na **Návrhář datových sad**.

     Do datové sady jsou přidány tabulky dat **objednávky** , **OrderDetailsTableAdapter**a datový vztah mezi tabulkami **Orders** a **OrderDetails** .

## <a name="next-steps"></a>Další kroky

- Uložte datovou sadu.

- V okně **zdroje dat** vyberte položky a přetáhněte je na formulář. Další informace najdete v tématu [vázání model Windows Forms ovládacích prvků na data v aplikaci Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Do instancí TableAdapter přidejte další dotazy.

- Přidejte logiku ověřování k událostem <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> tabulek dat v datové sadě. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření a konfigurace datových sad v sadě Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Ověřit data](../data-tools/validate-data-in-datasets.md)
