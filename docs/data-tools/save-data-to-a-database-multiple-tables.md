---
title: Uložení dat do databáze (více tabulek)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8d4dd98a622a3aa09b2ec11f4f3521ce1839ce8c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586247"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Uložení dat do databáze (více tabulek)

Jedním z nejběžnějších scénářů při vývoji aplikací je zobrazení dat ve formuláři aplikace systému Windows, úpravy dat a odeslání aktualizovaných dat zpět do databáze. Tento návod vytvoří formulář, který zobrazí data ze dvou souvisejících tabulek, a ukazuje, jak upravit záznamy a uložit změny zpět do databáze. V tomto příkladu se používá tabulka `Customers` a `Orders` z ukázkové databáze Northwind.

Data v aplikaci můžete uložit zpět do databáze voláním metody `Update` TableAdapter. Když přetáhnete tabulky z okna **zdroje dat** do formuláře, je automaticky přidán kód potřebný k uložení dat. Všechny další tabulky, které jsou přidány do formuláře, vyžadují ruční přidání tohoto kódu. Tento návod ukazuje, jak přidat kód pro uložení aktualizací z více než jedné tabulky.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření a konfigurace zdroje dat v aplikaci pomocí [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

- Nastavení ovládacích prvků položek v [okně zdroje dat](add-new-data-sources.md#data-sources-window). Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Vytváření ovládacích prvků vázaných na data přetažením položek z okna **zdroje dat** do formuláře.

- Úprava několika záznamů v každé tabulce datové sady.

- Úprava kódu pro odeslání aktualizovaných dat v datové sadě zpět do databáze.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio**můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editor dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms

Vytvořte nový projekt **aplikace model Windows Forms** pro buď C# nebo Visual Basic. Pojmenujte projekt **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Tento krok vytvoří zdroj dat z databáze Northwind pomocí **Průvodce konfigurací zdroje dat**. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o tom, jak nastavit ukázkovou databázi Northwind, najdete v tématu [Postup: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

1. Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.

   Otevře se okno **zdroje dat** .

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

3. Na obrazovce **Vybrat typ zdroje dat** vyberte **databáze**a pak vyberte **Další**.

4. Na obrazovce **Vybrat datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    - Vyberte **nové připojení** , aby se otevřelo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a pak vyberte **Další**.

6. V části **Uložit připojovací řetězec do konfiguračního souboru aplikace**vyberte možnost **Další**.

7. Na obrazovce **zvolit vaše databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte tabulky **zákazníci** a **objednávky** a pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulky se zobrazí v okně **zdroje dat** .

## <a name="set-the-controls-to-be-created"></a>Nastavit ovládací prvky, které se mají vytvořit

V tomto návodu jsou data v `Customers` tabulce v rozložení **podrobností** , kde se zobrazují data v jednotlivých ovládacích prvcích. Data z `Orders` tabulky jsou v rozložení **mřížky** , které se zobrazí v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Nastavení typu přetažení pro položky v okně zdroje dat

1. V okně **zdroje dat** rozbalte uzel **Customers (zákazníci** ).

2. V uzlu **Customers (zákazníci** ) vyberte **Podrobnosti** ze seznamu řízení a změňte tak řízení tabulky **Customers** na jednotlivé ovládací prvky. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Vytvoření formuláře vázaného na data

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

1. Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře **Form1**.

     Ovládací prvky vázané na data s popisnými popisky se zobrazí ve formuláři spolu s pruhem nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)`CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>a <xref:System.Windows.Forms.BindingNavigator>.

2. Přetáhněte uzel souvisejících **objednávek** z okna **zdroje dat** do formuláře **Form1**.

    > [!NOTE]
    > Uzel souvisejících **objednávek** je umístěný pod sloupcem **Fax** a je podřízeným uzlem uzlu **Customers (zákazníci** ).

     Na formuláři se zobrazí ovládací prvek <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí `OrdersTableAdapter` a <xref:System.Windows.Forms.BindingSource>.

## <a name="add-code-to-update-the-database"></a>Přidání kódu pro aktualizaci databáze

Databázi můžete aktualizovat voláním metod `Update` objekty TableAdapter a **Customers** a **Orders** . Ve výchozím nastavení je obslužná rutina události pro tlačítko **uložit**<xref:System.Windows.Forms.BindingNavigator> přidána do kódu formuláře, aby odesílala aktualizace databáze. Tento postup upraví kód tak, aby odesílal aktualizace ve správném pořadí. Tím se eliminuje možnost vyvolání chyb referenční integrity. Kód také implementuje zpracování chyb zabalením volání aktualizace do bloku try-catch. Kód můžete upravit tak, aby vyhovoval potřebám vaší aplikace.

> [!NOTE]
> Pro přehlednost tento návod nepoužívá transakci. Pokud však aktualizujete dvě nebo více souvisejících tabulek, zahrňte do transakce veškerou logiku aktualizace. Transakce je proces, který zaručuje, že všechny související změny v databázi budou úspěšné, než budou všechny změny potvrzeny. Další informace najdete v tématu [transakce a souběžnost](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Přidání logiky aktualizací do aplikace

1. Vyberte tlačítko **Uložit** na <xref:System.Windows.Forms.BindingNavigator>. Otevře se Editor kódu pro obslužnou rutinu události `bindingNavigatorSaveItem_Click`.

2. Nahraďte kód v obslužné rutině události pro volání metody `Update` souvisejícího objekty TableAdapter. Následující kód nejprve vytvoří tři dočasné tabulky dat, které uchovávají aktualizované informace pro každý <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added>a <xref:System.Data.DataRowState.Modified>). Aktualizace se spouští ve správném pořadí. Kód by měl vypadat takto:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testování aplikace

1. Stiskněte klávesu **F5**.

2. Proveďte některé změny dat jednoho nebo více záznamů v každé tabulce.

3. Vyberte tlačítko **Uložit**.

4. Zkontrolujte hodnoty v databázi a ověřte, zda byly změny uloženy.

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
