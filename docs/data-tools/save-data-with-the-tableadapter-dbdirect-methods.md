---
title: Ukládání dat pomocí metod TableAdapter DBDirect
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 16ba6fcab6ef0f7a60f8cb8373a10a7c4383676b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586208"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Ukládání dat pomocí metod TableAdapter DBDirect

Tento návod poskytuje podrobné pokyny pro spuštění příkazů SQL přímo proti databázi pomocí metod DBDirect TableAdapter. Metody DBDirect pro TableAdapter poskytují jemnou úroveň kontroly nad aktualizacemi databáze. Můžete je použít ke spuštění specifických příkazů SQL a uložených procedur voláním jednotlivých metod `Insert`, `Update`a `Delete` podle potřeby vaší aplikace (na rozdíl od přetížené `Update` metody, která provádí příkazy UPDATE, INSERT a DELETE v jednom volání).

V tomto návodu se naučíte:

- Vytvořte novou **model Windows Forms aplikaci**.

- Vytvořte a nakonfigurujte datovou sadu pomocí [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

- Vyberte ovládací prvek, který má být vytvořen ve formuláři při přetahování položek z okna **zdroje dat** . Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Vytvořte formulář vázaný na data přetažením položek z okna **zdroje dat** do formuláře.

- Přidejte metody pro přímý přístup k databázi a provádění vložení, aktualizace a odstranění.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio**můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editor dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace model Windows Forms

Prvním krokem je vytvoření **aplikace model Windows Forms**.

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.

2. V levém podokně rozbalte buď **vizuál C#**  , nebo **Visual Basic** a pak vyberte **Desktop Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **TableAdapterDbDirectMethodsWalkthrough**a klikněte na **tlačítko OK**.

     Projekt **TableAdapterDbDirectMethodsWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Tento krok používá **Průvodce konfigurací zdroje dat** k vytvoření zdroje dat založeného na `Region` tabulce v ukázkové databázi Northwind. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o tom, jak nastavit ukázkovou databázi Northwind, najdete v tématu [Postup: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.

   Otevře se okno **zdroje dat** .

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

3. Na obrazovce **Vybrat typ zdroje dat** vyberte **databáze**a pak vyberte **Další**.

4. Na obrazovce **Vybrat datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a pak vyberte **Další**.

6. Na obrazovce **Uložit připojovací řetězec do konfiguračního souboru aplikace** vyberte **Další**.

7. Na obrazovce **zvolit vaše databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte tabulku `Region` a pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulka `Region` se zobrazí v okně **zdroje dat** .

## <a name="add-controls-to-the-form-to-display-the-data"></a>Přidejte ovládací prvky do formuláře, aby se zobrazila data.

Vytvořte ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

Chcete-li vytvořit ovládací prvky vázané na data ve formuláři Windows, přetáhněte hlavní uzel **oblasti** z okna **zdroje dat** do formuláře.

Na formuláři se zobrazí ovládací prvek <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)`RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>a <xref:System.Windows.Forms.BindingNavigator>.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Chcete-li přidat tlačítka, která budou volat jednotlivé metody DbDirect TableAdapter

1. Přetáhněte tři ovládací prvky <xref:System.Windows.Forms.Button> z **panelu nástrojů** na **Form1** (pod **RegionDataGridView**).

2. Pro každé tlačítko nastavte následující vlastnosti **názvu** a **textu** .

    |Name|Text|
    |----------|----------|
    |`InsertButton`|**Vložit**|
    |`UpdateButton`|**Aktualizace**|
    |`DeleteButton`|**Delete**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Přidání kódu pro vložení nových záznamů do databáze

1. Vyberte **InsertButton** a vytvořte obslužnou rutinu události pro událost Click a otevřete formulář v editoru kódu.

2. `InsertButton_Click` obslužnou rutinu události nahraďte následujícím kódem:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Přidání kódu pro aktualizaci záznamů v databázi

1. Poklikejte na **UpdateButton** a vytvořte obslužnou rutinu události pro událost Click a otevřete formulář v editoru kódu.

2. `UpdateButton_Click` obslužnou rutinu události nahraďte následujícím kódem:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Přidání kódu pro odstranění záznamů z databáze

1. Vyberte **DeleteButton** a vytvořte obslužnou rutinu události pro událost Click a otevřete formulář v editoru kódu.

2. `DeleteButton_Click` obslužnou rutinu události nahraďte následujícím kódem:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Spuštění aplikace

- Pro spuštění aplikace vyberte **F5** .

- Vyberte tlačítko **Vložit** a ověřte, že se nový záznam zobrazí v mřížce.

- Klikněte na tlačítko **aktualizovat** a ověřte, zda je záznam v mřížce aktualizován.

- Vyberte tlačítko **Odstranit** a ověřte, zda je záznam odebrán z mřížky.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření formuláře vázaného na data. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Přidání vyhledávací funkce do formuláře.

- Přidáním dalších tabulek do datové sady výběrem možnosti **Konfigurovat datovou sadu pomocí Průvodce** v okně **zdroje dat** . Můžete přidat ovládací prvky, které zobrazují související data přetažením souvisejících uzlů do formuláře. Další informace najdete v tématu [relace v datových sadách](relationships-in-datasets.md).

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
