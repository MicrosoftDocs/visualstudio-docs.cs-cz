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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c4e5ca1e9903089cbcc9daf99e8c8d49d170b1c8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388816"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Uložení dat do databáze (více tabulek)

Jedním z nejběžnějších scénářů při vývoji aplikace je zobrazení dat na formulář v nástrojích pro aplikace Windows, upravte údaje a odeslat aktualizovaná data zpět do databáze. Tento návod vytvoří formulář, který zobrazuje data ze dvou souvisejících tabulek a ukazuje, jak upravovat záznamy a změny uložit zpět do databáze. V tomto příkladu `Customers` a `Orders` tabulek z ukázkové databáze Northwind.

Data můžete uložit ve vaší aplikaci zpět do databáze pomocí volání `Update` metody třídy TableAdapter. Při přetažení tabulky z **zdroje dat** okna do formuláře, kód, který je potřeba k uložení dat se automaticky přidá. Žádné další tabulky, které jsou přidány k formuláři vyžadují ruční přidání tohoto kódu. Tento návod ukazuje, jak přidat kód pro uložení aktualizací z více než jedné tabulky.

Úlohy v tomto návodu zahrnují:

-   Vytvoření nového **formulářová aplikace Windows** projektu.

-   Vytvoření a konfigurace zdroje dat ve vaší aplikaci se [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

-   Ovládací prvky položek v nastavení [okna zdroje dat](add-new-data-sources.md#data-sources-window). Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Vytváření ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okna do formuláře.

-   Úprava několik záznamů ve všech tabulkách v datové sadě.

-   Úprava kódu pro odesílání aktualizovaná data v datové sadě zpět do databáze.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2. Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-the-windows-forms-application"></a>Vytvoření aplikace Windows Forms

Prvním krokem je vytvoření **formulářová aplikace Windows**. Přiřazení názvu projektu během tohoto kroku je volitelné, ale. poskytneme mu název protože uložíme také projekt později.

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **UpdateMultipleTablesWalkthrough**a klikněte na tlačítko **OK**.

     **UpdateMultipleTablesWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Tento krok vytváří zdroj dat v databázi Northwind pomocí průvodce **Průvodce konfigurací zdroje dat**. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o nastavení ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

1. Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.

   **Zdroje dat** otevře se okno.

2. V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

3. Na **zvolte typ zdroje dat** obrazovky, vyberte **databáze**a pak vyberte **Další**.

4. Na **vyberte datové připojení** obrazovky, proveďte jednu z následujících akcí:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    -   Vyberte **nové připojení** otevřít **přidat/změnit připojení** dialogové okno.

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak vyberte **Další**.

6. Na **uložit připojovací řetězec do konfiguračního souboru aplikace**vyberte **Další**.

7. Na **zvolte vaše databázové objekty** obrazovky, rozbalte **tabulky** uzlu.

8. Vyberte **zákazníkům** a **objednávky** tabulky a pak vyberte **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a tabulky se zobrazí v **zdroje dat** okna.

## <a name="set-the-controls-to-be-created"></a>Můžete nastavit řízení, který se má vytvořit

V tomto návodu, data v `Customers` tabulka se **podrobnosti** rozložení, ve kterém se zobrazí data v jednotlivých ovládacích prvků. Data z `Orders` tabulka se **mřížky** rozložení, které se zobrazí v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Chcete-li nastavit typ přetažení pro položky v okně zdrojů dat.

1. V **zdroje dat** okna, rozbalte **zákazníkům** uzlu.

2. Na **zákazníkům** uzlu, vyberte **podrobnosti** ovládací prvek seznamu můžete změnit kontrolu **zákazníkům** tabulky do jednotlivých ovládacích prvků. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Vytvoření formuláře vázané na data

Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.

1. Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.

     Ovládací prvky vázaných dat pomocí popisků se zobrazí ve formuláři, spolu s pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

2. Přetáhněte související **objednávky** uzlu z **zdroje dat** okna do **Form1**.

    > [!NOTE]
    > Související **objednávky** uzel se nachází pod **Fax** sloupce a je podřízený uzel **zákazníkům** uzlu.

     A <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. `OrdersTableAdapter` a <xref:System.Windows.Forms.BindingSource> zobrazují v panelu komponent.

## <a name="add-code-to-update-the-database"></a>Přidejte kód k aktualizaci databáze

Databáze můžete aktualizovat pomocí volání `Update` metody **zákazníkům** a **objednávky** objekty TableAdapter. Ve výchozím nastavení, obslužná rutina události **Uložit** tlačítko<xref:System.Windows.Forms.BindingNavigator> je přidán do formuláře kód k odeslání aktualizací do databáze. Tento postup upravuje kód k odesílání aktualizací ve správném pořadí. Tím se eliminuje možnost vyvolání chyby referenční integrity. Kód také implementuje obalením volání update v bloku try-catch – zpracování chyb. Můžete upravit kód tak, aby odpovídaly potřebám vaší aplikace.

> [!NOTE]
> Tento návod pro přehlednost nepoužívá transakce. Pokud chcete aktualizovat dvě nebo více souvisejících tabulek, ale obsahovat veškerou logiku aktualizací v rámci transakce. Transakce je proces, který zaručuje, že všechny související změny do databáze úspěšní, než se změny potvrdí. Další informace najdete v tématu [transakce a souběžnost](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Chcete-li přidat logiku aktualizací do aplikace

1. Vyberte **Uložit** tlačítko <xref:System.Windows.Forms.BindingNavigator>. Otevře se Editor kódu `bindingNavigatorSaveItem_Click` obslužné rutiny události.

2. Nahraďte kód v obslužné rutině události pro volání `Update` metody související objekty TableAdapter. Následující kód nejprve vytvoří tři tabulky dočasných dat pro uložení aktualizované informace pro každý <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added>, a <xref:System.Data.DataRowState.Modified>). Aktualizace jsou spuštěny ve správném pořadí. Kód by měl vypadat nějak takto:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testování aplikace

1. Stisknutím klávesy **F5**.

2. Některé změny dat z jednoho nebo více záznamů v každé tabulce.

3. Vyberte **Uložit** tlačítko.

4. Zkontrolujte hodnoty v databázi a ověřte, že se změny uložily.

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)